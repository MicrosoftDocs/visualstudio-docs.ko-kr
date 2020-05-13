---
title: 명령 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739689"
---
# <a name="commands-element"></a>Commands 요소
VSPackage 도구 모음에서 명령 컬렉션을 나타냅니다. 컬렉션에는 메뉴, 그룹, 단추, 콤보 및 비트맵이 최대 5개의 하위 섹션을 가질 수 있습니다.

 각 하위 섹션 하위 요소(예: \<메뉴>)는 GUID 및 숫자 식별자 쌍인 고유 명령 ID로 식별됩니다. GUID는 "명령 집합"을 식별하고 논리적으로 관련된 명령을 그룹화하는 데 사용됩니다. VSPackage는 다른 VSPackage에서 정의한 명령 아이디와의 충돌을 방지하기 위해 자체 명령 집합을 정의해야 합니다.

## <a name="syntax"></a>구문

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|패키지|명령을 제공하는 VSPackage를 식별하는 GUID입니다.<br /><br /> 예를 들어 패키지="guidVsPackage1Pkg".|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[메뉴 요소](../extensibility/menus-element.md)|VSPackage가 구현하는 모든 메뉴를 정의합니다.|
|[요소 그룹](../extensibility/groups-element.md)|VSPackage에서 명령 그룹을 정의하는 항목을 포함합니다.|
|[단추 요소](../extensibility/buttons-element.md)|단추 요소를 그룹화합니다.|
|[비트맵 요소](../extensibility/bitmaps-element.md)|비트맵 요소를 그룹화합니다.|
|[콤보 요소](../extensibility/combos-element.md)|콤보 요소를 그룹화합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[명령 테이블 요소](../extensibility/commandtable-element.md)|VSPackage가 IDE에 제공하는 명령을 나타내는 모든 요소를 정의합니다. 가능한 요소는 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자입니다.|

## <a name="example"></a>예제
 다음 예제에서는 명령 요소를 사용하는 방법을 보여 [주십습니다.](../extensibility/commands-element.md)

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>참조
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
