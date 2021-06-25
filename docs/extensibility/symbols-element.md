---
title: Symbols 요소 | Microsoft Docs
description: Symbols 요소는 다른 VSCT 요소에서 사용되는GUID 및 ID를 정의합니다. 이 문서에는 예제가 포함되어 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b593f353714f2fbb6f5b726fa2bbc0da449043ea
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901736"
---
# <a name="symbols-element"></a>Symbols 요소
다른 VSCT 요소에서 사용하는GUID 및 ID를 정의합니다. 비 관리 코드의 경우 이 정보는 일반적으로 [Extern 요소](../extensibility/extern-element.md)에 지정된 헤더 파일에서 제공됩니다. 관리 코드는 Symbols 요소의 자식 요소를 사용하여 이 정보를 정의합니다.

 기존 .cto 파일에서 .vsct 파일을 만드는 경우 기호가 Symbols 요소의 자식으로 생성됩니다. 자세한 내용은 [방법: 만들기를 참조하세요. 기존 의 Vsct 파일입니다. Cto 파일.](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file)

 Symbols 요소는 전처리기에서 사용할 이름-값 쌍을 정의하는 [Define 요소](../extensibility/define-element.md)와 혼동해서는 안 됩니다.

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

|attribute|설명|
|---------------|-----------------|
|없음||

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|GuidSymbol|GUID 기호를 정의합니다. GuidSymbol에는 이름과 값의 두 가지 필수 특성이 있습니다. 이름은 기호의 이름이고 값은 문자열인 GUID의 값입니다.<br /><br /> 예를 들면 다음과 같습니다.\<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|
|IDSymbol|기호를 정의합니다. IDSymbol에는 이름과 값의 두 가지 필수 특성이 있습니다. 이름은 기호의 이름이고 값은 문자열로 기호의 값입니다.<br /><br /> 예를 들면 다음과 같습니다.\<IDSymbol name="MyMenuGroup" value="0x1020" />|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
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
