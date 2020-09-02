---
title: VisibilityItem 요소 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698158"
---
# <a name="visibilityitem-element"></a>VisibilityItem 요소
`VisibilityItem`요소는 명령 및 도구 모음의 정적 표시 여부를 결정 합니다. 모든 항목은 명령 또는 메뉴와 연결 된 명령 UI 컨텍스트를 식별 합니다. Visual Studio에서는 해당 항목을 정의 하는 Vspackage를 로드 하지 않고 명령, 메뉴 및 도구 모음과 표시 유형을 검색 합니다. IDE는 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 명령 UI 컨텍스트가 활성 상태 인지 여부를 확인 합니다.

 VSPackage를 로드 한 후에는 Visual Studio에서 대신 VSPackage에 의해 명령 표시 유형이 결정 됩니다 `VisibilityItem` . 명령의 표시 유형을 확인 하려면 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 명령을 구현한 방법에 따라 이벤트 처리기 또는 메서드를 구현할 수 있습니다.

 요소를 포함 하는 명령 또는 메뉴는 `VisibilityItem` 연결 된 컨텍스트가 활성 상태인 경우에만 표시 됩니다. 각 명령 컨텍스트 조합에 대 한 항목을 포함 하 여 단일 명령, 메뉴 또는 도구 모음에 하나 이상의 명령 UI 컨텍스트를 연결할 수 있습니다. 명령 또는 메뉴가 여러 명령 UI 컨텍스트와 연결 된 경우 연결 된 명령 UI 컨텍스트 중 하나가 활성화 되어 있으면 명령이 나 메뉴가 표시 됩니다.

 `VisibilityItem`요소는 그룹에만 적용 되는 것이 아니라 명령, 메뉴 및 도구 모음에만 적용 됩니다. 관련 요소가 없는 요소는 `VisibilityItem` 부모 메뉴가 활성화 될 때마다 표시 됩니다.

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

|특성|설명|
|---------------|-----------------|
|guid|필수 요소. GUID/ID 명령 식별자의 GUID입니다.|
|id|필수 요소. GUID/ID 명령 식별자의 ID입니다.|
|컨텍스트|필수 요소. 명령이 표시 되는 UI 컨텍스트입니다.|
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[VisibilityConstraints 요소](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`요소는 명령 및 도구 모음 그룹의 정적 표시 여부를 결정 합니다.|

## <a name="remarks"></a>설명
 표준 Visual Studio UI 컨텍스트는 및 클래스 뿐만 아니라 *Visual STUDIO SDK 설치 경로*\VisualStudioIntegration\Common\Inc\vsshlids.h 파일에도 정의 되어 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 있습니다. 보다 완전 한 UI 컨텍스트 집합은 클래스에 정의 되어 <xref:Microsoft.VisualStudio.VSConstants> 있습니다.

## <a name="example"></a>예제

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>참고 항목
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [VisibilityConstraints 요소](../extensibility/visibilityconstraints-element.md)
- [Visual Studio 명령 테이블 (. Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
