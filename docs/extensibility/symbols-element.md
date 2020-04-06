---
title: 기호 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c24c3f84df23a07b6b16272b66b29e32ad7b911
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699343"
---
# <a name="symbols-element"></a>Symbols 요소
다른 VSCT 요소에서 사용되는 GUID 및 GUID를 정의합니다. 관리되지 않는 코드의 경우 이 정보는 일반적으로 [Extern Element](../extensibility/extern-element.md). 관리 되는 코드는 이 정보를 정의 하기 위해 기호 요소의 자식 요소를 사용 합니다.

 기존 .cto 파일에서 .vsct 파일을 만들면 기호 요소가 자식으로 생성됩니다. 자세한 내용은 를 만드는 [방법을 참조하십시오. 기존 . Cto 파일](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 기호 요소는 전처리기에서 사용할 이름 값 쌍을 정의하는 [정의 요소와](../extensibility/define-element.md)혼동해서는 안 됩니다.

## <a name="syntax"></a>구문

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|None||

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|가이드 심볼|GUID 기호를 정의합니다. GuidSymbol에는 이름과 값이라는 두 가지 필수 속성이 있습니다. 이름은 기호의 이름이며 값은 GUID의 문자열값입니다.<br /><br /> 예:\<GuidSymbol 이름="guidVsPackage1Pkg" 값="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|ID 기호|기호를 정의합니다. IDSymbol에는 이름과 값이라는 두 가지 필수 특성이 있습니다. 이름은 기호의 이름이며 값은 문자열로 기호의 값입니다.<br /><br /> 예:\<ID 기호 이름="MyMenuGroup" 값="0x1020" />|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|.vsct 파일의 루트 요소입니다.|

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

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
