---
title: 옵션, 텍스트 편집기, C/C++, 실험적
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 7e239ad3d2091f334f18ec00a367fc47d5c21db3
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278705"
---
# <a name="options-text-editor-cc-experimental"></a>옵션, 텍스트 편집기, C/C++, 실험적

이러한 옵션을 변경하면 C 또는 C++에서 프로그래밍할 때 IntelliSense 및 검색 데이터베이스 관련 동작을 변경할 수 있습니다. 이러한 기능은 실험적이며 향후 릴리스의 Visual Studio에서 수정되거나 제거될 수 있습니다.

::: moniker range="vs-2017"

이 문서에서는 Visual Studio 2017의 옵션을 설명합니다. Visual Studio 2015의 경우 목차 위의 선택기에서 **2015**를 선택합니다.

::: moniker-end

이 속성 페이지에 액세스하려면 **Ctrl**+**Q**를 눌러 검색 상자를 활성화한 다음, **실험적**을 입력합니다. 검색에서 처음 몇 글자 후에 페이지를 찾습니다. **도구** > **옵션**을 선택하고 **텍스트 편집기**, **C/C++** 를 차례로 확장한 다음, **실험적**을 선택하여 액세스할 수도 있습니다.

이러한 기능은 Visual Studio 설치에서 사용할 수 있습니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. [Visual Studio IDE 개인 설정](../../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="enable-predictive-intellisense"></a>예측 IntelliSense 사용

예측 IntelliSense는 컨텍스트와 관련이 있는 결과만 표시되도록 IntelliSense 드롭다운 목록에 표시되는 결과의 수를 제한합니다. 예를 들어 `int x =`를 입력하고 IntelliSense 드롭다운을 호출하면 정수 또는 정수를 반환하는 함수만 표시됩니다. 예측 IntelliSense는 기본적으로 꺼져 있습니다.

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>빠른 프로젝트 로드 사용

Visual Studio 2017 버전 15.3부터 이 기능을 **프로젝트 캐싱 사용**이라고 하며 [VC++ 프로젝트 설정](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) 속성 페이지로 이동되었습니다.

이 옵션을 사용하면 다음에 프로젝트를 열 때 Visual Studio에서 프로젝트 데이터를 캐시할 수 있으며, 프로젝트 파일에서 다시 계산하지 않고 캐시한 데이터를 로드할 수 있습니다. 캐시한 데이터를 사용하면 프로젝트 로드 시간이 상당히 빨라집니다.

::: moniker-end

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Visual Studio Marketplace의 추가 기능

[Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads)에서 추가 텍스트 편집기 기능을 찾아볼 수 있습니다. 예제는 [C++ 빠른 조치 방법](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017)(영문)이며, 다음을 지원합니다.

- **누락된 #include 추가** - 코드의 알 수 없는 기호에 대해 관련 #include를 제안합니다.

- **네임스페이스/정규화 기호를 사용하여 추가** - 네임스페이스를 제외하고 이전 항목과 유사합니다.

- **누락된 세미콜론 추가**

- **온라인 도움말** - 오류 메시지에 대한 온라인 도움말 검색

- 기타...

## <a name="see-also"></a>참조

- [언어별 편집기 옵션 설정](../../ide/reference/setting-language-specific-editor-options.md)
- [C++에서의 리팩터링(VC 블로그)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
)
