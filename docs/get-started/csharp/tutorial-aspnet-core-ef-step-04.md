---
title: '4단계: ASP.NET Core 앱에서 웹 API 표시'
description: 이 동영상 자습서 및 단계별 지침을 사용하여 ASP.NET Core 웹앱에 웹 API를 추가합니다.
ms.custom: get-started
ms.date: 02/13/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 5ea9468bdf86986ab542fb1cabc873c9aeb75fd6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580043"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>4단계: ASP.NET Core 앱에서 웹 API 표시

다음 단계에 따라 기존 ASP.NET Core 앱에 웹 API를 추가합니다.

_이 비디오를 보고 따라서 첫 번째 ASP.NET Core 앱에 웹 API 지원을 추가합니다._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>프로젝트 열기

Visual Studio 2019에서 ASP.NET Core 앱을 엽니다. [이 자습서 시리즈의 3단계](tutorial-aspnet-core-ef-step-03.md)에 구성된 대로 모델 형식을 관리하려면 앱에서 EF Core를 이미 사용하고 있어야 합니다.

## <a name="add-an-api-controller"></a>API 컨트롤러 추가

프로젝트를 마우스 오른쪽 단추로 클릭하고 *API*라는 새 폴더를 추가합니다. 그런 다음, 이 폴더를 마우스 오른쪽 단추로 클릭하고 **추가** > **스캐폴드된 새 항목**을 선택합니다. **Entity Framework를 사용하며 동작이 포함된 API 컨트롤러**를 선택합니다. 이제 기존 모델 클래스를 선택하고 **추가**를 클릭합니다.

