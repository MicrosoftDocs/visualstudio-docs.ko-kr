---
title: UsedCommands 요소 | Microsoft Docs
description: UsedCommands 요소는 UsedCommand 요소 및 기타 UsedCommands 그룹화를 그룹화 합니다. UsedCommands 요소는 선택 사항입니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbc48d305e287fcb77407fbbf5ba52888b25dca6
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715901"
---
# <a name="usedcommands-element"></a>UsedCommands 요소
UsedCommands 요소는 UsedCommand 요소 및 기타 UsedCommands 그룹화를 그룹화 합니다.

 UsedCommands 요소는 선택 사항입니다. 패키지 외부에 정의 된 명령을 호출 하지 않는 경우에는이 섹션을. vsct 파일에 포함 하지 않아도 됩니다.

## <a name="syntax"></a>구문

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[UsedCommand 요소](../extensibility/usedcommand-element.md)|다른 코드에 의해 구현 되는 명령입니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|VSPackage가 IDE (통합 개발 환경)에 제공 하는 명령 (예: 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자)을 나타내는 요소를 모두 정의 합니다.|

## <a name="example"></a>예제

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>참조
- [UsedCommand 요소](../extensibility/usedcommand-element.md)
- [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
