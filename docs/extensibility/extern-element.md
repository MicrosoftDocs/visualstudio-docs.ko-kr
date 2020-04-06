---
title: 외향적 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cf6f9db77abaa7034af8d074b9833a4c1560f07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711495"
---
# <a name="extern-element"></a>외향적 요소
Extern 요소는 컴파일 타임에 *.vsct* 파일과 병합할 외부*헤더(.h)* 파일을 참조합니다. 병합할 파일은 VSCT 컴파일러에 제공된 포함 경로에 있거나 Include [요소에서](../extensibility/include-element.md)참조해야 합니다. 파일은 다른 *.vsct* 파일 또는 C++ 헤더 파일일 수 있습니다.

 헤더 파일의 정의는 "#define [기호] [값]" 이전에 정의된 경우 값이 다른 기호일 수 있습니다. 정의는 명령 항목의 조건부 문에 사용할 수 있습니다. 실제로 사용되지 않는 기호는 삭제됩니다.

 커맨드 테이블 엘리먼트 익스테르 니어

## <a name="syntax"></a>구문

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|href|필수 사항입니다. 헤더 파일에 대한 경로:<br /><br /> href="stdidcmd.h"|
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|
|언어|(선택 사항) 모든 문자열의 기본 언어는 명령 테이블의 요소를 [ \<>.](../extensibility/strings-element.md)<br /><br /> 언어="en-us"|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|없음|없음|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[명령 테이블 요소](../extensibility/commandtable-element.md)|VSPackage가 IDE에 제공하는 명령(즉, 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자)을 나타내는 모든 요소를 정의합니다.|

## <a name="example"></a>예제

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>참조
- [비주얼 스튜디오 명령 테이블 (.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
