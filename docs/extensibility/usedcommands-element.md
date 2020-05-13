---
title: 중고 명령 요소 | 마이크로 소프트 문서
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
ms.openlocfilehash: 76732b2a9700f1737af495098c8c23aa4b618819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698746"
---
# <a name="usedcommands-element"></a>UsedCommands 요소
UsedCommands 요소 그룹 UsedCommand 요소 및 기타 UsedCommands 그룹화.

 UsedCommands 요소는 선택 사항입니다. 패키지 외부에 정의된 명령을 호출하지 않으면 .vsct 파일에 이 섹션을 포함할 필요가 없습니다.

## <a name="syntax"></a>구문

```
<UsedCommands condition="Defined(DEBUG)">
  <UsedCommand ... />
</UsedCommands>
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
|[UsedCommand 요소](../extensibility/usedcommand-element.md)|다른 코드에서 구현되는 명령입니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[CommandTable 요소](../extensibility/commandtable-element.md)|VSPackage가 통합 개발 환경(IDE)에 제공하는 명령(예: 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자)을 나타내는 모든 요소를 정의합니다.|

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
