---
title: C#프로그램을 실행하는 방법
description: Visual Studio에서 C# 프로그램을 실행하는 방법에 대한 초보자 가이드입니다.
ms.custom: get-started
ms.date: 10/16/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2ffe52fc2bf7d05084307b4d972e45f4b1d2acdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "76928107"
---
# <a name="how-to-run-a-c-program-in-visual-studio"></a>방법: Visual Studio에서 C# 프로그램 실행

프로그램을 실행하기 위해 수행하는 작업은 시작하는 항목, 프로그램, 앱 또는 서비스의 형식, 디버거에서 실행할지 여부에 따라 달라집니다. 가장 간단한 경우, Visual Studio에서 프로젝트를 열었을 때 **Ctrl**+**F5**(**디버깅하지 않고 시작**) 또는 **F5**(**디버깅하여 시작**)를 눌러 빌드하고 실행하거나 기본 Visual Studio 도구 모음의 녹색 화살표(**시작 단추**)를 누릅니다.

![시작 단추를 보여 주는 스크린샷](media/vs-start-button.png)

## <a name="starting-from-a-project"></a>프로젝트에서 시작

C# 프로젝트( *.csproj* 파일)가 있는 경우 실행할 수 있습니다(실행할 수 있는 프로그램인 경우). 프로젝트가 `Main` 메서드를 사용하는 C# 파일을 포함하고 출력이 실행 파일(EXE)인 경우, 성공적으로 빌드되면 실행됩니다.

Visual Studio의 프로젝트에 프로그램에 대한 코드가 이미 있다면 프로젝트를 엽니다. 프로젝트를 열려면 Windows 파일 탐색기에서 *.csproj*를 두 번 클릭 하거나, Visual Studio에서 **프로젝트 열기**를 선택하고 프로젝트( *.csproj*) 파일을 찾은 다음 프로젝트 파일을 선택합니다.

Visual Studio에서 프로젝트를 로드한 후 **Ctrl**+**F5**(**디버깅하지 않고 시작**)를 누르거나 Visual Studio 도구 모음에서 녹색 **시작** 단추를 사용하여 프로그램을 실행합니다.  여러 프로젝트가 있는 경우 `Main` 메서드를 사용하는 프로젝트가 시작 프로젝트로 설정되어야 합니다. 시작 프로젝트를 설정하려면 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택합니다.

![시작 프로젝트 설정](media/set-as-startup-project.png)

Visual Studio가 프로젝트를 빌드하고 실행하려고 합니다.  빌드 오류가 발생하면 **출력** 창에 빌드 출력이 표시되고 **오류 목록** 창에 오류가 표시됩니다.

빌드가 성공하면 앱이 프로젝트 형식에 적합한 방식으로 실행됩니다. 콘솔 앱은 터미널 창에서 실행되고, Windows 데스크톱 앱은 새 창에서 시작되며, 웹앱은 브라우저(IIS Express에서 호스팅)에서 시작됩니다.

## <a name="starting-from-code"></a>코드에서 시작

코드 목록, 코드 파일 또는 적은 수의 파일에서 시작하는 경우, 먼저 실행하려는 코드가 신뢰할 수 있는 소스에서 실행되고 실행 가능한 프로그램인지 확인합니다. `Main` 메서드가 있는 경우 콘솔 앱 템플릿을 사용하여 Visual Studio에서 작업할 프로젝트를 만들 수 있는 실행 가능한 프로그램으로 계획되었을 가능성이 큽니다.

### <a name="code-listing-for-a-single-file"></a>단일 파일에 대한 코드 목록

Visual Studio를 시작하고 빈 C# 콘솔 프로젝트를 연 다음 프로젝트에 이미 있는 .cs 파일에 있는 모든 코드를 선택하고 삭제합니다. 그런 다음 코드의 내용을 .cs 파일에 붙여넣습니다. 코드를 붙여넣을 때 이전에 있던 코드를 덮어쓰거나 삭제합니다. 원본 코드와 일치하도록 파일의 이름을 바꿉니다.

### <a name="code-listings-for-a-few-files"></a>몇 개의 파일에 대한 코드 목록

Visual Studio를 시작하고 빈 C# 콘솔 프로젝트를 연 다음 프로젝트에 이미 있는 .cs 파일에 있는 모든 코드를 선택하고 삭제합니다. 그런 다음 첫 번째 코드 파일의 내용을 .cs 파일에 붙여넣습니다. 원본 코드와 일치하도록 파일의 이름을 바꿉니다. 

두 번째 파일의 경우 **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하여 프로젝트에 대한 바로 가기 메뉴를 열고, **추가 >기존 항목**(또는 **Shift**+**Alt**+**A** 키 조합 사용)을 선택한 다음 코드 파일을 선택합니다.

### <a name="multiple-files-on-disk"></a>디스크의 여러 파일

