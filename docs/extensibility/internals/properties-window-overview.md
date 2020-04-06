---
title: 속성 창 개요 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706025"
---
# <a name="properties-window-overview"></a>속성 창 개요
**속성** 창은 통합 개발 환경(IDE)에서 사용할 수 있는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 두 가지 주요 유형의 창에서 선택한 개체에 대한 속성을 표시하는 데 사용됩니다. 이러한 두 가지 유형의 창은 다음과 같습니다.

- 솔루션 탐색기, 클래스 뷰 및 개체 브라우저와 같은 도구 창

- 양식 디자이너, XML 편집기 및 HTML 편집기와 같은 편집기 및 디자이너가 포함된 문서 창

## <a name="using-the-properties-window"></a>속성 창 사용
 **속성** 창에는 선택한 단일 또는 여러 항목의 속성이 표시됩니다. 여러 항목을 선택하면 선택한 모든 객체에 대한 모든 속성의 교차점이 표시됩니다.

 COM+ 메타데이터를 사용하는 양식 디자인 창 또는 HTML 편집기 내에서 선택한 개체와 관련된 이벤트가 **속성** 창에 표시됩니다. 예를 들어 단추를 선택하고 해당 단추에 연결할 수 `OnClick` 있는 이벤트와 같은 관련 이벤트를 표시할 수 있습니다.

 **속성** 창에 표시되는 이벤트는 주로 코드에 바인딩된 개체와 함께 사용됩니다. 코드와 아무 관련이 없는 파일 형식을 편집하는 경우 이벤트가 발생하지 않습니다. 이벤트는 실행 중인 코드와 특정 개체와 연결된 특정 이벤트 사이에 바인딩이 있는 경우에만 **속성** 창에 표시됩니다. 이 예제는 해당 개체가 활성화될 때 실행되는 선택한 개체 뒤에 있는 코드입니다.

 다음 표에는 **속성** 창에서 사용하는 기본 인터페이스가 나열되어 있습니다.

|인터페이스 이름|설명|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|**속성** 창에 범주 목록을 제공하고 각 속성을 범주에 매핑합니다.|
|[IDispatch 인터페이스](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|개체의 메서드 및 속성을 자동화를 지원하는 프로그래밍 도구 및 기타 응용 프로그램에 노출합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|개체 자체에 의해 구현 된 모달 대화 상자 창을 여는 *빌더라는* 타원 (...) 단추를 제공합니다. 텍스트 필드에 사용자가 값을 쉽게 입력할 수 없는 경우에 사용됩니다. 예를 들어 RGB 값을 결정하는 색상 선택기를 여는 데 사용할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|**속성** 창에 표시되는 정보를 업데이트하는 데 사용되는 개체에 대한 액세스를 제공합니다. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>표시할 관련 속성이 있는 선택 가능한 개체가 포함된 각 창에 대해 VSPackages에 의해 구현됩니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|인터페이스의 메서드 및 구조의 필드와 같은 개체 의 형식에 대 한 정보를 제공 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|VSPackage가 선택 이벤트에 대한 알림을 수신하고 현재 프로젝트 계층 구조, 항목, 요소 값 및 명령 UI 컨텍스트에 대한 정보를 검색할 수 있도록 합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|환경에 여러 선택 항목에 대한 액세스 권한을 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|**속성** 창에 표시되는 일부 속성에 지역화된 이름을 제공하는 데 사용됩니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|현재 선택, 요소 값 또는 명령 UI 컨텍스트에 대한 등록된 VSPackage변경 사항을 인지합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|현재 선택 영역의 변경 환경을 통보하고 새 선택 영역과 관련된 계층 구조 및 항목 정보에 대한 액세스를 제공합니다.|

 자세한 `IDispatch`내용은 MSDN 라이브러리를 참조하십시오.

## <a name="see-also"></a>참조
- [속성 확장](../../extensibility/internals/extending-properties.md)
- [속성 창 필드 및 인터페이스](../../extensibility/internals/properties-window-fields-and-interfaces.md)
