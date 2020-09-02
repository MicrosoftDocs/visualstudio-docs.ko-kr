---
title: 현재 위치의 활성화 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
caps.latest.revision: 26
manager: jillfra
ms.openlocfilehash: 192274d087731f68cb7e01c1da20e80cbfef0360
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802930"
---
# <a name="in-place-activation"></a>내부 활성화
편집기 뷰에서 ActiveX 또는 기타 활성 컨트롤을 호스트하는 경우 바로 활성화 모델을 사용하여 ActiveX 컨트롤 또는 활성 문서 데이터 개체로 편집기 뷰를 구현해야 합니다.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>메뉴, 도구 모음 및 명령 지원  
 Visual Studio를 통해 편집기 뷰에서 IDE의 메뉴 및 도구 모음을 사용할 수 있습니다. 이러한 확장을 *OLE 내부 구성 요소*라고 합니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>를 참조하세요.  
  
 ActiveX 컨트롤을 구현하는 경우 다른 포함 개체를 호스트할 수 있습니다. 문서 데이터 개체를 구현하는 경우 창 프레임이 ActiveX 컨트롤을 사용하는 기능을 제한합니다.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> 및 <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> 인터페이스를 사용하여 데이터와 뷰를 분리할 수 있습니다. 그러나 Visual Studio는 이 기능을 지원하지 않으며, 이러한 인터페이스는 문서 뷰 개체를 나타내는 데만 사용됩니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 서비스를 사용하는 편집기는 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> 서비스에서 구현된 <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 인터페이스의 메서드를 호출하여 메뉴, 도구 모음 및 명령을 통합할 수 있습니다. 편집기는 선택 추적 및 실행 취소 관리와 같은 다른 Visual Studio 기능도 제공할 수 있습니다. 자세한 내용은 [사용자 지정 편집기 및 디자이너 만들기](../extensibility/creating-custom-editors-and-designers.md)를 참조 하세요.  
  
## <a name="objects-and-interfaces-used"></a>사용되는 개체 및 인터페이스  
 바로 활성화를 만드는 데 사용되는 개체는 다음 그림에 나와 있습니다.  
  
 ![&#45;환경 활성화 편집기에서](../misc/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
바로 활성화 편집기  
  
> [!NOTE]
> 이 그림의 개체 중에서 `CYourEditorFactory` 개체만 표준 편집기를 만드는 데 필요합니다. 사용자 지정 편집기를 만드는 경우 대체로 편집기에 자체 전용 지속성 메커니즘이 있기 때문에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 를 구현할 필요가 없습니다. 자세한 내용은 [사용자 지정 편집기 및 디자이너 만들기](../extensibility/creating-custom-editors-and-designers.md)를 참조 하세요.  
  
 바로 활성화 편집기를 만들기 위해 구현되는 모든 인터페이스가 단일 `CYourEditorDocument` 개체에 표시되지만 이 구성에서는 문서 데이터의 단일 보기만 지원합니다. 문서 데이터의 여러 보기를 지원하는 방법에 대한 자세한 내용은 [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md)을 참조하세요.  
  
|인터페이스|개체 유형|기능|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|보기|<xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> 서비스를 사용하여 내부 VSPackage 개체가 완전히 통합된 IDE 구성 요소로 작동할 수 있게 합니다. 이 서비스는 개체의 메뉴, 도구 모음 및 명령을 IDE에 통합하고 상태 변경 알림을 실행합니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|보기|포함 개체가 컨테이너에 기본 기능을 제공하고 통신하는 주요 수단입니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|보기|내부 개체의 활성화 및 비활성화를 관리하고 표시할 내부 개체 크기를 결정합니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|보기|내부 개체, 연결된 애플리케이션의 가장 바깥쪽 프레임 창 및 포함 개체를 포함하는 애플리케이션의 문서 창 간에 직접 통신 채널을 제공합니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|보기|ActiveX 개체를 구현합니다. 문서 데이터 및 보기를 분리하는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> 및 `T:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView` 의 메서드는 IDE에서 사용되지 않습니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|보기/데이터|문서 데이터 개체, 문서 보기 개체 또는 둘 다가 명령 처리에 참여할 수 있게 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|보기|상태 표시줄 업데이트를 사용하도록 설정합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|보기|도구 상자에 항목을 추가할 수 있게 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|데이터|편집된 파일에 대한 변경 알림을 보냅니다. 이 인터페이스는 선택 사항입니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|데이터|파일 형식에 대해 다른 이름으로 저장 기능을 사용할 수 있도록 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|데이터|문서에 대해 지속성을 사용하도록 설정합니다. 읽기 전용 파일의 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> 를 호출하여 읽기 전용 파일을 나타내는 "잠금" 아이콘을 제공합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|데이터|문서 데이터의 변경 내용을 무시할지 여부를 결정합니다.|