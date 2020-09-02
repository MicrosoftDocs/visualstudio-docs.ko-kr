---
title: Combo 요소 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ff9d9e20ec221a86f1cce5f9c43a4e47ed6dc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739813"
---
# <a name="combo-element"></a>Combo 요소
콤보 상자에 표시 되는 명령을 정의 합니다. DropDownCombo, DynamicCombo, IndexCombo 및 MRUCombo의 네 가지 종류의 콤보 상자가 있습니다.

## <a name="syntax"></a>구문

```xml
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">
  <Parent>... </Parent
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</combo>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|guid|필수 요소. GUID/ID 명령 식별자의 GUID입니다.|
|id|필수 요소. GUID/ID 명령 식별자의 ID입니다.|
|defaultWidth|필수 요소. 콤보 상자의 픽셀 너비를 지정 하는 정수입니다.|
|idCommandList|필수 요소. 콤보 상자에 표시할 항목 목록을 검색 하기 위해 활성 명령 대상으로 전송 되는 ID입니다. ID는 컨트롤과 동일한 GUID 범위에 있습니다.|
|priority|선택 사항입니다. 우선 순위를 지정 하는 숫자 값입니다.|
|형식|선택 사항입니다. 단추의 유형을 지정 하는 열거형 값입니다.<br /><br /> 지정 하지 않으면 단추를 사용 합니다.<br /><br /> DropDownCombo<br /> VSPackage는이 콤보 상자에 대 한 내용을 입력 해야 합니다. 사용자는이 드롭다운의 텍스트 상자에 아무것도 입력할 수 없습니다.<br /><br /> DynamicCombo<br /> VSPackage는이 콤보 상자의 내용을 채우는 일을 담당 합니다. 사용자가이 콤보 상자를 편집 하 고 항목을 선택할 수도 있습니다.<br /><br /> IndexCombo<br /> DynamicCombo와 동일 합니다. 단, 해당 텍스트가 아닌 항목의 인덱스를 발생 시킵니다.<br /><br /> M... 콤보<br /> VSPackage를 대신 하 여 IDE (통합 개발 환경)로 채웁니다.  사용자가이 콤보 상자에서 편집할 수 있습니다. IDE는 콤보 상자 당 마지막 16 개 항목을 기억 합니다.<br /><br /> 사용자가 콤보 상자에서 항목을 선택 하거나 새로운 항목을 입력 하면 IDE에서 적절 한 VSPackage에 알립니다.|
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|Parent|선택 사항입니다. 단추의 부모 요소입니다.|
|CommandFlag|필수 요소. [명령 플래그 요소](../extensibility/command-flag-element.md)를 참조 하세요. 단추에 대 한 유효한 CommandFlag 값은 다음과 같습니다.<br /><br /> -CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -필터 키<br /><br /> -IconAndText<br /><br /> -NoAutoComplete 완성<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> - StretchHorizontally|
|문자열|필수 요소. [Strings 요소](../extensibility/strings-element.md)를 참조 하세요. 자식 ButtonText 요소를 정의 해야 합니다.|
|주석|선택적 설명입니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Commands 요소](../extensibility/commands-element.md)|VSPackage 도구 모음에 있는 명령 컬렉션을 나타냅니다.|

## <a name="example"></a>예제

```xml
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>

<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"
  priority="0x0500" type="DropDownCombo" defaultWidth="100"
  idCommandList="cmdidGetInsertOptionsList">
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">
  <CommandFlag>DynamicVisibility</CommandFlag>
  <Strings>
    <ButtonText>Select Insert Options</ButtonText>
  </Strings>
</Combo>
```

## <a name="see-also"></a>참고 항목
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
