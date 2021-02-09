---
title: 기호 요소 | Microsoft Docs
description: 기호 요소는 다른 VSCT 요소에 사용 되는 Guid 및 Id를 정의 합니다. 이 문서에는 예제가 포함 되어 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 173da18ca3b38dd64b8a2594c03abd83987f58f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839324"
---
# <a name="symbols-element"></a>Symbols 요소
다른 VSCT 요소에 사용 되는 Guid 및 Id를 정의 합니다. 비관리 코드의 경우이 정보는 일반적으로 [Extern 요소](../extensibility/extern-element.md)에 지정 된 헤더 파일에서 가져옵니다. 관리 코드는 기호 요소의 자식 요소를 사용 하 여이 정보를 정의 합니다.

 기존 .cto 파일에서 .cvsct 파일을 만들면 기호가 symbol 요소의 자식으로 생성 됩니다. 자세한 내용은 [방법: 만들기를 참조 하세요. 기존에서 vsct 파일 Cto 파일](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 기호 요소는 전처리기에서 사용할 이름-값 쌍을 정의 하는 [Define 요소](../extensibility/define-element.md)와 혼동 해서는 안 됩니다.

## <a name="syntax"></a>구문

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|Description|
|---------------|-----------------|
|None||

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|GuidSymbol|GUID 기호를 정의 합니다. GuidSymbol에는 이름 및 값의 두 가지 필수 특성이 있습니다. 이름은 기호의 이름이 고, 값은 GUID의 값입니다.<br /><br /> 예를 들면 다음과 같습니다.\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|기호를 정의 합니다. IDSymbol에는 이름 및 값의 두 가지 필수 특성이 있습니다. 이름은 기호의 이름이 고, 값은 기호 값을 나타내는 문자열입니다.<br /><br /> 예를 들면 다음과 같습니다.\<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|Vsct 파일의 루트 요소입니다.|

## <a name="example"></a>예제

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>참고 항목
- [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
