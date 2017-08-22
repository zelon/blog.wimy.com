언젠가 한번 글로 정리해봐야지 하던 것을 한번 적어본다.

내가 처음 hello world를 모니터에 띄워본지 꽤 되었기 때문에, 지금은 어느 정도 쓸 수 있다고 생각하는 언어가 몇 개 있다. C++, Python, C\#, Java, Go, Javascript 정도가 있다. 물론 언어마다 숙련도가 꽤 차이가 난다.

어떤 새로운 프로그램을 만들 때 어떤 기준으로 언어를 고를까를 생각해보다가, 나에게는 2가지의 기준이 있다는 생각이 들었다.

# Garbage Collection

먼저 Garbage Collection 이 있느냐 없느냐이다. 이 기준은 성능에 민감한, 특히 온라인 게임 서버 중 필드 던전(불특정 다수가 만나서 전투를 할 수 있는 공간)을 랙 없이 구현할 수 있는 언어이냐 아니냐를 판단하는 기준이 된다. 쉽게 생각해서 Garbage Collection이 동작하게 되었을 때, 전투가 벌어진다면, 버벅이게 될 것이기 때문이다. 그래서 Garbage Collection이 있는 언어는 이런 서버를 제작할 때는 배제되어야 한다. 

그래서, 이런 서버를 만들 때는 C++을 쓸 수 밖에 없을 것 같다. Rust라는 언어가 최근에 나온 언어 중에는 Garbage Collection이 없다고 하는데, 아직 한번도 안 써봐서, 기회가 온다면 한번 살펴봐야 겠다.

# 동적 타입 vs 정적 타입

그리고 또 하나의 기준은 동적 타입이냐, 정적 타입이냐이다. 동적 타입인 python+Javascript로 약 4천줄의 코드를 5년 정도 유지보수하면서 느낀 것은 컴파일을 하면 쉽게 잡히는 버그들을 실행시간에 만나게 된다는 것이다. 그냥 함수 이름을 하나 더 알아보기 쉽게 바꾸었는데, 혹시나 내가 검색하지 못한 곳에서 참조하고 있을까봐 전전긍긍하게 되거나, 변수 하나 삭제했는데, 테스트 못한 케이스가 있을까봐 조바심을 낸다. 혹시나 이런 경우는 유닛 테스트를 잘 짜지 못해서 그렇다고 할 수도 있지만, 글쎄, 많은 케이스들을 로직 검증을 위해서가 아닌, code coverage 테스트를 위해서 하나하나 유닛 테스트로 짜고 있는 자신을 보고 있으면, 내가 왜 이러고 있나라는 생각이 든다.

그래서, 동적 타입의 스크립트 언어(pytho, javascript등)는 실행시켰을 때, if/for/while 등의 조건 분기가 없는 코드를 짜는 것 정도는 납득할만하다. 어차피 한번 실행시키면 대부분의 코드가 테스트되기 때문이다. 그 외에 복잡한 로직이 들어가고 depth가 깊어지는 코드라면 동적 타입의 언어는 버리자. 사실 이렇게 생각하면, python을 쓸 수 없는데, 그자리를 go언어와 C\#스크립트(Visual Studio 2015 Update3이상 설치)가 이제 그 대안이 될 수 있을 것 같다. 그리고 javascript의 경우에는 typescript를 통해서 컴파일해낸 javascript를 사용하게 될 것 같다.

# 나의 결론

python 이제 봉인하자

javascript는 typescript로 컴파일해내서 쓴다

스크립트는 가능하면 C\# script, cross platform은 go언어

랙없어야 하는 서버는 C++. 시간나면 rust 잠깐 봐두자

랙이 큰 문제없는 서버는 내가 만들 일이 거의 없긴 한데, C\#을 기본으로 하고, java를 보는게 어떨까 고민 중...