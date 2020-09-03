---
title: 솔루션 및 프로젝트 만들기
ms.date: 02/06/2018
ms.topic: how-to
f1_keywords:
- vs.openprojectfromweb
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19a836847aa01038bdbb015612c4fb4a3964d9a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770536"
---
# <a name="create-solutions-and-projects"></a>솔루션 및 프로젝트 만들기

*프로젝트*는 소스 코드 파일, 비트맵, 아이콘, 구성 요소 및 서비스 참조 등 Visual Studio에서 앱을 빌드하는 데 필요한 항목을 보관합니다. 새 프로젝트를 만들 때 Visual Studio는 해당 프로젝트를 포함할 *솔루션*을 만듭니다. 그런 다음 원하는 경우 다른 새 프로젝트나 기존 프로젝트를 솔루션에 추가할 수 있습니다. 특정 프로젝트에 연결되어 있지 않은 파일을 솔루션에 포함할 수도 있습니다.

![솔루션/프로젝트 계층 구조](./media/vside-proj-soln.png)

> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio에서 프로젝트 만들기](/visualstudio/mac/create-new-projects)를 참조하세요.

**솔루션 탐색기**라고 하는 도구 창에서 솔루션과 프로젝트를 볼 수 있습니다. 다음 스크린샷은 **솔루션 탐색기**에서 두 개의 프로젝트(**BikeSharing.Clients.Core** 및 **BikeSharing.Clients.Windows**)가 포함된 예제 솔루션(**BikeSharing.Xamarin-UWP**)을 보여줍니다. 각 프로젝트에는 여러 파일, 폴더 및 참조가 포함되어 있습니다. 굵게 표시된 프로젝트 이름은 *시작 프로젝트*, 즉 앱 실행 시 시작하는 프로젝트입니다. 어떤 프로젝트가 시작 프로젝트인지 지정할 수 있습니다.

![프로젝트와 솔루션 탐색기](./media/vside-solution-explorer-projects.png)

필요한 파일을 추가하여 프로젝트를 직접 구성할 수 있지만, Visual Studio는 시작할 수 있는 프로젝트 템플릿 모음을 제공합니다. 템플릿에서 새 프로젝트를 만들면 해당 프로젝트 형식에 대한 기본 사항이 포함된 프로젝트가 제공되며 파일 이름을 변경하거나 새 또는 기존 코드는 물론, 필요에 따라 기타 리소스를 추가할 수 있습니다.

Visual Studio에서 앱을 개발하는 데 솔루션과 프로젝트는 필요하지 않습니다. 클릭할 수도 Git에서 복제 하거나 다른 위치에서 다운로드 하는 코드를 열 수 있습니다. 자세한 내용은 [프로젝트 또는 솔루션 없이 Visual Studio에서 코드 개발](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)을 참조하세요.

## <a name="create-a-project-from-a-project-template"></a>프로젝트 템플릿에서 프로젝트 만들기

템플릿에서 새 프로젝트를 만드는 방법에 대한 자세한 내용은 [Visual Studio에서 새 프로젝트 만들기](create-new-project.md)를 참조하세요.

## <a name="create-a-project-from-existing-code-files"></a>기존 코드 파일에서 프로젝트 만들기

코드 소스 파일의 컬렉션이 있는 경우 프로젝트에 쉽게 추가할 수 있습니다.

1. 메뉴에서 **파일** > **새로 만들기** > **기존 코드의 프로젝트**를 선택합니다.

1. **기존 코드 파일에서 프로젝트 만들기** 마법사에서 **만들 프로젝트 형식** 드롭다운 목록 박스에서 원하는 프로젝트 형식을 선택하고 **다음** 단추를 선택합니다.

1. 마법사에서 파일의 위치로 이동한 다음 **이름** 상자에 새 프로젝트에 대한 이름을 입력합니다. 완료되면 **마침** 단추를 선택합니다.

> [!NOTE]
> 이 옵션은 상대적으로 간단한 파일 컬렉션에 적합합니다. 현재 C++, Apache Cordova, Visual Basic 및 C# 프로젝트 형식만 지원됩니다.

## <a name="add-files-to-a-solution"></a>솔루션에 파일 추가

솔루션의 readme 파일과 같이 여러 프로젝트에 적용되는 파일 또는 특정 프로젝트 아래가 아니라 논리적으로 솔루션 수준에 속하는 기타 파일이 있을 경우 솔루션 자체에 추가할 수 있습니다. 솔루션에 항목을 추가하려면 **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭하여 표시되는 상황에 맞는 메뉴에서 **추가** > **새 항목** 또는 **추가** > **기존 항목**을 선택합니다.

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>.NET Framework의 특정 버전을 대상으로 하는 .NET 프로젝트 만들기

.NET Framework 프로젝트를 만들 경우 프로젝트에서 사용하려는 특정 버전의 .NET Framework를 지정할 수 있습니다. (.NET Core 프로젝트를 만드는 경우에는 Framework 버전을 지정하지 않습니다.)

