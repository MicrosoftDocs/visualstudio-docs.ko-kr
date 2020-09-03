---
title: 프로젝트에 NuGet 패키지 포함하기
description: 이 문서에서는 Mac용 Visual Studio를 사용하여 프로젝트에 NuGet 패키지를 포함하는 방법을 설명합니다. 여기에서는 IDE 통합 기능을 소개할 뿐 아니라 패키지를 찾아 다운로드하는 방법도 살펴봅니다.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/01/2019
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 4200f466c079247d3efa036f4f7cca2fd2d6b5d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74127200"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Mac용 Visual Studio에서 NuGet 패키지 설치 및 관리

Mac용 Visual Studio의 NuGet 패키지 관리자 UI를 사용하여 프로젝트 및 솔루션에서 NuGet 패키지를 쉽게 설치, 제거 및 업데이트할 수 있습니다. .NET Core, ASP.NET Core 및 Xamarin 프로젝트를 검색하고 패키지를 추가할 수 있습니다.

이 문서에서는 프로젝트에 NuGet 패키지를 포함하는 방법을 설명하고 이 프로세스를 원활하게 하는 도구 체인을 보여줍니다.

Mac용 Visual Studio에서 NuGet을 사용하는 방법에 대해서는 [빠른 시작: Mac용 Visual Studio에서 패키지 설치 및 사용](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)을 참조하세요.

## <a name="find-and-install-a-package"></a>패키지 찾기 및 설치

1. Mac용 Visual Studio에서 프로젝트를 열어 놓고, **Solution Pad**에서 **종속성** 폴더(Xamarin 프로젝트를 사용하는 경우 **패키지** 폴더)를 마우스 오른쪽 단추로 클릭한 다음, **NuGet 패키지 관리...** 를 선택합니다.

    ![새 NuGet 패키지 컨텍스트 작업 추가하기](media/nuget-walkthrough-packages-menu.png)

2. **NuGet 패키지 관리** 창이 시작됩니다. 중앙 NuGet 패키지 리포지토리를 검색하도록, 대화 상자의 왼쪽 위에 있는 [소스] 드롭다운이 `nuget.org`로 설정되어 있는지 확인합니다.

    ![NuGet 패키지 목록](media/nuget-walkthrough-add-packages1.png)

3. 오른쪽 위의 검색 상자를 사용하여 특정 패키지(예: `EntityFramework`)를 검색합니다. 사용하려는 패키지를 찾았다면 해당 패키지를 선택하고 **패키지 추가** 단추를 클릭하여 설치를 시작합니다.

    ![EntityFramework NuGet 패키지 추가](media/nuget-walkthrough-add-packages2.png)

4. 패키지가 다운로드된 후 프로젝트에 추가됩니다. 솔루션은 편집 중인 프로젝트의 형식에 따라 변경됩니다.

    **Xamarin 프로젝트**
    * **참조** 노드는 NuGet 패키지의 일부인 모든 어셈블리의 목록을 포함합니다.
    * **패키지** 노드는 다운로드한 각 NuGet 패키지를 표시합니다. 이 목록에서 패키지를 업데이트하거나 제거할 수 있습니다.
    
    **.NET Core 프로젝트**

    * **종속성 > NuGet** 노드에 다운로드한 각 NuGet 패키지가 표시됩니다. 이 목록에서 패키지를 업데이트하거나 제거할 수 있습니다.

## <a name="using-nuget-packages"></a>NuGet 패키지 사용하기

NuGet 패키지를 추가하고 프로젝트 참조를 업데이트하면 모든 프로젝트 참조와 같은 방식으로 API에 대해 프로그래밍할 수 있습니다.

파일 상단에 필요한 `using` 지시문을 추가했는지 확인하세요.

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>패키지 업데이트

패키지 업데이트는 **종속성** 노드(Xamarin 프로젝트의 경우 **패키지** 노드)를 마우스 오른쪽 단추로 클릭하여 한 번에 모두 수행하거나, 각 패키지에서 개별적으로 수행할 수 있습니다. 새 버전의 NuGet 패키지를 사용할 수 있는 경우, 업데이트 아이콘이 ![원이 있는 위쪽 화살표](media/nuget-walkthrough-update-icon.png) 모양으로 표시됩니다.

**종속성**을 마우스 오른쪽 단추로 클릭하여 상황에 맞는 메뉴에 액세스하고 **업데이트**를 선택하여 모든 패키지를 업데이트합니다.

![패키지 메뉴](media/nuget-walkthrough-packages-menu-update.png)

* **NuGet 패키지 관리** - 프로젝트에 패키지를 더 추가하기 위한 창을 엽니다.
* **업데이트** - 각 패키지에 대해 소스 서버를 확인하고 모든 최신 버전을 다운로드합니다.
* **복원** - 기존 패키지를 최신 버전으로 업데이트하지 않고 모든 누락된 패키지를 다운로드합니다.

업데이트 및 복원 옵션은 솔루션 수준에서도 사용 가능하며, 솔루션 내의 모든 프로젝트에 영향을 줍니다.

### <a name="locating-outdated-packages"></a>오래된 패키지 찾기
solution pad에서 현재 설치된 패키지 버전을 확인하 고 업데이트할 패키지를 마우스 오른쪽 단추로 클릭할 수 있습니다.

