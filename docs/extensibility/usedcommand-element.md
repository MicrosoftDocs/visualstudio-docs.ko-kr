---
title: UsedCommand 요소 | Microsoft Docs
description: UsedCommand 요소를 사용하면 VSPackage가 다른 .vsct 파일에 정의된 명령에 액세스할 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9d120353b9d6191bfcaae38151eb970ab1071b99
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903049"
---
# <a name="usedcommand-element"></a>UsedCommand 요소
VSPackage가 다른 .vsct 파일에 정의된 명령에 액세스할 수 있도록 합니다. 예를 들어 VSPackage가 셸에서 정의한 표준 **복사** 명령을 사용하는 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 명령을 다시 구현하지 않고 메뉴 또는 도구 모음에 추가할 수 있습니다.

## <a name="syntax"></a>구문

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|guid|필수 요소. 명령을 식별하는 GUID ID 쌍의 GUID입니다.|
|id|필수 요소. 명령을 식별하는 GUID ID 쌍의 ID입니다.|
|조건|선택 사항입니다. [조건부 특성 을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|None||

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[UsedCommands 요소](../extensibility/usedcommands-element.md)|UsedCommand 요소 및 기타 UsedCommands 그룹화 그룹화|

## <a name="remarks"></a>설명
 `<UsedCommands>`VSPackage는 요소에 명령을 추가하여 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage에 명령이 필요하다는 것을 환경에 알릴 수 있습니다. 패키지에 필요한 모든 명령에 대한 요소를 추가해야 합니다. `<UsedCommand>` 이 요소는 Visual Studio 모든 버전 및 구성에 포함되지 않을 수 있습니다. 예를 들어 패키지에서 Visual C++ 특정 명령을 호출하는 경우 명령에 대한 요소를 포함하지 않는 한 Visual Web Developer 사용자가 명령을 사용할 수 `<UsedCommand>` 없습니다.

## <a name="example"></a>예제

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>참조
- [UsedCommands 요소](../extensibility/usedcommands-element.md)
- [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