![Visual Studio 2019 ASP.NET Core 스캐폴드된 API 컨트롤러](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>생성된 컨트롤러 검토

생성된 코드에는 새 컨트롤러 클래스가 포함됩니다. 클래스 정의의 맨 위에는 두 개의 특성이 있습니다.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

첫 번째 특성은 컨트롤러가 `GamesController`인 경우 경로가 `api/Games`가 될 것을 의미하는 `api/[controller]`로 이 컨트롤러의 동작 경로를 지정합니다.

두 번째 특성인 `[ApiController]`는 모든 동작 메서드에 고유한 `[Route]` 특성이 포함되는지 확인하는 것과 같이 클래스에 유용한 몇 가지 유효성 검사를 추가합니다.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

컨트롤러는 해당 생성자에 전달된 기존 `AppDbContext`를 사용합니다. 각 동작은 이 필드를 사용하여 애플리케이션의 데이터 작업을 수행합니다.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

첫 번째 메서드는 `[HttpGet]` 특성을 사용하여 지정된 간단한 GET 요청입니다. 매개 변수를 사용하지 않고 데이터베이스의 모든 게임 목록을 반환합니다.

```csharp
// GET: api/Games/5
[HttpGet("{id}")]
public async Task<IActionResult> GetGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);

    if (game == null)
    {
        return NotFound();
    }

    return Ok(game);
}
```

다음 메서드는 `/` 뒤의 경로에 추가될 `{id}`를 경로에서 지정하므로 전체 경로는 위쪽 설명에 표시된 대로 `api/Games/5`와 같이 표시됩니다. `id` 입력은 메서드의 `id` 매개 변수에 매핑됩니다. 메서드 내에서 모델이 잘못된 경우 `BadRequest` 결과가 반환됩니다. 그렇지 않으면 EF에서는 제공된 `id`와 일치하는 레코드를 찾으려고 시도합니다. 찾을 수 없는 경우 `NotFound` 결과가 반환되고, 찾을 수 있는 경우 해당 `Game` 레코드가 반환됩니다.

```csharp
// PUT: api/Games/5
[HttpPut("{id}")]
public async Task<IActionResult> PutGame([FromRoute] int id, [FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    if (id != game.Id)
    {
        return BadRequest();
    }

    _context.Entry(game).State = EntityState.Modified;

    try
    {
        await _context.SaveChangesAsync();
    }
    catch (DbUpdateConcurrencyException)
    {
        if (!GameExists(id))
        {
            return NotFound();
        }
        else
        {
            throw;
        }
    }

    return NoContent();
}
```

다음으로, API에 대해 생성되는 `[HttpPut]` 요청은 업데이트를 수행하는 데 사용됩니다. 새 `Game` 레코드는 요청 본문에 제공됩니다. 일부 유효성 검사 및 오류 검사가 수행되고, 모든 검사에 성공하면 데이터베이스의 레코드가 요청 본문에 제공된 값으로 업데이트됩니다. 그렇지 않으면 적절한 오류 응답이 반환됩니다.

```csharp
// POST: api/Games
[HttpPost]
public async Task<IActionResult> PostGame([FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    _context.Game.Add(game);
    await _context.SaveChangesAsync();

    return CreatedAtAction("GetGame", new { id = game.Id }, game);
}
```

`[HttpPost]` 요청은 시스템에 새 레코드를 추가하는 데 사용됩니다. `[HttpPut]`과 마찬가지로, 레코드는 요청 본문에 추가됩니다. 유효한 경우 EF Core에서는 데이터베이스에 레코드를 추가하고 동작은 업데이트된 레코드(데이터베이스 생성 ID 포함) 및 API의 레코드 링크를 반환합니다.

```csharp
// DELETE: api/Games/5
[HttpDelete("{id}")]
public async Task<IActionResult> DeleteGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);
    if (game == null)
    {
        return NotFound();
    }

    _context.Game.Remove(game);
    await _context.SaveChangesAsync();

    return Ok(game);
}
```

마지막으로 `[HttpDelete]` 경로는 레코드를 삭제하는 데 ID와 함께 사용됩니다. 요청이 유효하고 지정된 ID의 레코드가 있으면 EF Core에서는 데이터베이스에서 해당 레코드를 삭제합니다.

## <a name="adding-swagger"></a>Swagger 추가

Swagger는 서비스 및 미들웨어 세트로 ASP.NET Core 앱에 추가할 수 있는 API 문서 및 테스트 도구입니다. Swagger를 추가하려면 프로젝트를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리**를 선택합니다. 그런 다음, **찾아보기**를 클릭하고 `Swashbuckle.AspNetCore`를 검색하여 4.0.1 버전을 설치합니다.

![Visual Studio 2019 NuGet에서 Swashbuckle 추가](media/vs-2019/vs2019-nuget-swashbuckle.png)

설치되면 `Startup.cs`를 열고 `ConfigureServices` 메서드의 끝에 다음을 추가합니다.

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

또한 파일의 맨 위에 `using Swashbuckle.AspNetCore.Swagger;`를 추가해야 합니다.

그런 다음, `UseMvc` 바로 앞에 `Configure` 메서드에 다음을 추가합니다.

```csharp
// Enable middleware to serve generated Swagger as a JSON endpoint.
app.UseSwagger();

// Enable middleware to serve swagger-ui (HTML, JS, CSS, etc.), 
// specifying the Swagger JSON endpoint.
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
});
```

이제 앱을 빌드하고 실행할 수 있습니다. 브라우저의 주소 표시줄에서 `/swagger`로 이동합니다. 앱의 API 엔드포인트 및 모델 목록이 표시됩니다. 

![Visual Studio 2019 브라우저의 Swagger 페이지](media/vs-2019/vs2019-swagger-browser.png)

Games 아래에서 엔드포인트를 클릭한 다음, `Try it out` 및 `Execute`를 클릭하여 여러 가지 엔드포인트가 동작하는 방식을 확인합니다.

## <a name="next-steps"></a>다음 단계

다음 동영상에서는 Azure에 앱을 배포하는 방법을 알아봅니다.

[5단계: Azure에 ASP.NET Core 앱 배포](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>참조

- [Swashbuckle 및 ASP.NET Core 시작](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio)
- [Swagger/OpenAPI를 사용한 ASP.NET Core 웹 API 도움말 페이지](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2)