 MSSQL 2019부터는 Microsoft 에서 공식적으로 리눅스 컨테이너에서의 MSSQL 을 지원하게 되면서 간단하게 mssql을 컨테이너에서 실행할 수 있게 되었다. 하지만 오히려 윈도우 컨테이너용 MSSQL을 공식적으로 지원하지 않게 되어버렸다.
 
 윈도우용 서버 프로그램을 개발하는 입장에서는 윈도우용 컨테이너와 리눅스용 컨테이너를 혼용해서 사용해야하는 상황이 되어버려서 좀 찾아보니, 윈도우용 컨테이너에서 MSSQL을 실행하는 방법들이 있었다

 https://github.com/microsoft/mssql-docker/tree/master/windows/mssql-server-windows-developer 

 위의 주소에 가보면, MSSQL 2019 버전을 윈도우 컨테이너로 만드는 방법이 있는데, MSSQL 2022 버전으로 만들어 보았다.

 github url: https://github.com/zelon/DockerUtil/tree/main/MSSQLWindowsServer

 docker build 에 필요한 SQLServer2022-DEV-x64-ENU.box, SQLServer2022-DEV-x64-ENU.exe 파일은 https://www.microsoft.com/en-us/sql-server/sql-server-downloads 에서 다운 받은 후 실행하면 '미디어 다운로드' 를 하면 받을 수 있다

 Dockerfile 의 내용에 따라서

    docker build -t mssql-win-zelon .

 위와 같이 빌드를 하고

    docker run -d -p 1433:1433 -v C:/temp/:C:/temp/ -e sa_password=Abcd!234 -e ACCEPT_EULA=Y mssql-win-zelon

 위와 같이 실행을 하면 된다. 다만 sa_password 에는 원하는 암호로 변경하면 되는데 충분히 복잡한 암호를 사용해야 한다. 그렇지 않으면 sa 암호 설정이 되지 않는다


 이렇게 만들어진 이미지는 아래의 hub.docker.com 에 공유되어 있다

* MSSQL2022 on WindowsServer2019: https://hub.docker.com/repository/docker/zelonion/mssql2022-winsvr2019
* MSSQL2022 on WindowsServer2025: https://hub.docker.com/repository/docker/zelonion/mssql2022-winsvr2025



참고 Link:
 * setup.exe 인자들 설명: https://learn.microsoft.com/en-us/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-ver15
 
 