::: moniker range="vs-2017"

.NET Framework 버전을 지정하려면 **새 프로젝트** 대화 상자에서 **Framework** 드롭다운 메뉴를 선택합니다.

![새 프로젝트 대화 상자의 Framework 드롭다운](./media/vside-newproject-framework.png)

> [!NOTE]
> .NET Framework 4 이전 버전의 .NET Framework 버전에 액세스하려면 시스템에 .NET Framework 3.5가 설치되어 있어야 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

.NET Framework 버전을 지정하려면 **새 프로젝트 만들기** 페이지에서 **Framework** 드롭다운 메뉴를 선택합니다.

![새 프로젝트 구성의 Framework 선택기](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>빈 솔루션 만들기

프로젝트가 없는 빈 솔루션을 만들 수도 있습니다. 솔루션 및 프로젝트를 처음부터 만들려는 경우에 좋을 수 있습니다.

### <a name="to-create-an-empty-solution"></a>빈 솔루션을 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

::: moniker range="vs-2017"

2. 왼쪽(**템플릿**) 창의 확장된 목록에서 **기타 프로젝트 형식** > **Visual Studio 솔루션**을 선택합니다.

3. 가운데 창에서 **빈 솔루션**을 선택합니다.

4. 솔루션의 **이름** 및 **위치** 값을 입력한 다음, **확인**을 선택합니다.

::: moniker-end

::: moniker range=">=vs-2019"

2. **새 프로젝트 만들기** 페이지에서 **솔루션**을 검색 상자에 입력합니다.

3. **빈 솔루션** 템플릿을 선택한 후, **다음**을 클릭합니다.

4. 솔루션의 **이름** 및 **위치** 값을 입력한 다음, **만들기**를 선택합니다.

::: moniker-end

빈 솔루션을 만든 후 **프로젝트** 메뉴에서 **새 항목 추가** 또는 **기존 항목 추가**를 선택하여 새 프로젝트나 항목 또는 기존 프로젝트나 항목을 추가할 수 있습니다.

앞서 언급했듯이, 프로젝트나 솔루션 없이 코드 파일을 열 수도 있습니다. 이 방식으로 코드를 작성하는 방법에 대한 자세한 내용은 [프로젝트 또는 솔루션 없이 Visual Studio에서 코드 개발](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)을 참조하세요.

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>임시 프로젝트 만들기

(C# 및 Visual Basic만 해당)

디스크 위치를 지정하지 않고 .NET 기반 프로젝트를 만들 경우 임시 프로젝트입니다. 임시 프로젝트를 통해 .NET 프로젝트로 실험할 수 있습니다. 임시 프로젝트로 작업하는 동안 언제든지 프로젝트를 저장하거나 삭제할 수 있습니다.

임시 프로젝트를 만들려면 먼저 **도구** > **옵션** > **프로젝트 및 솔루션** > **일반**으로 이동하여 **만들어질 때 새 프로젝트 저장** 확인란의 선택을 취소합니다. 그런 다음, 일반적인 방법으로 **새 프로젝트**를 엽니다.

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>솔루션, 프로젝트 또는 항목 삭제

Visual Studio IDE를 사용하지 않고 솔루션 및 해당 콘텐츠를 영구적으로 삭제할 수 있습니다. Visual Studio 내에서 항목를 삭제하면 현재 솔루션 또는 프로젝트에서만 제거됩니다. 시스템에서 솔루션 또는 기타 구성 요소를 영구적으로 삭제하려면 파일 탐색기를 사용하여 *.sln* 및 *.suo* 솔루션 파일을 포함한 폴더를 삭제합니다. 그러나 솔루션을 영구적으로 삭제하기 전에 다시 필요한 경우에 대비하여 프로젝트 또는 파일을 백업하는 것이 좋습니다.

> [!NOTE]
> *.suo* 파일은 파일 탐색기의 기본 설정으로는 표시되지 않는 숨김 파일입니다. 숨겨진 파일을 표시하려면 파일 탐색기의 **보기** 메뉴에서는 **숨겨진 항목** 확인란을 선택합니다.

### <a name="permanently-delete-a-solution"></a>솔루션을 영구적으로 삭제

1. **솔루션 탐색기**에서 삭제하려는 솔루션의 오른쪽 클릭 메뉴(상황에 맞는 메뉴)에서 **파일 탐색기에서 폴더 열기**를 선택합니다.

1. 파일 탐색기에서 한 수준 위로 이동합니다.

1. 솔루션을 포함하는 폴더를 선택한 다음, **삭제** 키를 누릅니다.

## <a name="see-also"></a>참고 항목

- [솔루션 및 프로젝트](../ide/solutions-and-projects-in-visual-studio.md)
- [GitHub에 있는 Microsoft의 오픈 소스 리포지토리](https://github.com/Microsoft)
- [개발자 코드 샘플](https://code.msdn.microsoft.com/)
- [프로젝트 만들기(Mac용 Visual Studio)](/visualstudio/mac/create-new-projects)
