---
title: Extern 요소 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711495"
---
# <a name="extern-element"></a>Extern 요소
Extern 요소는 컴파일 타임에 *. vsct* 파일과 병합할 외부 헤더 파일 (*.h*)을 참조 합니다. 병합할 파일은 VSCT 컴파일러에 지정 된 포함 경로에 있거나 [include 요소](../extensibility/include-element.md)에서 참조 되어야 합니다. 파일은 다른 *. vsct* 파일 또는 c + + 헤더 파일 일 수 있습니다.

 헤더 파일의 정의는 "#define [Symbol] [Value]" 형식 이어야 합니다. 이전에 정의 된 경우 값은 다른 기호가 될 수 있습니다. 명령 항목의 조건 문에 정의를 사용할 수 있습니다. 실제로 사용 하지 않는 기호는 무시 됩니다.

 CommandTable 요소 Extern 요소

## <a name="syntax"></a>구문

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|href|필수 요소. 헤더 파일에 대 한 경로입니다.<br /><br /> href = "stdidcmd"|
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|
|language|선택 사항입니다. 명령 테이블의 모든 요소에 대 한 기본 언어 [\<Strings>](../extensibility/strings-element.md) :<br /><br /> language = "en-us"|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|없음|없음|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|VSPackage IDE에 제공 하는 명령, 즉 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자를 나타내는 모든 요소를 정의 합니다.|

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

## <a name="see-also"></a>참고 항목
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [명령, 메뉴 및 도구 모음](../extensibility/internals/commands-menus-and-toolbars.md)
