
# 업데이트
 아래의 내용은 임시로 취해진 조치이며, 결국에는 Visual Studio 16.4 버전이 릴리즈되면서 해결되었다
 
# 예전
 Visual Studio의 WPF Designer에서 내가 만든 UserControl을 추가했는데, 실행은 문제가 없는데 Could not load type xxxx 라면서 Designer에서 제대로 previwe가 안 될 때는, bin 폴더를 삭제하고, 다시 빌드 시켜본다. 뭔가 임시 파일에서 정보를 캐싱하는 게 있는지 삭제하고 빌드를 해야 인식하는 경우가 있다