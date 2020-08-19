---
title: '3단계: ASP.NET Core 앱에서 데이터 작업'
description: 이 동영상 자습서 및 단계별 지침을 통해 ASP.NET Core 웹앱에서 Entity Framework Core를 사용하여 데이터 작업을 시작합니다.
ms.custom: get-started
ms.date: 03/31/2019
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
ms.openlocfilehash: 42bc0442dc5901f92fc8a83b7af41c1fc42f4be4
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250798"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>3단계: Entity Framework를 사용하여 데이터 작업

다음 단계에 따라 ASP.NET Core 웹앱에서 Entity Framework Core를 사용하여 데이터 작업을 시작합니다.

_이 동영상을 보고 따라서 첫 번째 ASP.NET Core 앱에 데이터를 추가합니다._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>프로젝트 열기

해당 동영상을 따르는 경우 이전 섹션에서 만든 웹 애플리케이션 프로젝트를 엽니다. 여기에서 시작하는 경우에는 새 프로젝트를 만들고, **ASP.NET 웹 애플리케이션**을 선택한 다음, **웹 애플리케이션**을 선택해야 합니다. 나머지 옵션을 기본값으로 유지합니다.

## <a name="add-your-model"></a>모델 추가

ASP.NET Core 애플리케이션에서 데이터를 사용할 때 해야 할 첫 번째 작업은 데이터의 모양을 설명하는 것입니다. 이 설명은 해결하려는 문제에 관련된 항목의 ‘모델’을 만드는 것입니다.  실제 애플리케이션에서는 이 모델에 사용자 지정 비즈니스 논리를 추가하므로 애플리케이션이 특정 방식으로 동작하고 작업을 자동화할 수 있습니다. 이 샘플에서는 보드 게임을 추적하기 위한 간단한 시스템을 만들어 보겠습니다. 게임을 나타내고 게임에서 지원할 수 있는 플레이어 수 같이 해당 게임에 대해 기록하려는 몇 가지 속성을 포함하는 클래스가 필요합니다. 이 클래스는 ‘모델’이라는 웹 프로젝트의 루트에서 만들 새 폴더로 이동합니다. 

```csharp
public class Game
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int PublicationYear { get; set; }
    public int MinimumPlayers { get; set; }
    public int MaximumPlayers { get; set; }
}
```

## <a name="create-the-pages-to-manage-your-game-library"></a>게임 라이브러리를 관리할 페이지 만들기

이제 게임 라이브러리를 관리하는 데 사용할 페이지를 만들 준비가 되었습니다. 이 작업은 어려워 보일 수 있지만 실제로는 매우 쉽습니다. 먼저 앱에서 이 기능을 배치할 위치를 결정해야 합니다. 웹 프로젝트에서 Pages 폴더를 열고 새 폴더를 추가합니다. 폴더 이름을 *Games*로 지정합니다.

Games를 마우스 오른쪽 단추로 클릭하고 **추가** > **스캐폴드된 새 항목**을 선택합니다. **Entity Framework(CRUD)** 옵션을 사용하여 Razor Pages를 선택합니다. CRUD는 “만들기, 읽기, 업데이트, 삭제”를 나타내고 이 템플릿은 해당하는 각 작업의 페이지를 만듭니다(“모두 나열” 페이지 및 “한 항목의 세부 정보 보기” 페이지 포함).

![Visual Studio 2019 ASP.NET Core 스캐폴드된 페이지 추가](media/vs-2019/vs2019-add-scaffold.png)

사용자의 게임 모델 클래스를 선택하고 ‘+’ 아이콘을 사용하여 새 데이터 컨텍스트 클래스를 추가합니다. 이 EventHandler의 이름을 `AppDbContext`로 지정합니다. 나머지를 기본값으로 유지하고 **추가**를 클릭합니다.

Games 폴더에 다음 Razor Pages가 추가됩니다.

- Create.cshtml
- Delete.cshtml
- Details.cshtml
- Edit.cshtml
- Index.cshtml

![Visual Studio 2019 ASP.NET Core 스캐폴드된 페이지](media/vs-2019/vs2019-scaffolded-pages.png)

*Games* 폴더에 페이지를 추가할 뿐 아니라 스캐폴딩 작업은 내 *Startup.cs* 클래스에 코드를 추가했습니다. 이 클래스에서 `ConfigureServices` 메서드를 찾으면 이 코드가 추가된 것을 확인할 수 있습니다.

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

또한 `AppDbContext` 연결 문자열이 프로젝트의 *appsettings.json* 파일에 추가된 것을 알 수 있습니다.

아직 만들어진 데이터베이스가 없으므로 지금 앱을 실행하면 실패할 수 있습니다. [Program.cs에 일부 코드를 추가](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio#update-main)하여 필요한 경우 자동으로 데이터베이스를 만들도록 앱을 구성할 수 있습니다.

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<Data.AppDbContext>();
            context.Database.EnsureCreated();
        }
        catch (Exception ex)
        {
            var logger = services.GetRequiredService<ILogger<Program>>();
            logger.LogError(ex, "An error occurred creating the DB.");
        }
    }

    host.Run();
}
```

선행 코드의 유형 이름을 해결하려면 using 문의 기존 블록 끝에 있는 *Program.cs*에 다음 using 문을 추가합니다.

```csharp
using Microsoft.Extensions.DependencyInjection;
using WebApplication1.Models;
```

코드에서 WebApplication1 대신 프로젝트 이름을 사용해야 합니다.

대부분의 코드는 오류 처리에만 사용되고 앱이 실행되기 전에 EF Core `AppDbContext`에 대한 액세스를 제공합니다. 아직 존재하지 않는 데이터베이스를 만드는 `context.Database.EnsureCreated()`라는 줄이 중요합니다. 이제 앱을 실행할 준비가 되었습니다.

## <a name="test-it-out"></a>앱 테스트

애플리케이션을 실행하고 주소 표시줄에서 `/Games`로 이동합니다. 빈 목록 페이지가 표시됩니다. **새로 만들기**를 클릭하여 새 `Game`을 컬렉션에 추가합니다. 양식을 입력하고 **만들기**를 클릭합니다. 양식이 목록 보기에 표시됩니다. **세부 정보**를 클릭하여 단일 레코드의 세부 정보를 확인합니다.

다른 레코드를 추가합니다. 편집을 클릭하여 레코드의 세부 정보를 변경하거나, **삭제**를 클릭하여 레코드를 제거합니다. 레코드를 실제로 삭제하기 전에 확인 메시지가 표시됩니다. 

![Visual Studio 2019 ASP.NET Core 브라우저의 스캐폴드된 페이지](media/vs-2019/vs2019-game-list.png)

EF Core 및 Visual Studio 2019를 사용하여 ASP.NET Core 앱에서 데이터 작업을 시작하는 과정을 모두 살펴보았습니다.

## <a name="next-steps"></a>다음 단계

다음 동영상에서는 앱에 웹 API 지원을 추가하는 방법을 알아봅니다.

[4단계: ASP.NET Core 앱에서 웹 API 표시](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>참조

- [ASP.NET Core에서 Entity Framework Core를 사용한 Razor Pages](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio)
- [ASP.NET Core Razor Pages 및 EF Core](/aspnet/core/data/?view=aspnetcore-2.1)