1. 적절한 형식의 새 프로젝트를 만듭니다(확실하지 않을 경우 C# **콘솔 앱**을 사용).

2. 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **기존 항목**을 눌러 파일을 선택하고 선택한 파일을 프로젝트로 가져옵니다.  

### <a name="starting-from-a-folder"></a>폴더에서 시작

파일이 많은 폴더를 사용해 작업하는 경우 먼저 프로젝트나 솔루션이 있는지 확인합니다.  Visual Studio를 사용하여 프로그램이 만들어진 경우 프로젝트 파일 또는 솔루션 파일을 찾아야 합니다. *.csproj* 확장명 또는 .sln 확장명을 사용하여 파일을 찾은 다음 Windows 파일 탐색기에서 해당 파일 중 하나를 두 번 클릭하여 Visual Studio에서 엽니다. [Visual Studio 솔루션 또는 프로젝트에서 시작](#starting-from-a-project)을 참조하세요.

다른 개발 환경에서 코드가 개발된 경우처럼 프로젝트 파일이 없는 경우 Visual Studio에서 **폴더 열기** 메서드를 사용하여 최상위 폴더를 엽니다. [프로젝트 또는 솔루션 없이 코드 개발](../../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)을 참조하세요.

## <a name="starting-from-a-github-or-azure-devops-repo"></a>GitHub 또는 Azure DevOps 리포지토리에서 시작

실행하려는 코드가 GitHub 또는 Azure DevOps 리포지토리에 있는 경우 Visual Studio를 사용하여 리포지토리에서 직접 프로젝트를 열 수 있습니다. [리포지토리에서 프로젝트 열기](../tutorial-open-project-from-repo.md)를 참조하세요.

## <a name="run-the-program"></a>프로그램 실행

프로그램을 시작하려면 기본 Visual Studio 도구 모음에서 녹색 화살표(**시작 단추**)를 누르거나, **F5** 또는 **Ctrl**+**F5**를 눌러 프로그램을 실행합니다. **시작** 단추를 사용하는 경우 디버거에서 실행됩니다.  Visual Studio가 프로젝트에서 코드를 빌드하고 실행하려고 합니다.  성공한다면 좋은 일입니다. 그러나 그렇지 않은 경우 성공적으로 빌드하는 방법에 대한 몇 가지 아이디어를 계속 읽어보세요.

## <a name="troubleshooting"></a>문제 해결

코드에 오류가 있을 수 있습니다. 하지만 코드가 올바른데 다른 어셈블리 또는 NuGet 패키지에 종속되거나 다른 버전의 .NET을 대상으로 작성된 경우 쉽게 수정할 수 있습니다.

### <a name="add-references"></a>참조 추가

제대로 빌드하려면 코드가 올바르고 라이브러리 또는 기타 종속성에 대한 올바른 참조가 설정되어 있어야 합니다. 빨간색 물결선과 **오류 목록**을 보고 프로그램을 컴파일하고 실행하기 전에 오류가 있는지 확인할 수 있습니다. 확인되지 않은 이름과 관련된 오류가 표시되는 경우 참조 또는 using 지시문을 추가하거나 둘 다를 추가해야 합니다. 코드에서 어셈블리 또는 NuGet 패키지를 참조하는 경우 해당 참조를 프로젝트에 추가해야 합니다.

Visual Studio는 누락된 참조를 식별하도록 도와줍니다. 이름을 확인할 수 없으면 편집기에 전구 아이콘이 표시됩니다. 전구를 클릭하면 문제를 해결하는 방법에 대한 몇 가지 제안을 확인할 수 있습니다. 다음을 수정할 수 있습니다.

- using 지시문 추가
- 어셈블리에 대한 참조 추가 또는
- NuGet 패키지를 설치합니다.

#### <a name="missing-using-directive"></a>using 지시문 누락

예를 들어 다음 화면에서 코드 파일의 시작 부분에 `using System;`을 추가하여 확인되지 않은 이름 `Console`을 확인할 수 있습니다.

![using 지시문을 추가하는 전구 스크린샷](media/name-does-not-exist2.png)

#### <a name="missing-assembly-reference"></a>어셈블리 참조 누락

.NET 참조는 어셈블리 또는 NuGet 패키지 양식이 될 수 있습니다. 일반적으로 소스 코드를 찾으면 게시자 또는 작성자가 어떤 어셈블리가 필요한지, 그리고 코드가 종속된 패키지가 무엇인지 설명합니다. 프로젝트에 대한 참조를 수동으로 추가하려면 **솔루션 탐색기**에서 **참조** 노드를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택한 다음 필요한 어셈블리를 찾습니다.

![참조 추가 메뉴의 스크린샷](media/add-reference.png)

[참조 관리자를 사용하여 참조 추가 또는 제거](../../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)의 지침에 따라 어셈블리를 찾고 참조를 추가할 수 있습니다.

#### <a name="missing-nuget-package"></a>NuGet 패키지 누락

Visual Studio가 누락된 NuGet 패키지를 감지하면 전구가 나타나고 전구를 설치하는 옵션이 제공됩니다.

![패키지를 설치할 전구 스크린샷](media/lightbulb-add-package.png)

이 문제가 해결되지 않고 Visual Studio가 패키지를 찾지 못하는 경우 온라인으로 검색해 보세요. [Visual Studio에서 NuGet 패키지 설치 및 사용](/nuget/quickstart/install-and-use-a-package-in-visual-studio)을 참조하세요.

## <a name="use-the-right-version-of-net"></a>올바른 버전의 .NET 사용

.NET Framework의 서로 다른 버전은 이전 버전과 호환성을 가지므로 최신 프레임워크는 수정 없이 이전 프레임워크용으로 작성된 코드를 실행할 수 있습니다. 그러나 특정 프레임워크를 대상으로 해야 하는 경우도 있습니다. .NET Framework 또는 .NET Core가 아직 설치되지 않은 경우 특정 버전을 설치해야 할 수도 있습니다. [Visual Studio 수정](../../install/modify-visual-studio.md)을 참조하세요.

대상 프레임워크를 변경하려면 [대상 프레임워크 변경](../../ide/visual-studio-multi-targeting-overview.md#select-a-target-framework-version)을 참조하세요. 자세한 내용은 [.NET Framework 대상 지정 오류 문제 해결](../../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계

[Visual studio IDE 시작](../visual-studio-ide.md)을 읽고 Visual Studio 개발 환경을 살펴보세요.

## <a name="see-also"></a>참조

[첫 번째 C# 앱 만들기](tutorial-console.md)
