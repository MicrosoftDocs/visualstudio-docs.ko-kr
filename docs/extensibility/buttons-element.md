---
title: 버튼 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64ac5621093f30af28ade0817906b767231e4ee1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739923"
---
# <a name="buttons-element"></a>단추 요소
개별 명령을 나타내는 [단추](../extensibility/button-element.md) 요소 그룹입니다.

## <a name="syntax"></a>구문

```
<Buttons>
  <Button>... </Button>
  <Button>... </Button>
</Buttons>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[단추 요소](../extensibility/buttons-element.md)|단추 요소를 그룹화합니다.|
|[버튼 요소](../extensibility/button-element.md)|사용자가 상호 작용할 수 있는 명령을 정의합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[명령 요소](../extensibility/commands-element.md)|VSPackage 도구 모음에서 명령 컬렉션을 나타냅니다.|

## <a name="example"></a>예제

```
<Buttons>
  <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button">
    <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/>
    <Icon guid="guidGenericCmdBmp" id="bmpArrow"/>
    <Strings>
      <ButtonText>C# Command Sample</ButtonText>
    </Strings>
  </Button>
</Buttons>
```

## <a name="see-also"></a>참조
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
