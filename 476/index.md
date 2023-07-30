 윈도우 10 1709 이상의 버전에서는 기본적으로 winget 이라는 명령을 사용하여 각종 프로그램을 설치할 수 있다(http://blog.wimysoft.com/471/). 하지만 윈도우 서버(Windows Server)에서는 기본적으로 설치가 되어 있지 않은데, 공식 사이트의 샌드박스에서의 설치 방법(https://learn.microsoft.com/ko-kr/windows/package-manager/winget/)과 github 의 comment(https://github.com/microsoft/winget-cli/issues/700#issuecomment-825918522)를 참고하면 아래와 같이 설치하면 된다

먼저 아래와 같이 powershell 권한을 상승시켜준다

    PS> Set-ExecutionPolicy RemoteSigned

그 후 아래의 스크립트를 실행하면 된다

    $progressPreference = 'silentlyContinue'
    Write-Host "Installing Microsoft.UI.Xaml v2.7.3..."
    $latestUIXamlAppxUri = "https://github.com/microsoft/microsoft-ui-xaml/releases/download/v2.7.3/Microsoft.UI.Xaml.2.7.x64.appx"
    $latestUIXamlAppxOutFileName = $latestUIXamlAppxUri.Split("/")[-1]
    Invoke-WebRequest -Uri $latestUIXamlAppxUri -OutFile "./$latestUIXamlAppxOutFileName"
    Add-AppxPackage "./$latestUIXamlAppxOutFileName"
    Write-Host "Installing Microsoft.VCLibs.x64.14.00..."
    Invoke-WebRequest -Uri https://aka.ms/Microsoft.VCLibs.x64.14.00.Desktop.appx -OutFile Microsoft.VCLibs.x64.14.00.Desktop.appx
    Add-AppxPackage Microsoft.VCLibs.x64.14.00.Desktop.appx
    Write-Host "Download WinGet:latest License..."
    $latestWingetLicenseUri = $(Invoke-RestMethod https://api.github.com/repos/microsoft/winget-cli/releases/latest).assets.browser_download_url | Where-Object {$_.EndsWith("_License1.xml")}
    $latestWingetLicenseOutfileName = $latestWingetLicenseUri.Split("/")[-1]
    Invoke-WebRequest -Uri $latestWingetLicenseUri -OutFile "./$latestWingetLicenseOutfileName"
    Write-Host "Installing WinGet:latest..."
    $latestWingetMsixBundleUri = $(Invoke-RestMethod https://api.github.com/repos/microsoft/winget-cli/releases/latest).assets.browser_download_url | Where-Object {$_.EndsWith(".msixbundle")}
    $latestWingetMsixBundleOutfileName = $latestWingetMsixBundleUri.Split("/")[-1]
    Invoke-WebRequest -Uri $latestWingetMsixBundleUri -OutFile "./$latestWingetMsixBundleOutfileName"
    Add-AppxProvisionedPackage -Online -PackagePath "./$latestWingetMsixBundleOutfileName" -LicensePath "./$latestWingetLicenseOutfileName" -Verbose

설치되고 나면 해당 폴더에 다운로드 받은 파일들은 삭제하자.


위의 스크립트의 내용을 살펴보면, 공식 사이트(https://learn.microsoft.com/ko-kr/windows/package-manager/winget/)의 방법대로 하면 windows server 에서는 Microsoft.UI.Xaml 이 없어서 설치가 실패한다. 그래서 Microsoft.UI.Xaml 을 설치해준다. 최신 버전은 오히려 winget 설치가 안되어서 2.7버전을 지정해서 설치한다. 그리고 그냥 winget 을 설치하면 License 가 없다고 오류가 나기 때문에 License 파일도 받아서, Add-AppxProvisionedPackage 명령으로 설치해준다

