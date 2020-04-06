---
title: 콤보 엘리먼트 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739813"
---
# <a name="combo-element"></a>콤보 요소
콤보 상자에 나타나는 명령을 정의합니다. 드롭다운콤보, 다이나믹콤보, 인덱스콤보, MRUCombo의 콤보 박스는 네 종류가 있습니다.

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

|attribute|설명|
|---------------|-----------------|
|guid|필수 사항입니다. GUID/ID 명령 식별자의 GUID입니다.|
|id|필수 사항입니다. GUID/ID 명령 식별자의 ID입니다.|
|기본 너비|필수 사항입니다. 콤보 상자의 픽셀 너비를 지정하는 정수입니다.|
|idCommandList|필수 사항입니다. 콤보 상자에 표시할 항목 목록을 검색하기 위해 활성 명령 대상으로 전송되는 ID입니다. ID는 컨트롤과 동일한 GUID 범위에 있습니다.|
|priority|(선택 사항) 우선 순위를 지정하는 숫자 값입니다.|
|type|(선택 사항) 단추 유형을 지정하는 예인된 값입니다.<br /><br /> 지정되지 않은 경우 단추를 사용합니다.<br /><br /> 드롭다운콤보<br /> VSPackage는 이 콤보 상자의 내용을 채우는 작업을 담당합니다. 사용자는 이 드롭다운의 텍스트 상자에 아무 것도 입력할 수 없습니다.<br /><br /> 다이나믹콤보<br /> VSPackage는 이 콤보 상자의 내용을 채울 책임이 있습니다. 사용자는 이 콤보를 편집하고 해당 콤보에 있는 항목을 선택할 수도 있습니다.<br /><br /> 인덱스 콤보<br /> DynamicCombo와 동일하지만 텍스트가 아닌 항목의 인덱스를 발생시면 됩니다.<br /><br /> MRU콤보<br /> VSPackage를 대신하여 통합 개발 환경(IDE)으로 채워져 있습니다.  사용자는 이 콤보 상자에서 편집할 수 있습니다. IDE는 콤보 상자당 마지막 16개의 항목을 기억합니다.<br /><br /> 사용자가 콤보 상자에서 무언가를 선택하거나 새로운 것을 입력하면 IDE는 적절한 VSPackage에 대해 통보합니다.|
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|Parent|(선택 사항) 단추의 상위 요소입니다.|
|커맨드 플래그|필수 사항입니다. [명령 플래그 요소를](../extensibility/command-flag-element.md)참조하십시오. 단추에 대 한 유효한 CommandFlag 값은 다음과 같습니다.<br /><br /> - 케이스감미성<br /><br /> - 커맨드웰만<br /><br /> - 기본 사용 안 함<br /><br /> - 기본 보이지 않는<br /><br /> - 동적 가시성<br /><br /> - 필터 키<br /><br /> - 아이콘및텍스트<br /><br /> - 자동 완성 없음<br /><br /> - 버튼 없음 사용자 정의<br /><br /> - 사용자 지정 없음<br /><br /> - 노키 커스터마이징<br /><br /> - 늘이보수평|
|문자열|필수 사항입니다. [문자열 요소를](../extensibility/strings-element.md)참조하십시오. 자식 ButtonText 요소를 정의해야 합니다.|
|주석|선택적 주석.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[명령 요소](../extensibility/commands-element.md)|VSPackage 도구 모음에서 명령 컬렉션을 나타냅니다.|

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

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
