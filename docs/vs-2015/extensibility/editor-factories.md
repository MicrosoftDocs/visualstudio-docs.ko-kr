---
title: 편집기 팩터리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2de1fc8440bd33a526da62dbb4c7937800484aaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197757"
---
# <a name="editor-factories"></a>편집기 팩터리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

편집기 팩터리는 편집기 개체를 만들고이를 물리적 뷰 라고 하는 창 프레임에 배치 합니다. 편집기 및 디자이너를 만드는 데 필요한 문서 데이터와 문서 뷰 개체를 만듭니다. Visual Studio 핵심 편집기와 표준 편집기를 만들려면 편집기 팩터리가 필요 합니다. 편집기 팩터리를 사용 하 여 사용자 지정 편집기를 선택적으로 만들 수도 있습니다.  
  
 인터페이스를 구현 하 여 편집기 팩터리를 만듭니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> . 다음 예제에서는를 구현 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 편집기 팩터리를 만드는 방법을 보여 줍니다.  
  
 [!code-csharp[VSSDKEditorFactories#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkeditorfactories/cs/vssdkeditorfactoriespackage.cs#1)]
 [!code-vb[VSSDKEditorFactories#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkeditorfactories/vb/vssdkeditorfactoriespackage.vb#1)]  
  
 편집기는 처음으로 해당 편집기에서 처리 한 파일 형식을 열 때 로드 됩니다. 특정 편집기나 기본 편집기 중 하나를 열도록 선택할 수 있습니다. 기본 편집기를 선택 하는 경우 IDE (통합 개발 환경)에서 올바른 편집기를 확인 한 다음 엽니다. 자세한 내용은 [프로젝트에서 파일을 여는 편집기 확인](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)을 참조 하세요.  
  
## <a name="registering-editor-factories"></a>편집기 팩터리 등록  
 만든 편집기를 사용 하려면 먼저 처리할 수 있는 파일 확장명을 포함 하 여 해당 편집기에 대 한 정보를 등록 해야 합니다.  
  
 VSPackage이 관리 코드로 작성 된 경우 MPF (Managed Package Framework) 메서드를 사용 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> 하 여 VSPackage가 로드 된 후 편집기 팩터리를 등록할 수 있습니다. VSPackage이 비관리 코드로 작성 된 경우 서비스를 사용 하 여 편집기 팩터리를 등록 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> .  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>관리 코드를 사용 하 여 편집기 팩터리 등록  
 VSPackage의 메서드에 편집기 팩터리를 등록 해야 합니다 `Initialize` . 먼저 `base.Initialize` 를 호출한 다음 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> 각 편집기 팩터리에 대해를 호출 합니다.  
  
 관리 코드에서는 VSPackage가이를 처리 하므로 편집기 팩터리의 등록을 취소할 필요가 없습니다. 또한 편집기 팩터리가를 구현 하는 경우 <xref:System.IDisposable> 등록이 취소 되 면 자동으로 삭제 됩니다.  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>비관리 코드를 사용 하 여 편집기 팩터리 등록  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>편집기 패키지에 대 한 구현에서 메서드를 사용 `QueryService` 하 여를 호출 `SVsRegisterEditors` 합니다. 이렇게 하면에 대 한 포인터가 반환 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> 됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>인터페이스의 구현을 전달 하 여 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> . 별도의 클래스에 m 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> .  
  
## <a name="the-editor-factory-registration-process"></a>편집기 팩터리 등록 프로세스  
 다음 프로세스는 Visual Studio에서 편집기 팩터리를 사용 하 여 편집기를 로드할 때 발생 합니다.  
  
1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]프로젝트 시스템에서를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 합니다.  
  
2. 이 메서드는 편집기 팩터리를 반환 합니다. 그러나 Visual Studio는 프로젝트 시스템에 실제로 편집기가 필요할 때까지 편집기의 패키지 로드를 지연 시킵니다.  
  
3. 프로젝트 시스템에 편집기가 필요한 경우 Visual Studio는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 문서 뷰와 문서 데이터 개체를 모두 반환 하는 특수 메서드인를 호출 합니다.  
  
4. 를 사용 하 여 Visual Studio에서 편집기 팩터리에 대 한 호출을 통해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 문서 데이터 개체와 문서 뷰 개체를 모두 반환 하는 경우, Visual studio는 문서 창을 만들고 문서 뷰 개체를 배치한 다음 문서 데이터 개체에 대 한 RDT (실행 중인 문서 테이블)에 항목을 만듭니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [문서 테이블 실행](../extensibility/internals/running-document-table.md)
