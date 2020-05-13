---
title: 문자열 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db44db8926b523665a21c00b710dcee55749ab89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699726"
---
# <a name="strings-element"></a>Strings 요소
문자열 요소에는 최소한 **ButtonText** 자식 요소가 포함되어야 합니다. 다른 모든 자식 요소는 선택 사항입니다. '&' 및 '<'과 같은 유효하지 않은 XML 문자는 엔터티로 코딩되어야 합니다('&amp;및 '&lt;' 등등).

 텍스트 문자열의 앰퍼샌드는 명령에 대한 키보드 단축키를 지정합니다.

## <a name="syntax"></a>구문

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|언어|(선택 사항) 언어 =".".|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|단추 텍스트|이 필드와 명령 정의의 다음 5개의 텍스트 필드를 사용하면 다양한 메뉴에 나타나는 텍스트를 지정할 수 있습니다. 기본적으로 `ButtonText` 필드는 메뉴 컨트롤러에 나타납니다. 다른 `ButtonText` 텍스트 필드가 비어 있는 경우에도 필드가 기본값이 됩니다. 다른 `ButtonText` 텍스트 필드를 지정한 경우에도 필드를 비워둘 수 없습니다.|
|Tooltiptext|필드는 `ToolTipText` 메뉴 항목에 대한 도구 설명에 나타나는 텍스트를 지정합니다.<br /><br /> 필드가 `ToolTipText` 비어 있으면 `ButtonText` 필드가 사용됩니다.|
|메뉴 텍스트|이 `MenuText` 필드는 주 메뉴, 도구 모음, 바로 가기 메뉴 또는 하위 메뉴에 있는 경우 명령에 대해 표시되는 텍스트를 지정합니다. 필드가 `MenuText` 비어 있으면 통합 개발 환경(IDE)이 `ButtonText` 필드를 사용합니다. 필드를 `MenuText` 지역화에도 사용할 수 있습니다.<br /><br /> 바로 가기 메뉴의 `MenuText` 경우 필드는 바로 가기 메뉴 도구 모음에 표시되는 이름으로, IDE에서 바로 가기 메뉴를 사용자 지정할 수 있습니다. 따라서 바로 가기 메뉴의 이름을 구체적으로 지정해야 합니다. 예를 들어 "바로 가기" 대신 "위젯 패키지 바로 가기 메뉴"를 사용합니다.<br /><br /> `MenuText` 필드를 지정하지 않으면 필드가 `ButtonText` 사용됩니다.|
|CommandName|이 `CommandName` 필드는 **사용자 지정** 대화 상자의 **명령** 탭에서 키보드 범주에 나타나는 텍스트를 지정합니다(도구 메뉴에서 **Tools** **사용자 지정을** 클릭하여 사용 가능).|
|정식이름|영어 `CanonicalName` 필드는 메뉴 항목을 실행 하기 위해 **명령** 창에 입력할 수 있는 영어 텍스트에서 명령의 이름을 지정 합니다. IDE는 문자, 숫자, 밑줄 또는 포함된 기간이 아닌 모든 문자를 제거합니다. 그런 다음 이 텍스트를 `ButtonText` 필드에 연결하여 명령을 정의합니다. 예를 들어 **파일** 메뉴의 **새 프로젝트는** File.NewProject 명령이 됩니다.<br /><br /> 영어 `CanonicalName` 필드를 지정하지 않으면 IDE는 `ButtonText` 필드를 사용하고 문자, 숫자, 밑줄 및 포함된 기간을 제외한 모든 필드를 제거합니다. 예를 들어 단추 텍스트 "&명령 정의..." 이 때 는 [Ampersand], 공백 및 타원이 제거되는 정의 명령이 된다.<br /><br /> 플래그를 `TextChanges` 지정하고 명령의 텍스트가 변경되면 **Command** 창에서 인식하는 해당 명령은 변경되지 않습니다. 그것은 원래 `ButtonText` 또는 영어 `CanonicalName` 필드의 정식 형태로 남아있다.|
|로크캐니컬네임|필드는 `LocCanonicalName` 영어 `CanonicalName` 필드와 동일하게 작동하지만 지역화된 명령 텍스트를 지정할 수 있습니다. 두 표준 필드를 모두 지정할 수 있습니다. IDE는 **명령** 창에 입력된 텍스트를 구문 분석하여 명령과 연결하기 때문에 영어 텍스트와 영어 이외의 텍스트는 동일한 명령과 연결할 수 있습니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[Button 요소](../extensibility/button-element.md)|사용자가 상호 작용할 수 있는 요소를 정의합니다.|
|[Menu 요소](../extensibility/menu-element.md)|단일 메뉴 항목을 정의합니다.|
|[Combo 요소](../extensibility/combo-element.md)|콤보 상자에 나타나는 명령을 정의합니다.|

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
