---
title: Strings 요소 | Microsoft Docs
description: Strings 요소는 ButtonText 자식 요소 및 기타 선택적 자식 요소를 포함합니다. 텍스트 문자열의 앰퍼샌드는 바로 가기 키를 지정합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 27a649c7d3a8bb808153c280921d2304de59c379
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899409"
---
# <a name="strings-element"></a>Strings 요소
Strings 요소는 **최소한 ButtonText** 자식 요소를 포함해야 합니다. 다른 모든 자식 요소는 선택 사항입니다. '&' 및 '<'와 같은 잘못된 XML 문자는 엔터티(' &amp; ' 및 ' ' 등)로 코딩되어야 &lt; 합니다.

 텍스트 문자열의 앰퍼샌드는 명령의 바로 가기 키를 지정합니다.

## <a name="syntax"></a>구문

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|언어|선택 사항입니다. Language=".".|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|ButtonText|이 필드와 명령 정의의 다음 5개 텍스트 필드를 사용하면 다양한 메뉴에 표시되는 텍스트를 지정할 수 있습니다. 기본적으로 `ButtonText` 필드는 메뉴 컨트롤러에 나타납니다. 다른 텍스트 필드가 비어 있으면 `ButtonText` 필드도 기본값이 됩니다. `ButtonText`다른 텍스트 필드가 지정된 경우에도 필드를 비워 둘 수 없습니다.|
|Tooltiptext|`ToolTipText`필드는 메뉴 항목의 도구 설명에 표시되는 텍스트를 지정합니다.<br /><br /> `ToolTipText`필드가 비어 있으면 `ButtonText` 필드가 사용됩니다.|
|MenuText|`MenuText`필드는 주 메뉴, 도구 모음, 바로 가기 메뉴 또는 하위 메뉴에 있는 경우 명령에 대해 표시되는 텍스트를 지정합니다. `MenuText`필드가 비어 있으면 IDE(통합 개발 환경)에서 `ButtonText` 필드를 사용합니다. `MenuText`필드는 지역화에도 사용할 수 있습니다.<br /><br /> 바로 가기 메뉴의 경우 `MenuText` 필드는 바로 가기 메뉴 도구 모음에 표시되는 이름으로, IDE에서 바로 가기 메뉴를 사용자 지정할 수 있습니다. 따라서 바로 가기 메뉴의 이름을 구체적으로 지정해야 합니다. 예를 들어 "바로 가기" 대신 "위젯 패키지 바로 가기 메뉴"를 사용합니다.<br /><br /> 필드를 `MenuText` 지정하지 않으면 `ButtonText` 필드가 사용됩니다.|
|CommandName|필드는 사용자 `CommandName` 지정 대화 상자의 **명령** 탭에 있는 키보드  범주에 표시되는 텍스트를 지정합니다(도구  메뉴에서 **사용자 지정을** 클릭하여 사용 가능).|
|CanonicalName|영어 `CanonicalName` 필드는 메뉴 항목을 실행하기 위해 명령 창에 입력할 수 있는 **명령의** 이름을 영어 텍스트로 지정합니다. IDE는 문자, 숫자, 밑 줄 또는 포함된 마침표가 아닌 모든 문자를 제거합니다. 그런 다음, 이 텍스트가 필드에 결합되어 `ButtonText` 명령을 정의합니다. 예를 들어 파일 메뉴의 **새 프로젝트는** File.NewProject 명령이 됩니다. <br /><br /> 영어 필드를 지정하지 않으면 `CanonicalName` IDE는 필드를 사용하고 문자, 숫자, 밑 줄 및 `ButtonText` 포함된 마침표만 제외한 모든 것을 제거합니다. 예를 들어 단추 텍스트 "&명령 정의..." 는 앰퍼샌드, 공간 및 말임표가 제거되는 DefineCommands가 됩니다.<br /><br /> `TextChanges`플래그가 지정되고 명령 텍스트가 변경되면 **명령** 창에서 인식되는 해당 명령은 변경되지 않으며 원래 또는 영어 필드의 정식 형식으로 `ButtonText` 유지됩니다. `CanonicalName`|
|LocCanonicalName|`LocCanonicalName`필드는 영어 필드와 동일하게 `CanonicalName` 동작하지만 지역화된 명령 텍스트를 지정할 수 있습니다. 두 정식 필드를 모두 지정할 수 있습니다. IDE는 **명령** 창에 입력된 텍스트를 구문 분석하고 명령과 연결하기 때문에 영어 텍스트와 영어가 아닌 텍스트는 모두 동일한 명령에 연결될 수 있습니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Button 요소](../extensibility/button-element.md)|사용자가 상호 작용할 수 있는 요소를 정의합니다.|
|[Menu 요소](../extensibility/menu-element.md)|단일 메뉴 항목을 정의합니다.|
|[Combo 요소](../extensibility/combo-element.md)|콤보 상자에 표시되는 명령을 정의합니다.|

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
