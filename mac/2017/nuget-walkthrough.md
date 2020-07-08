---
title: 프로젝트에 NuGet 패키지 포함하기
description: 이 문서에서는 Xamarin 프로젝트에 NuGet 패키지를 포함하는 방법을 다룹니다. 여기에서는 IDE 통합 기능을 소개할 뿐 아니라 패키지를 찾아 다운로드하는 방법도 살펴봅니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: 58d749a1d014288754dcd9eb7e620730933d742a
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950408"
---
# <a name="include-a-nuget-package-in-your-project"></a>프로젝트에 NuGet 패키지 포함

NuGet은 가장 인기 있는 .NET 개발용 패키지 관리자이며 Mac용 Visual Studio와 Windows용 Visual Studio에 내장되어 있습니다. 두 IDE 중 하나를 사용하여 패키지를 검색하고 Xamarin.iOS 및 Xamarin.Android 프로젝트에 추가할 수 있습니다.

이 문서에서는 프로젝트에 NuGet 패키지를 포함하는 방법을 설명하고 이 프로세스를 원활하게 하는 도구 체인을 보여줍니다.

## <a name="nuget-in-visual-studio-for-mac"></a>Mac용 Visual Studio의 NuGet

NuGet 패키지 기능을 보여주기 위해 먼저 새로운 애플리케이션을 만들고 여기에 패키지를 추가하는 방법을 살펴보겠습니다. 그런 다음 패키지 관리를 돕는 IDE 기능에 대해 논의하겠습니다.

## <a name="create-a-new-project"></a>새 프로젝트 만들기

먼저 아래 그림과 같이 `HelloNuget`이라는 이름의 프로젝트를 만듭니다. 이 예제에서는 iOS Single View Application 템플릿을 보여주지만, 지원되는 모든 프로젝트 형식을 사용할 수 있습니다.

![새 iOS 프로젝트 만들기](media/nuget-walkthrough-NewProject.png)

## <a name="adding-a-package"></a>패키지 추가하기

Mac용 Visual Studio에서 프로젝트를 연 상태로 **Solution Pad**의 **패키지** 폴더를 마우스 오른쪽 단추로 클릭하고 **패키지 추가**를 선택합니다.

![새 NuGet 패키지 컨텍스트 작업 추가하기](media/nuget-walkthrough-PackagesMenu.png)

이렇게 하면 **패키지 추가** 창이 시작됩니다. 소스 드롭다운이 `nuget.org`로 설정되어 있는지 확인하세요.

![소스 목록 드롭다운](media/nuget-walkthrough-Source.png)

창이 열리면 기본 패키지 소스인 nuget.org에서 패키지 목록이 로드됩니다. 초기 결과는 다음과 같습니다.

![NuGet 패키지 목록](media/nuget-walkthrough-AddPackages1.png)

오른쪽 위의 검색 상자를 사용하여 특정 패키지(예: `azure`)를 검색합니다. 사용하려는 패키지를 찾아서 선택하고 **패키지 추가** 단추를 클릭하여 설치를 시작합니다.

[Azure NuGet 패키지 추가하기](media/nuget-walkthrough-AddPackages2.png)

패키지가 다운로드된 후 프로젝트에 추가됩니다. 솔루션은 다음과 같이 변경됩니다.

* **참조** 노드는 NuGet 패키지의 일부인 모든 어셈블리의 목록을 포함합니다.
* **패키지** 노드는 다운로드한 각 NuGet 패키지를 표시합니다. 이 목록에서 패키지를 업데이트하거나 제거할 수 있습니다.
* **packages.config** 파일이 프로젝트에 추가됩니다. 이 XML 파일은 이 프로젝트에서 참조하는 패키지 버전을 IDE에서 추적하는 데 사용됩니다. 이 파일은 직접 편집해서는 안 되며, 버전 제어를 통해 보관해야 합니다. packages.config 파일 대신 project.json 파일을 사용할 수 있습니다. project.json 파일은 NuGet 3에 도입된 새로운 패키지 파일 형식으로, 전이적 복원을 지원합니다. project.json에 대한 자세한 내용은 [NuGet 설명서](/NuGet/Schema/Project-Json)에서 확인할 수 있습니다. project.json 파일은 수동으로 추가해야 하고 Mac용 Visual Studio에서 project.json 파일을 사용하려면 프로젝트를 닫은 후 다시 열어야 합니다.

## <a name="using-nuget-packages"></a>NuGet 패키지 사용하기

NuGet 패키지를 추가하고 프로젝트 참조를 업데이트하면 모든 프로젝트 참조와 같은 방식으로 API에 대해 프로그래밍할 수 있습니다.

파일 상단에 필요한 `using` 지시문을 추가했는지 확인하세요.

```csharp
using Newtonsoft.Json;
```

대부분의 NuGet은 NuGet 소스에 대한 README 또는 프로젝트 페이지 링크와 같은 추가 정보를 제공합니다. 이에 대한 링크는 일반적으로 [패키지 추가] 페이지의 패키지 안내에서 찾을 수 있습니다.

[프로젝트 페이지 링크 보기](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>패키지 업데이트

패키지 업데이트는 **패키지** 노드를 마우스 오른쪽 단추로 클릭하여 한꺼번에 수행하거나, 각 구성 요소마다 마우스 오른쪽 단추로 클릭하여 개별적으로 수행할 수 있습니다.

상황에 맞는 메뉴에 액세스하려면 **패키지**를 마우스 오른쪽 단추로 클릭하세요.

![패키지 메뉴](media/nuget-walkthrough-PackagesMenu.png)

* **패키지 추가** - 프로젝트에 패키지를 더 추가하기 위한 창을 엽니다.
* **업데이트** - 각 패키지에 대해 소스 서버를 확인하고 모든 최신 버전을 다운로드합니다.
* **복원** - 기존 패키지를 최신 버전으로 업데이트하지 않고 모든 누락된 패키지를 다운로드합니다.

업데이트 및 복원 옵션은 솔루션 수준에서도 사용 가능하며, 솔루션 내의 모든 프로젝트에 영향을 줍니다.

또한 개별 패키지를 마우스 오른쪽 단추로 클릭하여 상황에 맞는 메뉴에 액세스할 수 있습니다.

![패키지 메뉴](media/nuget-walkthrough-PackageMenu.png)

* **버전 번호** - 버전 번호는 비활성화된 메뉴 항목이며, 정보 제공 용도로만 표시됩니다.
* **업데이트** - 소스 서버를 확인하고 새 버전(있는 경우)을 다운로드합니다.
* **제거** - 이 프로젝트에서 패키지를 제거하고 프로젝트의 참조에서 관련 어셈블리를 제거합니다.

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
