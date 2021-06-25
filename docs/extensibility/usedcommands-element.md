---
title: UsedCommands 요소 | Microsoft Docs
description: UsedCommands 요소는 UsedCommand 요소 및 기타 UsedCommands 그룹화 그룹을 그룹화합니다. UsedCommands 요소는 선택 사항입니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UsedCommands
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 5e000ee0-a919-46e9-9277-2a0659f1eb78
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 21233527c9fcfb97fd45a8eeed60c04927df8ba1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903036"
---
# <a name="usedcommands-element"></a>UsedCommands 요소
UsedCommands 요소는 UsedCommand 요소 및 기타 UsedCommands 그룹화 그룹을 그룹화합니다.

 UsedCommands 요소는 선택 사항입니다. 패키지 외부에 정의된 명령을 호출하지 않는 경우 .vsct 파일에 이 섹션을 포함할 필요가 없습니다.

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
|조건|선택 사항입니다. [조건부 특성 을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[UsedCommand 요소](../extensibility/usedcommand-element.md)|다른 코드에 의해 구현되는 명령입니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|VSPackage가 IDE(통합 개발 환경)에 제공하는 명령(예: 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자)을 나타내는 모든 요소를 정의합니다.|

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
