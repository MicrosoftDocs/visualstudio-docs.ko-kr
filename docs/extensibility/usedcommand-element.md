---
title: 중고 명령 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65030c3fe24c3456b0c4c99a667362d2a4c67703
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698833"
---
# <a name="usedcommand-element"></a>UsedCommand 요소
VSPackage가 다른 .vsct 파일에 정의된 명령에 액세스할 수 있도록 합니다. 예를 들어 VSPackage가 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 셸에 의해 정의된 표준 **복사** 명령을 사용하는 경우 다시 구현하지 않고 메뉴 또는 도구 모음에 명령을 추가할 수 있습니다.

## <a name="syntax"></a>구문

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|guid|필수 사항입니다. 명령을 식별하는 GUID ID 쌍의 GUID입니다.|
|id|필수 사항입니다. 명령을 식별하는 GUID ID 쌍의 ID입니다.|
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|None||

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[UsedCommands 요소](../extensibility/usedcommands-element.md)|그룹 usedCommand 요소 및 기타 UsedCommands 그룹화.|

## <a name="remarks"></a>설명
 `<UsedCommands>` 요소에 명령을 추가하면 VSPackage는 VSPackage에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 명령이 필요하다는 환경을 알립니다. 패키지에 필요한 `<UsedCommand>` 모든 명령에 대한 요소를 추가해야 하며, 이 요소는 Visual Studio의 모든 버전 및 구성에 포함되지 않을 수 있습니다. 예를 들어 패키지에서 Visual C++와 관련된 명령을 호출하는 경우 명령에 대한 `<UsedCommand>` 요소를 포함하지 않는 한 Visual Web Developer 사용자는 명령을 사용할 수 없습니다.

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
