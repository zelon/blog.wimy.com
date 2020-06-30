Wimybox - http://box.wimy.com 을 이제 더이상 서비스할 수 없게 되었다. 그래서 더이상 개발도 하지 않게 되었다.

회사 일도 바쁘고 조금 지친 것도 있지만, 직접적인 원인은 YouTube API를 쓰는데 너무 복잡한 것을 요구해왔기 때문이다

아마 YouTube API를 쓰는 다른 사람들도 관련 메일을 받았겠지만 얼마 전부터 YouTube API측에서 약관을 지키라면서 Audit Form(사용 방법 등 - https://support.google.com/youtube/contact/yt_api_form)을 등록하라고 해왔고, 귀찮기도 하고, 엄청나게 긴 영어로 된 약관을 하나하나 읽어보기는 힘들었기 때문에 Audit Form을 보내지 않았다. 참고로 읽어보고 준수해야 하는 약관은 3개이며 그 중에 1개는 이만큼(https://developers.google.com/youtube/terms/developer-policies)의 길이다. 여튼 Form을 보내지 않았더니 YouTube API 접근이 제한되었고 결국 wimybox 서비스는 오류를 발생하게 되었다.

시간이 되어서 Audit Form을 채워서 보냈더니, "이런저런 약관이 위배되었으니 A,B,C를 고쳐주세요"라고 답변 받았고, 다시 예전 소스를 꺼내서 수정하고, 약관을 첫 화면 잘 보이는 곳에 배치하고, 링크도 걸고 해서 답변을 보냈더니, 아래처럼 답변이 왔다.

* Screencast or Video recording(s) that clearly demonstrates how your API Client and its users access and use the YouTube API Services
* Please confirm that you don't wish to use the YouTube API services any longer in the future for this project key. Once we get the confirmation, we will revoke access for the project keys from our end

 동영상을 만드는 것도 힘들고, 나의 구현 방법을 알려달라는 것도 웃기고... 사용 안할거면 알려달라고 친절하게 설명도 해준다(내가 귀찮아한다는 것을 알았나...) 그래서 wimybox 서비스를 종료하기로 결정했다.
 
 2009년 무한도전 듀엣 가요제의 냉면을 들으면서 열심히 만들고, 2011년 원더걸스의 Be My Baby를 들으면서 재미있게 업그레이드 했던 기억이 난다. 아쉽지만 여기까지.

 시간이 되면 코드만 마지막으로 정리하고, 정식으로 사이트 닫아야 겠다. 앞으로 취미 삼아 토이프로젝트 만들 때도 이제 구글의 API를 가능하면 사용하지 않도록 해야겠다
