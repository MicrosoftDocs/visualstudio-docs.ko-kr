---
title: 디자이너에 실행 취소 지원 제공 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6136caaec0cb8f0d79e3fb7b96245fc3fd070710
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675334"
---
# <a name="supplying-undo-support-to-designers"></a>디자이너에 실행 취소 지원 제공
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기와 같은 디자이너는 일반적으로 사용자가 코드 요소를 수정할 때 최근 변경 내용을 되돌릴 수 있도록 실행 취소 작업을 지원 해야 합니다.  
  
 Visual Studio에서 구현 된 대부분의 디자이너에는 환경에서 자동으로 제공 되는 실행 취소 지원이 있습니다.  
  
 실행 취소 기능에 대 한 지원을 제공 해야 하는 디자이너 구현:  
  
- 추상 기본 클래스를 구현 하 여 실행 취소 관리 제공 <xref:System.ComponentModel.Design.UndoEngine>  
  
- 및 클래스를 구현 하 여 지 속성 및 CodeDOM 지원을 제공 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> 합니다.  
  
  을 사용 하 여 디자이너를 작성 하는 방법에 대 한 자세한 내용은 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] [디자인 타임 지원 확장](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)을 참조 하세요.  
  
  는 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 다음을 수행 하 여 기본 실행 취소 인프라를 제공 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>및 클래스를 통해 실행 취소 관리 구현 제공 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>  
  
- 기본 <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> 및 구현을 통해 지 속성 및 CodeDOM 지원 <xref:System.ComponentModel.Design.IComponentChangeService> 제공  
  
## <a name="obtaining-undo-support-automatically"></a>실행 취소 지원 자동으로 가져오기  
 에서 만든 모든 디자이너는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 다음과 같은 경우 자동 및 전체 실행 취소를 지원 합니다.  
  
- <xref:System.Windows.Forms.Control>사용자 인터페이스에 대해 기반 클래스를 사용 합니다.  
  
- 코드 생성 및 지 속성을 위해 표준 CodeDOM 기반 코드 생성 및 구문 분석 시스템을 사용 합니다.  
  
     Visual Studio CodeDOM 지원 사용에 대 한 자세한 내용은 [동적 소스 코드 생성 및 컴파일](https://msdn.microsoft.com/library/d077a3e8-bd81-4bdf-b6a3-323857ea30fb) 을 참조 하세요.  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>명시적 디자이너 실행 취소 지원을 사용 하는 경우  
 디자이너는에서 제공 하는 것 외에는 뷰 어댑터 라고 하는 그래픽 사용자 인터페이스를 사용 하는 경우 자체 실행 취소 관리를 제공 해야 합니다 <xref:System.Windows.Forms.Control> .  
  
 이에 대 한 예로는 기반 그래픽 인터페이스가 아닌 웹 기반 그래픽 디자인 인터페이스를 사용 하 여 제품을 만들 수 있습니다 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .  
  
 이러한 경우를 사용 하 여이 뷰 어댑터를 등록 하 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> 고 명시적 실행 취소 관리를 제공 해야 합니다.  
  
 디자이너는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 이름 공간에 제공 된 코드 생성 모델을 사용 하지 않는 경우 CodeDOM 및 지 속성 지원을 제공 해야 <xref:System.CodeDom> 합니다.  
  
## <a name="undo-support-features-of-the-designer"></a>디자이너의 실행 취소 지원 기능  
 환경 SDK는 <xref:System.Windows.Forms.Control> 사용자 인터페이스 또는 표준 CodeDOM 및 지 속성 모델에 대 한 기반 클래스를 사용 하지 않는 디자이너에서 사용할 수 있는 실행 취소 지원을 제공 하는 데 필요한 기본 인터페이스 구현을 제공 합니다.  
  
 클래스는 클래스 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.ComponentModel.Design.UndoEngine> 의 구현을 사용 하 여 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> 실행 취소 작업을 관리 하는 클래스에서 파생 됩니다.  
  
 Visual Studio에서는 디자이너 실행 취소에 다음과 같은 기능을 제공 합니다.  
  
- 여러 디자이너에서 연결 된 실행 취소 기능  
  
- 디자이너 내의 자식 단위는 및을 구현 하 여 부모와 상호 작용할 수 있습니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .  
  
  환경 SDK는 다음을 제공 하 여 CodeDOM 및 지 속성 지원을 제공 합니다.  
  
- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> 의 구현으로 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
  <xref:System.ComponentModel.Design.IComponentChangeService> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ' ' 디자인 호스트에서 제공 하는입니다.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>환경 SDK 기능을 사용 하 여 실행 취소 지원 제공  
 실행 취소 지원을 얻으려면 디자이너를 구현 하는 개체는 다음을 수행 해야 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>올바른 구현을 사용 하 여 클래스의 인스턴스를 인스턴스화하고 초기화 <xref:System.IServiceProvider> 합니다.  
  
- 이 <xref:System.IServiceProvider> 클래스는 다음 서비스를 제공 해야 합니다.  
  
  - <xref:System.ComponentModel.Design.IDesignerHost>.  
  
  - <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
       CodeDOM serialization을 사용 하는 디자이너는의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> 구현으로 제공 된를 사용 하도록 선택할 수 있습니다 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
       이 경우 <xref:System.IServiceProvider> 생성자에 제공 된 클래스는 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 이 개체를 클래스의 구현으로 반환 해야 합니다 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .  
  
  - <xref:System.ComponentModel.Design.IComponentChangeService>  
  
       디자인 호스트에서 제공 하는 기본를 사용 하는 디자이너 <xref:System.ComponentModel.Design.DesignSurface> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에는 클래스의 기본 구현이 보장 됩니다 <xref:System.ComponentModel.Design.IComponentChangeService> .  
  
  기반 실행 취소 메커니즘을 구현 하는 디자이너는 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 다음과 같은 경우 변경 내용을 자동으로 추적 합니다.  
  
- 속성 변경은 개체를 통해 수행 됩니다 <xref:System.ComponentModel.TypeDescriptor> .  
  
- <xref:System.ComponentModel.Design.IComponentChangeService> 취소할 수 있는 변경 내용이 커밋될 때 이벤트는 수동으로 생성 됩니다.  
  
- 디자이너에 대 한 수정 내용이의 컨텍스트 내에서 만들어졌습니다 <xref:System.ComponentModel.Design.DesignerTransaction> .  
  
- 디자이너는 <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> 에서 파생 되 고 <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> 및의 구현을 제공 하는 Visual Studio 별 구현 또는의 구현에서 제공 하는 표준 실행 취소 단위를 사용 하 여 실행 취소 단위를 명시적으로 만들도록 선택 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .  
  
## <a name="see-also"></a>관련 항목  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [디자인 타임 지원 확장](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
