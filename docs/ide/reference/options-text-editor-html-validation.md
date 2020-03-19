---
title: 옵션, 텍스트 편집기, HTML(Web Forms), 유효성 검사
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ede4600cb1fa1df118b4635a193d8bff348d5119
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568284"
---
# <a name="options-text-editor-html-web-forms-validation"></a>옵션, 텍스트 편집기, HTML(Web Forms), 유효성 검사

**유효성 검사** 옵션 페이지를 사용하여 HTML 편집기에서 문서의 HTML 태그 구문이 올바른지 검사하는 방법에 대한 기본 설정을 지정합니다. 이 페이지에 액세스하려면 메뉴 모음에서 **도구** > **옵션**을 선택한 다음, **텍스트 편집기** > **HTML(Web Forms)**  > **유효성 검사**를 확장합니다.

## <a name="validation"></a>유효성 검사

- **유효성 검사 스키마 검색에 doctype 사용**

   각 스키마에 따라 해당 스키마에서 유효한 요소, 특성 및 대문자 표시가 결정됩니다. 또한 선택한 스키마에 따라 IntelliSense에서 사용할 수 있는 태그와 특성이 결정됩니다.

   Visual Studio에서 페이지의 **<!DOCTYPE>** 선언 및 **html** 요소의 콘텐츠를 사용하여 스키마를 결정하도록 하려면 이 옵션을 선택합니다. 예를 들어 페이지에 `<!DOCTYPE html>` 선언이 있는 경우 이 옵션을 선택하면 Visual Studio에서 HTML5 스키마를 사용합니다. 하지만 **html** 태그에 **xmlns** 특성(예: `<html xmlns="http://www.w3.org/1999/xhtml">`)이 포함된 경우에는 Visual Studio에서 XHTML5 스키마를 사용합니다.

- **doctype을 찾을 수 없을 때의 대상**

   페이지에 **<!DOCTYPE>** 선언이 없는 경우 유효성을 검사할 스키마를 선택합니다.

  - **오류 표시**

     유효성 검사를 사용하려면 확인란을 선택합니다. 이 확인란을 선택하지 않으면 편집기는 유효성 검사 오류를 표시하지 않습니다.

     다른 확인란을 사용하여 편집기에서 표시하게 할 오류의 개별 유형을 지정하여 유효성 검사를 세부 조정할 수 있습니다.

     > [!NOTE]
     > 일부 스키마는 오류의 개별 유형을 표시하는 옵션을 제공하지 않습니다. 예를 들어 대상 스키마로 **XHTML 1.1**을 선택한 경우 모든 옵션 확인란이 사용하지 않도록 설정됩니다. 이 경우 모든 오류 유형이 표시됩니다.

## <a name="see-also"></a>참고 항목

- [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)
