---
title: 옵션, 텍스트 편집기, JavaScript, IntelliSense
ms.date: 10/29/2018
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.References
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Intellisense.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.IntelliSense.General
ms.assetid: b4a9816d-cf87-4dc6-a8d4-1591d6a48103
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3d030e028332bd57afe66eee31c888713721212
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68605972"
---
# <a name="options-dialog-box-text-editor--javascript--intellisense"></a>옵션 대화 상자: 텍스트 편집기 \> JavaScript \> IntelliSense

**옵션** 대화 상자의 **IntelliSense** 페이지를 사용하여 JavaScript용 IntelliSense의 동작에 영향을 주는 설정을 수정합니다. 메뉴 모음에서 **도구** > **옵션**을 선택한 다음, **텍스트 편집기** > **JavaScript/TypeScript** > **IntelliSense**를 차례로 확장하여 **IntelliSense** 페이지에 액세스할 수 있습니다.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

**IntelliSense** 페이지에는 다음과 같은 섹션이 포함되어 있습니다.

## <a name="statement-completion"></a>문 완성

이러한 옵션을 사용하여 IntelliSense 문 완성 동작을 변경할 수 있습니다.

### <a name="uielement-list"></a>UI 요소 목록

**Tab 또는 Enter 키만 사용하여 커밋**

이 확인란을 선택하면 JavaScript 코드 편집기에서는 **Tab** 키나 **Enter** 키를 선택한 후에만 완성 목록의 선택한 항목을 포함한 문이 추가됩니다. 이 확인란이 선택되어 있지 않으면 마침표, 쉼표, 콜론, 여는 괄호, 여는 중괄호({)와 같은 기타 문자로도 선택한 항목을 사용하여 명령문을 추가할 수 있습니다.

## <a name="references"></a>참조 항목

이러한 옵션을 사용하여 다른 JavaScript 프로젝트 형식의 범위에 있는 IntelliSense .js 파일의 형식을 지정할 수 있습니다. IntelliSense 참조는 일반적으로 전역 개체에 대한 IntelliSense 지원을 제공하기 위해 사용됩니다. 또한 이 페이지를 사용하여 런타임에 로드해야 하는 스크립트의 로드 순서를 설정하고 IntelliSense 확장 파일을 추가할 수 있습니다.

### <a name="uielement-list"></a>UI 요소 목록

**참조 그룹**

이 옵션은 참조 그룹의 형식을 지정합니다. 다음 세 가지 참조 그룹이 지원됩니다.

미리 정의된 참조 그룹을 사용하여 다른 JavaScript 프로젝트의 범위에 있는 특정 IntelliSense .js 파일을 지정할 수 있습니다. 다음 네 가지 참조 그룹을 사용할 수 있습니다.

- 암시적(Windows *버전*), JavaScript를 사용하는 [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] 앱용 이 그룹에 포함된 파일은 JavaScript를 사용하는 [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] 앱용 코드 편집기에 열려 있는 각 .js 파일의 범위에 있습니다.

- 암시적(웹), HTML5 프로젝트용 이 그룹에 포함된 파일은 이러한 프로젝트 형식용 코드 편집기에 열려 있는 각 .js 파일의 범위에 있습니다.

- 전용 작업자 참조 그룹, HTML5 웹 작업자용. 이 그룹에 지정된 파일은 전용 근로자 참조 그룹을 명시적으로 참조하는 .js 파일 범위에 속합니다.

- 일반, 다른 JavaScript 프로젝트 형식용

**포함된 파일**

이 옵션은 언어 서비스 컨텍스트에 로드되는 파일의 순서를 지정합니다. **제거**, **위로 이동**및 **아래로 이동** 단추를 사용하여 이 순서를 구성할 수 있습니다. IntelliSense가 제대로 작동하려면 다른 파일에 종속된 파일은 다른 파일 뒤에 로드해야 합니다.

> [!CAUTION]
> 하나의 개체가 두 개 이상의 암시적 참조에서 조건 없이 정의된 경우, 이 목록의 마지막 참조가 개체 정의에 사용됩니다.

**그룹에 참조 추가**

이 옵션은 해당하는 파일을 찾아 IntelliSense .js 파일을 추가하는 방법을 제공합니다.

**기타 파일 프로젝트의 파일에 대한 원격 참조(예: http://) 다운로드**

이 확인란을 선택하면 JavaScript 파일이 프로젝트의 컨텍스트 외부에 열려 있는 경우 Visual Studio에서는 IntelliSense 정보를 제공할 목적으로 파일에서 참조하는 원격 JavaScript 파일을 다운로드합니다. 이 옵션을 선택하는 경우 JavaScript 파일에 참조로 파일을 포함하면 해당 파일이 다운로드됩니다.

> [!NOTE]
> 웹 프로젝트의 경우 프로젝트에서 참조된 원격 파일이 기본적으로 다운로드됩니다.

## <a name="see-also"></a>참조

- [JavaScript IntelliSense](../../ide/javascript-intellisense.md)