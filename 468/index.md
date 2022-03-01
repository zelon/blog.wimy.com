ASP.NET Core를 재미있게 보고 있어서 appsettings.json 에 이런 저런 설정을 많이 넣다가 별도의 파일에 특정한 설정들만 분리해서 넣고 싶어서 찾아보니 아래와 같은 방법으로 사용할 수 있었다. .NET 6.0 기준이다. 재미있는 점은 json 파일의 내용이 변경되었을 때 바로 변경된 내용을 반영해주는 옵션이 제공된다는 점이다

mydata.json 파일을 추가한 다음에 Properties 창에서 Copy to Output Directory 옵션이 Copy if newer 인지만 잘 확인하고 사용하자.

Program.cs 를 아래 코드를 참고하여 수정


    var builder = WebApplication.CreateBuilder(args);
    builder.Configuration.AddJsonFile("mydata.json", optional: false, reloadOnChange: true);

특정 페이지에서 아래와 같이 사용

    private readonly IConfiguration _configuration;

    public IndexModel(IConfiguration configuration)
    {
        _configuration = configuration;
    }

    public void OnGet()
    {
        var section = _configuration.GetSection("Additional");
        var k = section.GetSection("MySetting").GetSection("Default")["Max"];
        System.Diagnostics.Trace.WriteLine(k);
    }



#ASP.NETCore #json #data