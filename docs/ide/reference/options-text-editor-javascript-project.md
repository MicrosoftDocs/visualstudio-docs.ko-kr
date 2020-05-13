---
title: 옵션, 텍스트 편집기, JavaScript, 프로젝트
ms.date: 1/15/2019
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 190cbdb2a8096415985d83fc525b997572d252c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68605923"
---
# <a name="options-text-editor-javascript-project"></a>옵션, 텍스트 편집기, JavaScript, 프로젝트

**옵션** 대화 상자의 **프로젝트** 페이지를 사용하여 코드 편집기에서 JavaScript 및 TypeScript 프로젝트 옵션을 지정합니다. 이 페이지에 액세스하려면 메뉴 모음에서 **도구** > **옵션**을 선택한 다음, **텍스트 편집기** > **JavaScript/TypeScript** > **프로젝트**를 확장합니다.

## <a name="project-analysis-options"></a>프로젝트 분석 옵션

이 옵션은 편집기에서 프로젝트를 분석하고, 진단을 보고하고, 개선 사항을 제안하는 방법을 결정합니다. 옵션을 선택하거나 선택 취소하여 편집기에서 해당 상황을 처리하는 방법을 지정합니다.

### <a name="uielement-list"></a>UIElement 목록

- **편집기에서 열린 파일이 있는 프로젝트만 분석**
- **편집기에 열려 있는 파일에 대한 진단만 보고**
- **수정이 아닌 가능한 개선 사항 제안**

## <a name="virtual-projects-in-solution-explorer"></a>솔루션 탐색기의 가상 프로젝트

이 옵션을 사용하여 솔루션이 로드되거나 로드되지 않을 경우 가상 프로젝트를 표시할지 여부를 선택할 수 있습니다.

## <a name="compile-on-save"></a>저장 시 컴파일

이 옵션은 프로젝트의 일부가 아닌 TypeScript 파일이 자동으로 컴파일되는지 여부를 결정합니다. 확인란을 선택한 후 사용할 코드 생성 유형을 선택합니다.

### <a name="uielement-list"></a>UIElement 목록

- **프로젝트의 일부가 아닌 모듈에 대해 AMD 코드 생성 사용**
- **프로젝트의 일부가 아닌 모듈에 대해 CommonJS 코드 생성 사용**
- **프로젝트의 일부가 아닌 모듈에 대해 UMD 코드 생성 사용**
- **프로젝트의 일부가 아닌 모듈에 대해 시스템 코드 생성 사용**
- **프로젝트의 일부가 아닌 모듈에 대해 ES2015 코드 생성 사용**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>프로젝트에 포함되지 않는 파일에 대한 ECMAScript 버전

이 옵션을 사용하여 프로젝트의 일부가 아닌 파일의 ECMAScript 버전을 선택할 수 있습니다. **ECMAScript 3**, **ECMAScript 5** 또는 **ECMAScript 6** 중에서 선택할 수 있습니다.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>프로젝트에 포함되지 않는 TSX 파일에 대한 JSX 내보내기

이 옵션은 편집기에서 프로젝트의 일부가 아닌 TypeScript 파일이 처리하는 방법을 결정합니다.

### <a name="uielement-list"></a>UIElement 목록

|옵션|Description|
|------------|-----------------|
|**React Framework**|이 옵션을 선택하면 코드 편집기에서 *.js* 파일 확장명을 내보냅니다.|
|**Preserve**|이 옵션을 선택하면 코드 편집기에서 JSX를 출력의 일부로 유지하고 *.jsx* 파일 확장명을 내보냅니다.|

## <a name="see-also"></a>참고 항목

- [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)