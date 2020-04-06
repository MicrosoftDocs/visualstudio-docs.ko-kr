---
title: 디자이너에게 수행 취소 지원 제공 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0580f974c362a71c3e400946f2ad34f565ad1232
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699670"
---
# <a name="supply-undo-support-to-designers"></a>디자이너에게 수행 취소 지원 제공

편집기와 같은 디자이너는 일반적으로 사용자가 코드 요소를 수정할 때 최근 변경 내용을 되돌릴 수 있도록 작업 취소 작업을 지원해야 합니다.

Visual Studio에서 구현된 대부분의 디자이너는 환경에서 자동으로 제공하는 "실행 취소" 지원을 제공합니다.

실행 취소 기능에 대한 지원을 제공해야 하는 디자이너 구현:

- 추상 기본 클래스를 구현하여 실행 취소 관리 제공<xref:System.ComponentModel.Design.UndoEngine>

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> 및 <xref:System.ComponentModel.Design.IComponentChangeService> 클래스를 구현하여 지속성 및 CodeDOM 지원을 제공합니다.

.NET Framework를 사용하는 작성 디자이너에 대한 자세한 내용은 [디자인 시간 지원 확장을](/previous-versions/37899azc(v=vs.140))참조하십시오.

는 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 다음과 같은 기본 취소 인프라를 제공합니다.

- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 및 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> 클래스를 통해 실행 취소 관리 구현을 제공합니다.

- 기본 <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> 및 <xref:System.ComponentModel.Design.IComponentChangeService> 구현을 통해 지속성 및 CodeDOM 지원을 제공합니다.

## <a name="obtain-undo-support-automatically"></a>취소 지원 자동 받기

Visual Studio에서 만든 모든 디자이너는 디자이너의 경우 자동 및 전체 취소 지원이 있습니다.

- 사용자 인터페이스에 <xref:System.Windows.Forms.Control> 기반 클래스를 사용합니다.

- 코드 생성 및 지속성을 위해 표준 CodeDOM 기반 코드 생성 및 구문 분석 시스템을 사용합니다.

   Visual Studio CodeDOM 지원 작업에 대한 자세한 내용은 [동적 소스 코드 생성 및 컴파일](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)을 참조하십시오.

## <a name="when-to-use-explicit-designer-undo-support"></a>명시적 디자이너 사용 취소 지원
 디자이너는 <xref:System.Windows.Forms.Control>에서 제공하는 응용 기능 이외의 보기 어댑터라고 하는 그래픽 사용자 인터페이스를 사용하는 경우 고유한 취소 관리를 제공해야 합니다.

 예를 들어 .NET Framework 기반 그래픽 인터페이스가 아닌 웹 기반 그래픽 디자인 인터페이스가 있는 제품을 만드는 것이 있을 수 있습니다.

 이러한 경우 을 사용하여 이 뷰 어댑터를 Visual <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>Studio에 등록하고 명시적 취소 관리를 제공해야 합니다.

 디자이너는 <xref:System.CodeDom> 이름 공간에 제공된 Visual Studio 코드 생성 모델을 사용하지 않는 경우 CodeDOM 및 지속성 지원을 제공해야 합니다.

## <a name="undo-support-features-of-the-designer"></a>디자이너의 지원 기능 취소
 환경 SDK는 사용자 인터페이스 또는 표준 CodeDOM 및 지속성 모델에 기반 <xref:System.Windows.Forms.Control> 클래스를 사용하지 않는 디자이너가 사용할 수 있는 실행 취소 지원을 제공하는 데 필요한 인터페이스의 기본 구현을 제공합니다.

 클래스는 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 실행 취소 작업을 <xref:System.ComponentModel.Design.UndoEngine> 관리하기 위해 클래스의 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> 구현을 사용하여 .NET Framework 클래스에서 파생됩니다.

 Visual Studio는 디자이너의 취소에 다음과 같은 기능을 제공합니다.

- 여러 디자이너에 걸쳐 연결 취소 기능.

- 디자이너 내의 자식 단위는 을 <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> 구현하고 에 구현하여 부모와 상호 작용할 수 있습니다. <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>

환경 SDK는 다음을 제공하여 CodeDOM 및 지속성 지원을 제공합니다.

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>의 구현으로<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- 비주얼 <xref:System.ComponentModel.Design.IComponentChangeService> 스튜디오 디자인 호스트가 제공합니다.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>환경 SDK 기능을 사용하여 수행 취소 지원 제공

실행 취소 지원을 얻으려면 디자이너를 구현하는 개체는 유효한 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> <xref:System.IServiceProvider> 구현을 사용하여 클래스의 인스턴스를 인스턴스화하고 초기화해야 합니다. 이 <xref:System.IServiceProvider> 클래스는 다음 서비스를 제공해야 합니다.

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Visual Studio CodeDOM 직렬화를 사용하는 <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> 디자이너는 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 을 구현하기 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>위해 제공된 을 사용하도록 선택할 수 있습니다.

   이 경우 <xref:System.IServiceProvider> <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 생성자에게 제공된 클래스는 이 개체를 <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> 클래스의 구현으로 반환해야 합니다.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Visual Studio <xref:System.ComponentModel.Design.DesignSurface> 디자인 호스트에서 제공하는 기본값을 사용하는 디자이너는 <xref:System.ComponentModel.Design.IComponentChangeService> 클래스의 기본 구현을 보장합니다.

기반 실행 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> 취소 메커니즘을 구현하는 디자이너는 다음과 같은 경우 변경 내용을 자동으로 추적합니다.

- 속성은 개체를 <xref:System.ComponentModel.TypeDescriptor> 통해 변경됩니다.

- <xref:System.ComponentModel.Design.IComponentChangeService>실행 취소할 수 없는 변경이 커밋될 때 이벤트가 수동으로 생성됩니다.

- 디자이너에 대한 수정은 <xref:System.ComponentModel.Design.DesignerTransaction>의 컨텍스트 내에서 만들어졌습니다.

- <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> 디자이너는 구현에서 제공하는 표준 실행 취소 단위 또는 Visual Studio 관련 구현을 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>사용하여 실행 취소 단위를 명시적으로 생성하도록 선택합니다. <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>

## <a name="see-also"></a>참조

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [설계 시간 지원 확장](/previous-versions/37899azc(v=vs.140))