![업데이트, 제거, 새로 고침 옵션이 있는 패키지 메뉴](media/nuget-walkthrough-PackageMenu.png)

패키지의 새 버전을 사용할 수 있는 경우 패키지 이름 옆에 알림이 표시되므로 업데이트할지 여부를 결정할 수 있습니다.

![새 패키지 버전을 사용할 수 있을 때 표시되는 알림](media/nuget-walkthrough-package-update-available.png)

표시된 메뉴에는 두 가지 옵션이 있습니다.

* **업데이트** - 소스 서버를 확인하고 새 버전(있는 경우)을 다운로드합니다.
* **제거** - 이 프로젝트에서 패키지를 제거하고 프로젝트의 참조에서 관련 어셈블리를 제거합니다.

## <a name="manage-packages-for-the-solution"></a>솔루션 패키지 관리

솔루션의 패키지를 관리하는 것은 여러 프로젝트를 동시에 사용할 수 있는 편리한 방법입니다.

1. 솔루션을 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리...** 를 선택합니다.

    ![솔루션에 대한 NuGet 패키지 관리](media/nuget-walkthrough-manage-packages-solution.png)

1. 솔루션의 패키지를 관리할 때 UI를 사용하여 작업의 영향을 받는 프로젝트를 선택할 수 있습니다.

    ![솔루션의 패키지를 관리할 경우의 프로젝트 선택기](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>통합 탭

여러 프로젝트를 사용하는 솔루션에서 작업하는 경우, 각 프로젝트에서 같은 NuGet 패키지를 사용하는 모든 위치에서 해당 패키지의 같은 버전 번호를 사용하고 있는지도 확인하는 것이 좋습니다. Mac용 Visual Studio에서는 솔루션의 패키지를 관리하도록 선택하면 패키지 관리자 UI에 **통합** 탭이 제공되어 이 작업을 더 쉽게 수행할 수 있습니다. 이 탭을 사용하여 솔루션의 다른 프로젝트에서 고유한 버전 번호가 있는 패키지가 사용되는 위치를 쉽게 확인할 수 있습니다.

![패키지 관리자 UI 통합 탭](media/nuget-walkthrough-consolidate-tab.png)

이 예제에서 NuGetDemo 프로젝트는 Microsoft.EntityFrameworkCore 2.20을 사용하고 있는 반면, NuGetDemo.Shared는 Microsoft.EntityFrameworkCore 2.2.6을 사용하고 있습니다. 패키지 버전을 통합하려면 다음을 수행합니다.

- 프로젝트 목록에서 업데이트할 프로젝트를 선택합니다.
- **새 버전** 목록에서 모든 프로젝트에서 사용할 버전을 선택합니다(예: Microsoft.EntityFrameworkCore 3.0.0).
- **패키지 통합** 단추를 선택합니다.

패키지 관리자가 선택한 모든 프로젝트에 선택한 패키지 버전을 설치하면, 해당 패키지가 더 이상 **통합** 탭에 표시되지 않습니다.

## <a name="adding-package-sources"></a>패키지 소스 추가하기

설치에 사용할 수 있는 패키지를 처음에는 nuget.org에서 검색합니다. 하지만 Mac용 Visual Studio에 다른 패키지 위치를 추가할 수 있습니다. 이는 개발 중인 자체 NuGet 패키지를 테스트하거나, 회사나 조직 내에서 개인 NuGet 서버를 사용할 때 유용할 수 있습니다.

Mac용 Visual Studio에서 **Visual Studio > 기본 설정 > NuGet > 소스**로 이동하여 패키지 소스의 목록을 보고 편집합니다. 소스는 (URL로 지정된) 원격 서버 또는 로컬 디렉터리일 수 있습니다.

![패키지 소스](media/nuget-walkthrough-PackageSource.png)

새로운 소스를 설정하려면 **추가**를 클릭합니다. 패키지 소스에 식별 이름과 URL(또는 파일 경로)을 입력하세요. 소스가 보안 웹 서버인 경우에는 사용자 이름과 암호도 입력하고, 그렇지 않은 경우에는 비워둡니다.

![패키지 소스 추가](media/nuget-walkthrough-PackageSource2.png)

그런 다음 패키지를 검색할 때 서로 다른 소스를 선택할 수 있습니다.

![패키지 소스 추가](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>버전 제어

NuGet 설명서에서는 [소스 제어에 패키지를 커밋하지 않고 NuGet을 사용하는 방법](/nuget/consume-packages/packages-and-source-control)에 대해 논의합니다. 소스 제어에 이진 파일 및 사용되지 않은 정보를 저장하지 않으려는 경우 Mac용 Visual Studio를 구성하여 서버에서 패키지를 자동으로 복원할 수 있습니다. 즉, 개발자가 소스 제어에서 프로젝트를 처음 검색하는 경우에는 Mac용 Visual Studio에서 필요한 패키지를 자동으로 다운로드하고 설치합니다.

![패키지를 자동으로 복원](media/nuget-walkthrough-AutoRestore.png)

추적 대상에서 `packages` 디렉터리를 제외하는 방법에 대한 자세한 내용은 해당 소스 제어 설명서를 참조하세요.

## <a name="related-video"></a>관련 동영상

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>참조

* [Visual Studio에서 패키지 설치 및 사용(Windows에서)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
