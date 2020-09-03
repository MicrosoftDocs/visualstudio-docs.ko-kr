---
title: IntelliSense 호스팅 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c378aec6822a436de0d8fc2656fcac7be4149f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203902"
---
# <a name="intellisense-hosting"></a>IntelliSense 호스팅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서는 IntelliSense 호스팅을 사용할 수 있습니다. IntellSense 호스팅을 사용 하면 Visual Studio 텍스트 편집기에서 호스팅되지 않는 코드에 대해 IntelliSense를 제공할 수 있습니다.  
  
## <a name="intellisense-hosting-usage"></a>IntelliSense 호스팅 사용  
 Visual Studio에서 완성 집합과 텍스트 버퍼에 대 한 액세스 권한이 있는 모든 코드는 UI (사용자 인터페이스)의 어디에서 나 IntelliSense 창을 가져올 수 있습니다. 이에 대 한 몇 가지 예제 시나리오는 **조사식** 창 또는 중단점 속성 창의 조건 필드에서 완료 됩니다.  
  
### <a name="implementation-interfaces"></a>구현 인터페이스  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 IntelliSense 팝업 창을 호스트 하는 모든 UI 구성 요소는 인터페이스를 지원 해야 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> . 기본 핵심 편집기 텍스트 뷰에는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 현재 IntelliSense 기능을 유지 하기 위한 스톡 인터페이스 구현이 포함 되어 있습니다. 대부분의 경우 인터페이스의 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 인터페이스에 구현 된 항목의 하위 집합을 나타냅니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . 하위 집합에는 IntelliSense UI 처리, 캐럿 및 선택 조작 및 간단한 텍스트 대체 기능이 포함 됩니다. 또한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 인터페이스는 개별 intellisense "subject" 및 "context"를 사용 하 여 컨텍스트에 사용 되는 텍스트 버퍼에 직접 존재 하지 않는 주제에 대해 intellisense를 제공할 수 있도록 합니다.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>인터페이스 공급자는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> 클라이언트에서 지원 되는 IntelliSense 기능 유형을 확인할 수 있도록 메서드를 구현 해야 합니다.  
  
 [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md)에 정의 된 호스트 플래그는 아래에 요약 되어 있습니다.  
  
|IntelliSense 호스트 플래그|설명|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|이 플래그를 설정 하면 컨텍스트 버퍼가 읽기 전용이 고 편집이 제목 텍스트 내 에서만 발생 합니다.|  
|IHF_NOSEPERATESUBJECT|이 플래그를 설정 하면 별도의 IntelliSense 주체가 없음을 의미 합니다. 주체는 기존 IntelliSense 시스템에서와 같이 컨텍스트 버퍼에 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
|IHF_SINGLELINESUBJECT|이 플래그를 설정 하면 해당 주체가 **조사식** 창에서 한 줄의 편집과 같이 여러 줄을 사용할 수 없습니다.|  
|IHF_FORCECOMMITTOCONTEXT|이 플래그를 설정 하 고 컨텍스트 버퍼를 업데이트 해야 하는 경우 호스트는 컨텍스트 버퍼에 대 한 읽기 전용 플래그를 무시 하 고 편집 하 여 계속 진행할 수 있습니다.|  
|IHF_OVERTYPE|편집 (주체 또는 컨텍스트)은 겹쳐쓰기 모드에서 수행 해야 합니다.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost BeforeCompletorCommit 및 IVsIntellisenseHost AfterCompletorCommit  
 이러한 콜백 메서드는 전처리 및 후 처리를 사용 하기 위해 텍스트를 커밋하기 전과 후에 완료 창에서 호출 됩니다.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor>인터페이스는 IDE (통합 개발 환경)에서 사용 하는 표준 완성 창의 공동 만들 수 있는 버전입니다. 모든 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> 인터페이스는이 completor 인터페이스를 사용 하 여 IntelliSense를 신속 하 게 구현할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
