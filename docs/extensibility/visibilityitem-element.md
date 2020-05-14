---
title: 가시성항목 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9129d64e430d661bbdd8f7682e64c93650570211
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698158"
---
# <a name="visibilityitem-element"></a>가시성항목 요소
요소는 `VisibilityItem` 명령 및 도구 모음의 정적 가시성을 결정합니다. 모든 항목은 명령 또는 메뉴와 연결된 명령 UI 컨텍스트를 식별합니다. Visual Studio는 명령, 메뉴 및 도구 모음을 정의하는 VSPackage를 로드하지 않고 명령, 메뉴 및 도구 모음 및 가시성을 검색합니다. IDE는 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 사용하여 명령 UI 컨텍스트가 활성 상태인지 여부를 확인합니다.

 VSPackage를 로드한 후 Visual Studio는 명령 가시성이 `VisibilityItem`가 아닌 VSPackage에 의해 결정될 것으로 예상합니다. 명령의 가시성을 확인하려면 명령을 구현한 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 방법에 따라 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 이벤트 처리기 또는 메서드를 구현할 수 있습니다.

 `VisibilityItem` 요소가 있는 명령또는 메뉴는 연결된 컨텍스트가 활성 상태일 때만 나타납니다. 각 명령 컨텍스트 조합에 대한 항목을 포함하여 하나 이상의 명령 UI 컨텍스트와 단일 명령, 메뉴 또는 도구 모음을 연결할 수 있습니다. 명령 또는 메뉴가 여러 명령 UI 컨텍스트와 연결되어 있으면 연결된 명령 UI 컨텍스트 중 하나가 활성 상태일 때 명령 또는 메뉴가 표시됩니다.

 이 `VisibilityItem` 요소는 그룹이 아닌 명령, 메뉴 및 도구 모음에만 적용됩니다. 관련 `VisibilityItem` 요소가 없는 요소는 부모 메뉴가 활성화될 때마다 표시됩니다.

## <a name="syntax"></a>구문

```xml
<VisibilityItem
  guid ="="cmdGuidMyProductCommands"
  id=="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|guid|필수 사항입니다. GUID/ID 명령 식별자의 GUID입니다.|
|id|필수 사항입니다. GUID/ID 명령 식별자의 ID입니다.|
|컨텍스트|필수 사항입니다. 명령이 표시되는 UI 컨텍스트입니다.|
|조건|(선택 사항) [조건부 특성을](../extensibility/vsct-xml-schema-conditional-attributes.md)참조하십시오.|

### <a name="child-elements"></a>자식 요소
 None

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[가시성 제약 요소](../extensibility/visibilityconstraints-element.md)|요소는 `VisibilityConstraints` 명령 및 도구 모음 그룹의 정적 가시성을 결정합니다.|

## <a name="remarks"></a>설명
 표준 Visual Studio UI 컨텍스트는 *Visual Studio SDK 설치 경로*\VisualStudioIntegration\Common\Inc\vsshlids.h <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> 파일뿐만 아니라 및 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 클래스에도 정의되어 있습니다. 보다 완전한 UI 컨텍스트 집합이 클래스에 <xref:Microsoft.VisualStudio.VSConstants> 정의되어 있습니다.

## <a name="example"></a>예제

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [가시성 제약 요소](../extensibility/visibilityconstraints-element.md)
- [비주얼 스튜디오 명령 테이블(. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
