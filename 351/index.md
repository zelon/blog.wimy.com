 구글에서 wimy.com 처럼 자신의 도메인을 가지고 있는 사람들을 위해, G메일, 구글 문서 등을 제공해주는 Google Apps 라는 서비스가 있다. 이 서비스를 이용하면, 자신의 도메인의 메일 - myname@mydomain.com 같은 메일 주소를 사용할 수 있게 해주거나, 도메인 안의 사용자들끼리만 공유할 수 있는 구글 서비스들을 제공받게 된다.

 http://www.google.com/a 를 통해서 이런 서비스를 제공받을 수 있으며, 더욱 재미있는 것은 google app engine 으로 만든 웹 사이트를 내 하위 도메인의 특정 google app 에 연결할 수 있게 된다(pop.wimy.com 이 이렇게 만들어져있다) 그리고 당연히 www 도 하위 도메인이므로, www.wimy.com 을 google app engine 에 만들면 연결할 수 있게 된다.

 그런데!!!! 이상하게도 www.wimy.com 이 연결이 안되는것이었다. 게다가 아무리 시도를 해도, 아무런 오류 메시지(왜 안되는지에 대한 내용)도 없고.... 약 2주 넘게 이런저런 방법을 해보다가 안되어서 포기하고, w.wimy.com 을 사용하도록 했었다.

 그러다가, 오늘 google app 에 좀 더 많은 구글 서비스를 사용하도록 되었다는 공지가 와서, 업그레이드를 시켜주고, 갑자기 이 문제가 생각나서 다시 해보니, 역시나 안되었다.... -\_-;;;;

 그래서 이번 기회에 다시 찾아봐야겠다 싶어서 영어로 된 포럼을 좀 뒤져봤더니, 이런 결과를 얻을 수 있었다... 만세 ㅠㅜ

<https://www.google.com/support/forum/p/Google+Apps/thread?tid=2bf66e830460fec0&hl=en>

 내용을 요약하면, google sites 기능과 중복해서 하위 도메인을 설정을 할 수 없는데(이건 나도 알고 있었다. 그래도 안되었음), sites 기능을 disable 한다고 해서 하위 도메인 설정이 제거되지는 않는다는 것이었다(!! 이게 주된원인!!!). 구글 측의 버그라고 적혀있는데.... 여튼 결론은 다음과 같다.

1. google sites 기능을 켠다.

2. google sites 에 www 하위 도메인을 연결한다.

3. google sites 에서 www 하위 도메인을 제거한다(!!!!!!!!!!!!!) 즉, default 설정으로 되돌린다.

4. google sites 기능을 끈다.

5. google app engine 에 www 하위 도메인을 연결한다.

즉, 위의 3번을 안 하고, sites 기능을 꺼서 발생한 문제였던듯..... ㅠㅜ

이건 마치, C++ 소멸자에서 deep copy 된 메모리를 해제하지 않은 것 같은 오류다...(뭐래;;)

그래도... 이제 잘되겠지?.....(DNS 관련해서는 캐시 때문에 하루 정도 지나야 정상동작하니 100% 잘되는지 확인하려면 시간이 또 걸릴듯 ㅠㅜ)


