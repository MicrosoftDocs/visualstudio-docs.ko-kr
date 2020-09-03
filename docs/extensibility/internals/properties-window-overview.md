---
title: 속성 창 개요 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 445a43cec976f363873c89dfe9b8e05429aebaf2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706025"
---
# <a name="properties-window-overview"></a>속성 창 개요
**속성** 창은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (통합 개발 환경)에서 사용할 수 있는 두 가지 주요 windows 형식에서 선택한 개체의 속성을 표시 하는 데 사용 됩니다. 이러한 두 가지 유형의 windows는 다음과 같습니다.

- 솔루션 탐색기, 클래스 뷰 및 개체 브라우저와 같은 도구 창

- 양식 디자이너, XML 편집기 및 HTML 편집기와 같은 편집기 및 디자이너를 포함 하는 문서 창

## <a name="using-the-properties-window"></a>속성 창 사용
 **속성** 창에는 단일 또는 여러 개의 선택 된 항목의 속성이 표시 됩니다. 여러 항목을 선택 하면 선택한 모든 개체에 대 한 모든 속성의 교집합이 표시 됩니다.

 COM + 메타 데이터를 사용 하 여 양식 디자인 창이 나 HTML 편집기에서 선택한 개체와 관련 된 이벤트는 **속성** 창에 표시 됩니다. 예를 들어 단추를 선택 하 고 `OnClick` 해당 단추에 연결할 수 있는 이벤트와 같은 관련 이벤트를 표시할 수 있습니다.

 **속성** 창에 표시 되는 이벤트는 주로 코드에 바인딩된 개체에 사용 됩니다. 코드와 관련 된 내용이 없는 파일 형식을 편집 하는 경우에는 이벤트가 발생 하지 않습니다. 실행 코드와 특정 개체에 연결 된 특정 이벤트 간에 바인딩이 있는 경우에만 이벤트를 **속성** 창에 표시할 수 있습니다. 이에 대 한 예는 해당 개체가 활성화 될 때 실행 되는 선택 된 개체의 코드 뒤에 있는 코드입니다.

 다음 표에서는 **속성** 창에서 사용 하는 기본 인터페이스를 보여 줍니다.

|인터페이스 이름|Description|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|**속성** 창에 범주 목록을 제공 하 고 각 속성을 범주에 매핑합니다.|
|[IDispatch 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|자동화를 지 원하는 프로그래밍 도구 및 기타 응용 프로그램에 개체의 메서드 및 속성을 노출 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|개체 자체에서 구현 하는 모달 대화 상자 창을 여는 *작성기* 라는 줄임표 (...) 단추를 제공 합니다. 사용자가 텍스트 필드에 값을 쉽게 입력 하지 않을 때 사용 됩니다. 예를 들어이 값을 사용 하 여 RGB 값을 결정 하는 색 선택기를 열 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|**속성** 창에 표시 된 정보를 업데이트 하는 데 사용 되는 개체에 대 한 액세스를 제공 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 는 표시 되는 관련 속성이 포함 된 선택 가능한 개체를 포함 하는 각 창에 대해 Vspackage에 의해 구현 됩니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|인터페이스의 메서드 및 구조체의 필드와 같은 개체의 형식에 대 한 정보를 제공 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Vspackage가 선택 이벤트에 대 한 알림을 받고 현재 프로젝트 계층, 항목, 요소 값 및 명령 UI 컨텍스트에 대 한 정보를 검색할 수 있도록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|여러 선택 항목에 대 한 액세스 권한을 환경에 제공 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|**속성** 창에 표시 되는 일부 속성의 지역화 된 이름을 제공 하는 데 사용 됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|현재 선택, 요소 값 또는 명령 UI 컨텍스트에 대해 등록 된 Vspackage 변경 내용을 알립니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|현재 선택 항목의 변경 내용을 환경에 알리고 새 선택 항목과 관련 된 계층 및 항목 정보에 대 한 액세스를 제공 합니다.|

 에 대 한 자세한 내용은 `IDispatch` MSDN library를 참조 하십시오.

## <a name="see-also"></a>추가 정보
- [속성 확장](../../extensibility/internals/extending-properties.md)
- [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md)
