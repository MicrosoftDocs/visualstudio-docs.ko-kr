---
title: 버튼 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05bd73764e96a27a92d741f144c222acc48fa518
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739934"
---
# <a name="button-element"></a>버튼 요소
사용자가 상호 작용할 수 있는 요소를 정의합니다. 단추는 단추, 메뉴 단추 및 분할 드롭다운과 같은 다양한 종류가 될 수 있습니다.

## <a name="syntax"></a>구문

```
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">
  <Parent>... </Parent>
  <Icon>... </Icon>
  <CommandFlag>... </CommandFlag>
  <Strings>... </Strings>
</Button>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|guid|필수 사항입니다. GUID/ID 명령 식별자의 GUID입니다.|
|id|필수 사항입니다. GUID/ID 명령 식별자의 ID입니다.|
|priority|(선택 사항) 우선 순위를 지정하는 숫자 값입니다.|
|type|(선택 사항) 단추의 종류를 지정하는 예인된 값입니다.<br /><br /> 지정되지 않은 경우 단추를 사용합니다.<br /><br /> 단추<br /> 도구 모음(일반적으로 상징적인 단추), 메뉴 및 컨텍스트 메뉴에 나타나는 표준 명령입니다.<br /><br /> 메뉴 버튼<br /> 명령을 실행하지 않지만 다른 메뉴를 생성하는 메뉴 항목입니다.<br /><br /> 분할 드롭다운<br /> Microsoft Word의 표준 도구 모음에서 수행 취소 및 다시 하기 단추와 같은 컨트롤입니다.|
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[부모 요소](../extensibility/parent-element.md)|(선택 사항) 단추의 상위 요소입니다.|
|[아이콘 요소](../extensibility/icon-element.md)|(선택 사항) 단추와 연결된 아이콘입니다.|
|[명령 플래그 요소](../extensibility/command-flag-element.md)|필수 사항입니다. 단추에 대 한 유효한 CommandFlag 값은 다음과 같습니다.<br /><br /> - 허용파라름<br /><br /> - 커맨드웰만<br /><br /> - 기본 사용 안 함<br /><br /> - 기본 보이지 않는<br /><br /> - 돈트캐시<br /><br /> - 동적 항목 시작<br /><br /> - 동적 가시성<br /><br /> - 수정 메뉴 컨트롤러<br /><br /> - 아이콘및텍스트<br /><br /> - 버튼 없음 사용자 정의<br /><br /> - 사용자 지정 없음<br /><br /> - 노키 커스터마이징<br /><br /> - 노쇼온메뉴컨트롤러<br /><br /> - 픽트 (것)와 같은<br /><br /> - 포스트엑섹<br /><br /> - 제안 된 Cmd<br /><br /> - 루트토독스<br /><br /> - 텍스트캐서스유스Btn<br /><br /> - 텍스트 메뉴사용버튼<br /><br /> - 텍스트 변경 사항<br /><br /> - 텍스트 변경 버튼<br /><br /> - 텍스트 컨텍스트 사용 버튼<br /><br /> - 텍스트 메뉴CtrluseMenu<br /><br /> - 텍스트 메뉴사용버튼<br /><br /> - 텍스트 만|
|[문자열 요소](../extensibility/strings-element.md)|필수 사항입니다. 자식 [ButtonText 요소를](../extensibility/buttontext-element.md) 정의해야 합니다.|
|주석|선택적 주석.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[단추 요소](../extensibility/buttons-element.md)|단추 요소를 그룹화합니다.|

## <a name="example"></a>예제
 다음 예제에서는 *.vsct* 파일의 단추를 정의합니다.

 ```xml
<Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
    <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
    <Icon guid="guidImages" id="bmpPic1" />
    <CommandFlag>TextChanges</CommandFlag>
    <Strings>
          <CommandName>cmdidMyCommand</CommandName>
          <ButtonText>My Command name</ButtonText>
    </Strings>
</Button>
 ```

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
