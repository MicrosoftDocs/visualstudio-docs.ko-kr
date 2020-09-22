---
title: 단순화 포함 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b8e1ac2fa17409ac3228f87eb71c99ce9e725521
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841375"
---
# <a name="simplified-embedding"></a>간단한 포함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

단순화 된 포함은 해당 문서 뷰 개체가 부모 (즉,의 자식) 인 경우 편집기에서 사용 하도록 설정 되며, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 인터페이스는 해당 창 명령을 처리 하기 위해 구현 됩니다. 단순화 된 포함 편집기는 활성 컨트롤을 호스트할 수 없습니다. 다음 그림에서는 간단한 포함 편집기를 만드는 데 사용 되는 개체를 보여 줍니다.  
  
 ![간단한 포함 편집기 그래픽](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor")  
포함이 단순화 된 편집기  
  
> [!NOTE]
> 이 그림의 개체 중에서 `CYourEditorFactory` 개체는 표준 파일 기반 편집기를 만드는 데 필요 합니다. 사용자 지정 편집기를 만드는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 편집기에 고유한 개인 지 속성 메커니즘이 있기 때문에를 구현할 필요가 없습니다. 그러나 사용자 지정이 아닌 편집기의 경우에는이 작업을 수행 해야 합니다.  
  
 단순화 된 포함 편집기를 만들기 위해 구현 된 모든 인터페이스는 개체에 포함 되어 `CYourEditorDocument` 있습니다. 그러나 문서 데이터의 여러 보기를 지원 하려면 다음 표에 나와 있는 것 처럼 인터페이스를 별개의 데이터로 분할 하 고 개체를 확인 합니다.  
  
|인터페이스|인터페이스 위치|기능|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|View|부모 창에 대 한 연결을 제공 합니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|View|명령을 처리 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|View|상태 표시줄 업데이트를 사용하도록 설정합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|View|**도구 상자** 항목을 사용 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|데이터|파일이 변경 될 때 알림을 보냅니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|데이터|파일 형식에 대해 다른 이름으로 저장 기능을 사용 하도록 설정 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|데이터|문서에 대해 지속성을 사용하도록 설정합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|데이터|파일 변경 이벤트 (예: 다시 로드 트리거)를 해제할 수 있습니다.|
