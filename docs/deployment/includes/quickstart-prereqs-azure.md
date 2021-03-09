---
ms.openlocfilehash: 3ffab1767817189c8bf27c699713354979425d21
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101750859"
---
## <a name="prerequisites"></a>사전 요구 사항

::: moniker range=">=vs-2019"

* 선택한 언어에 적절한 워크로드를 사용하여 설치된 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
  * ASP.NET: **ASP.NET 및 웹 개발**
  * Node.js: **Node.js 개발**
::: moniker-end
::: moniker range="vs-2017"
* 선택한 언어에 적절한 워크로드를 사용하여 설치된 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
  * ASP.NET: **ASP.NET 및 웹 개발**
  * Node.js: **Node.js 개발**
::: moniker-end

* Azure 구독 아직 구독하지 않은 경우 [무료로 등록합니다](https://azure.microsoft.com/free/dotnet/). 이는 30일 동안 $200의 크레딧 및 12개월의 인기 있는 무료 서비스를 포함합니다.

* ASP.NET, ASP.NET Core, .NET Core 또는 Node.js 프로젝트. 프로젝트가 아직 없는 경우 아래 옵션을 선택합니다.
  * ASP.NET Core: [빠른 시작: Visual Studio를 사용하여 첫 ASP.NET Core 웹앱 만들기](../../ide/quickstart-aspnet-core.md) 또는 다음 단계를 수행합니다.
    ::: moniker range=">=vs-2019"
    Visual Studio 2019의 시작 창에서 **새 프로젝트 만들기** 를 선택합니다. 시작 창이 열려 있지 않으면 **파일** > **시작 창** 을 선택합니다. 검색 상자에 **web app** 을 입력하고 **C#** 을 언어로 선택한 다음 **ASP.NET Core 웹 애플리케이션(Model-View-Controller)** 을 선택한 후 **다음** 을 선택합니다. 다음 화면에서 프로젝트 이름을 **MyASPApp** 로 지정한 후 **다음** 을 선택합니다.

    권장되는 대상 프레임워크(.NET Core 3.1) 또는 .NET 5를 선택한 후 **만들기** 를 선택합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017에서 **파일** > **새 프로젝트** 를 선택하고 **Visual C#**  >  **.NET Core** 를 선택한 다음, **ASP.NET Core 웹 애플리케이션** 을 선택합니다. 메시지가 표시되면 **웹 애플리케이션(Model-View-Controller)** 템플릿을 선택하고, **인증 안 함** 이 선택되었는지 확인한 다음, **확인** 을 선택합니다.
    ::: moniker-end
  * Node.js: [빠른 시작: Visual Studio를 사용하여 첫 번째 Node.js 앱 만들기](../../ide/quickstart-nodejs.md)를 따르거나 **파일** > **새 프로젝트** 를 사용하고, **JavaScript** 를 선택한 다음, **빈 Node.js 웹 애플리케이션** 을 선택합니다.

* 배포 단계를 수행하기 전에 **빌드 > 솔루션 빌드** 메뉴 명령을 사용하여 프로젝트를 빌드해야 합니다.