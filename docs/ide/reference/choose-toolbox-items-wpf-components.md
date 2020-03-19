---
title: 도구 상자 항목 선택, WPF 구성 요소
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 731fe05e90e01c60f0a7ff3a14917d6d7625bc1e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570559"
---
# <a name="choose-toolbox-items-wpf-components"></a>도구 상자 항목 선택, WPF 구성 요소

**도구 상자 항목 선택** 대화 상자의 이 탭에는 로컬 컴퓨터에서 사용할 수 있는 WPF(Windows Presentation Foundation) 컨트롤 목록이 표시됩니다. 이 목록을 표시하려면 **도구** 메뉴에서 **도구 상자 항목 선택**을 선택하여 **도구 상자 항목 선택** 대화 상자를 표시하고 **WPF 구성 요소** 탭을 선택합니다. 나열된 구성 요소를 정렬하려면 열 머리글을 선택합니다.

- 구성 요소 옆의 확인란이 선택되면 해당 구성 요소의 아이콘이 **도구 상자**에 표시됩니다.

    > [!TIP]
    > WPF 컨트롤을 편집용으로 열린 프로젝트 문서에 추가하려면 해당 **도구 상자** 아이콘을 디자인 보기 화면으로 끌어서 놓습니다. 구성 요소의 기본 태그 및 코드가 프로젝트에 삽입되고 이제 수정할 수 있습니다. 자세한 내용은 [도구 상자](../../ide/reference/toolbox.md)를 참조하세요.

- 구성 요소 옆의 확인란이 선택 취소되면 해당 아이콘이 **도구 상자**에서 제거됩니다.

    > [!NOTE]
    > 구성 요소의 아이콘이 **도구 상자**에 표시되는지 여부에 관계없이 컴퓨터에 설치된 .NET 구성 요소를 계속 사용할 수 있습니다.

**WPF 구성 요소** 탭에는 다음 정보가 포함됩니다.

**이름**

컴퓨터의 레지스트리에 있는 항목에 대한 WPF 컨트롤의 이름을 나열합니다.

**네임스페이스**

구성 요소 구조를 정의하는 [.NET API](/dotnet/api/?view=netframework-4.7) 네임스페이스의 계층 구조를 표시합니다. 컴퓨터에 설치된 각 .NET 네임스페이스 내에서 사용 가능한 구성 요소를 나열하려면 이 열을 기준으로 정렬합니다.

**어셈블리 이름**

각 구성 요소의 네임스페이스가 포함된 .NET 어셈블리의 이름을 표시합니다. 컴퓨터에 설치된 각 .NET 어셈블리에 포함된 네임스페이스를 나열하려면 이 열을 기준으로 정렬합니다.

**디렉터리**

.NET 어셈블리의 위치를 표시합니다. 모든 어셈블리의 기본 위치는 전역 어셈블리 캐시(GAC)입니다. 전역 어셈블리 캐시에 대한 자세한 내용은 [어셈블리 및 전역 어셈블리 캐시 사용](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac)을 참조하세요.

## <a name="uielement-list"></a>UI 요소 목록

### <a name="filter"></a>필터

입력란에 제공하는 문자열을 기준으로 WPF 컨트롤 목록을 필터링합니다. 4개 열에서 모든 일치 항목이 표시됩니다.

**지우기**

필터 문자열을 지웁니다.

**찾아보기**

WPF 컨트롤이 포함된 어셈블리로 이동할 수 있는 **열기** 대화 상자를 엽니다. 전역 어셈블리 캐시에 없는 어셈블리를 로드하려면 이 요소를 사용합니다.

**언어**

선택된 WPF 컨트롤이 포함된 어셈블리의 지역화된 언어를 표시합니다.

## <a name="limitations"></a>제한 사항

사용자 지정 컨트롤 또는 <xref:System.Windows.Controls.UserControl>을 도구 상자에 추가할 경우 다음과 같은 제한 사항이 있습니다.

- 현재 프로젝트 외부에서 정의된 사용자 지정 컨트롤에만 적용됩니다.

- 솔루션 구성을 디버그에서 릴리스로 또는 릴리스에서 디버그로 변경하면 제대로 업데이트되지 않습니다. 이는 참조가 프로젝트 참조가 아니라 디스크의 어셈블리에 대한 참조이기 때문입니다. 컨트롤이 현재 솔루션에 포함된 경우 디버그에서 릴리스로 변경하면 프로젝트에서는 계속해서 컨트롤의 디버그 버전을 참조합니다.

또한 디자인 타임 메타데이터가 사용자 지정 컨트롤에 적용되고 이 메타데이터에서 [Microsoft.Windows.Design.ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100))가 `false`로 설정되도록 지정하면 컨트롤이 도구 상자에 표시되지 않습니다.

컨트롤에 대한 네임스페이스 및 어셈블리를 매핑하면 XAML에서 직접 컨트롤을 참조할 수 있습니다.

## <a name="see-also"></a>참조

- [도구 상자](../../ide/reference/toolbox.md)
- [WPF 시작](../../designers/getting-started-with-wpf.md)
