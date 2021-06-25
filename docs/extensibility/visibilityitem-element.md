---
title: VisibilityItem 요소 | Microsoft Docs
description: VisibilityItem 요소는 명령 및 도구 모음의 정적 표시 여부를 결정합니다. 항목은 명령 또는 메뉴와 연결된 명령 UI 컨텍스트를 식별합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 025e05dd0346c7da0a70985aa579d1673f2ffcaa
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905438"
---
# <a name="visibilityitem-element"></a>VisibilityItem 요소
`VisibilityItem`요소는 명령 및 도구 모음의 정적 표시 여부를 결정합니다. 모든 항목은 명령 또는 메뉴와 연결된 명령 UI 컨텍스트를 식별합니다. Visual Studio 명령, 메뉴 및 도구 모음과 해당 표시를 정의하는 VSPackage를 로드하지 않고 검색합니다. IDE는 메서드를 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 명령 UI 컨텍스트가 활성 상태인지 여부를 확인합니다.

 VSPackage가 로드된 후 Visual Studio 명령 표시 유형이 가 아닌 VSPackage에 의해 결정되어야 `VisibilityItem` 합니다. 명령의 표시 여부를 확인하려면 명령을 구현한 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 방법에 따라 이벤트 처리기 또는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드를 구현할 수 있습니다.

 연결된 컨텍스트가 활성 상태인 경우에만 요소가 있는 명령 또는 `VisibilityItem` 메뉴가 나타납니다. 각 명령 컨텍스트 조합에 대한 항목을 포함하여 단일 명령, 메뉴 또는 도구 모음을 하나 이상의 명령 UI 컨텍스트와 연결할 수 있습니다. 명령 또는 메뉴가 여러 명령 UI 컨텍스트와 연결된 경우 연결된 명령 UI 컨텍스트 중 하나가 활성 상태일 때 명령 또는 메뉴가 표시됩니다.

 `VisibilityItem`요소는 그룹에는 적용되지 않고 명령, 메뉴 및 도구 모음에만 적용됩니다. 관련 요소가 없는 요소는 `VisibilityItem` 부모 메뉴가 활성 상태일 때마다 표시됩니다.

## <a name="syntax"></a>구문

```xml
<VisibilityItem
  guid="cmdGuidMyProductCommands"
  id="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|guid|필수 요소. GUID/ID 명령 식별자의 GUID입니다.|
|id|필수 요소. GUID/ID 명령 식별자의 ID입니다.|
|컨텍스트|필수 요소. 명령이 표시되는 UI 컨텍스트입니다.|
|조건|선택 사항입니다. [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하세요.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[VisibilityConstraints 요소](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`요소는 명령 및 도구 모음 그룹의 정적 표시 여부를 결정합니다.|

## <a name="remarks"></a>설명
 표준 Visual Studio UI 컨텍스트는 및 클래스뿐만 아니라 *Visual Studio SDK 설치 경로*\VisualStudioIntegration\Common\Inc\vsshlids.h 파일에 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 정의됩니다. 보다 완전한 UI 컨텍스트 집합이 클래스에 정의되어 <xref:Microsoft.VisualStudio.VSConstants> 있습니다.

## <a name="example"></a>예제

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [VisibilityConstraints 요소](../extensibility/visibilityconstraints-element.md)
- [Visual Studio 명령 테이블(. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
