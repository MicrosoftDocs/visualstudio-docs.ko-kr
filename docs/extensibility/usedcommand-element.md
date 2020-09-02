---
title: UsedCommand 요소 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698833"
---
# <a name="usedcommand-element"></a>UsedCommand 요소
VSPackage에서 다른. vsct 파일에 정의 된 명령에 액세스할 수 있습니다. 예를 들어 VSPackage에서 셸에서 정의한 표준 **복사** 명령을 사용 하는 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 명령을 다시 구현 하지 않고 메뉴 또는 도구 모음에 명령을 추가할 수 있습니다.

## <a name="syntax"></a>구문

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|guid|필수 요소. 명령을 식별 하는 GUID ID 쌍의 GUID입니다.|
|id|필수 요소. 명령을 식별 하는 GUID ID 쌍의 ID입니다.|
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|없음||

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[UsedCommands 요소](../extensibility/usedcommands-element.md)|UsedCommand 요소 및 기타 UsedCommands 그룹화를 그룹화 합니다.|

## <a name="remarks"></a>설명
 VSPackage는 요소에 명령을 추가 하 여 `<UsedCommands>` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage에 명령이 필요 함을 환경에 알립니다. `<UsedCommand>`패키지에 필요한 모든 명령에 요소를 추가 해야 합니다 .이는 Visual Studio의 모든 버전 및 구성에 포함 될 수 없습니다. 예를 들어 패키지에서 Visual C++와 관련 된 명령을 호출 하는 경우 명령 `<UsedCommand>` 에 대 한 요소를 포함 하지 않으면 Visual Web Developer 사용자가이 명령을 사용할 수 없습니다.

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
