---
title: 레거시 API의 텍스트 버퍼 이벤트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82fa31ca435d0c850a4d9e75e927cff9613b046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186413"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>레거시 API의 텍스트 버퍼 이벤트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 버퍼 개체는 여러 상황에 응답할 수 있는 여러 이벤트를 내보냅니다.  
  
 레거시 API를 사용 하는 경우 텍스트 버퍼에 대 한 변경 알림을 수신 하기 위해 다음 인터페이스를 구현 해야 합니다. 텍스트 버퍼의 인터페이스를 사용 하 여 `IConnectionPointContainer` 버퍼의 줄 변경 알림을 수신 하는 인터페이스를 텍스트 버퍼에 노출 합니다. 자세한 내용은 [방법: 레거시 API를 사용 하 여 텍스트 버퍼 이벤트 등록](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)을 참조 하세요. 또는 인터페이스의 경우에는 `IVsTextStreamEvents` `IVsTextLinesEvents` 각각 1 차원 또는 2 차원 좌표에서 변경 내용이 반환 됩니다.  
  
## <a name="text-buffer-interfaces"></a>텍스트 버퍼 인터페이스  
 텍스트 버퍼 개체에서 구현 하는 인터페이스는 다음과 같습니다.  
  
|인터페이스|설명|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|복합 작업 (즉, 단일 실행 취소/다시 실행 단위로 그룹화 된 작업)을 만들 수 있도록 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|텍스트 버퍼에서 관리 되는 문서 데이터의 지 속성을 사용 하도록 설정 합니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|기본 서비스를 제공 합니다. 많은 클라이언트에서 사용 됩니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|2 차원 좌표를 사용 하 여 읽기 및 쓰기 기능을 제공 합니다. `IVsTextBuffer`에서 상속됩니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|버퍼의 텍스트에 대 한 빠른 스트림 지향 순차적 액세스를 제공 합니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|1 차원 좌표를 사용 하 여 읽기 및 쓰기 기능을 제공 합니다. `IVsTextBuffer`에서 상속됩니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|속성의 제네릭 컬렉션에 대 한 액세스를 제공 합니다. 가장 중요 한 속성은 버퍼의 이름 또는 모니커입니다. GUID를 만들어 키로 사용 하면이 인터페이스를 사용 하 여 버퍼에 고유한 임의 데이터를 저장할 수 있습니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|이벤트에 대 한 연결 지점이 지원 됩니다.|  
  
## <a name="text-buffer-event-interfaces"></a>텍스트 버퍼 이벤트 인터페이스  
 텍스트 버퍼 이벤트 알림에 대 한 인터페이스는 다음과 같습니다.  
  
|인터페이스|설명|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|새 언어 서비스가 텍스트 버퍼와 연결 된 경우 클라이언트에 알립니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|텍스트 버퍼가 초기화 되 고 텍스트 버퍼의 데이터가 변경 되 면 클라이언트에 게 알립니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|1 차원 좌표에서 기본 텍스트 버퍼에 대 한 변경 내용을 클라이언트에 알립니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|2 차원 좌표에서 기본 텍스트 버퍼에 대 한 변경 내용을 클라이언트에 알립니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|사용자 데이터에 대 한 변경 내용을 클라이언트에 알립니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|이벤트를 트리거하고 변경 된 텍스트 범위를 제공 하는 마지막 커밋 제스처를 클라이언트에 알립니다. `IVsPreliminaryTextChangeCommitEvents`인터페이스는 실행 취소 또는 다시 실행 명령에 대 한 응답으로 발생 하지 않습니다. 이벤트는 실행 취소 관리자가 있는 버퍼에 대해서만 발생 합니다. `IVsPreliminaryTextChangeCommitEvents` 는 다른 이벤트가 변경 내용을 커밋하기 전에 텍스트를 변경 하지 않도록 하기 위해 다른 이벤트 (예: 예쁜 목록) 이전에 발생 합니다. VSPackage 인터페이스 또는 인터페이스 중 하나만 모니터링 해야 합니다 `IVsPreliminaryTextChangeCommitEvents` `IVsFinalTextChangeCommitEvents` .|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|이벤트를 트리거하고 변경 된 텍스트 범위를 제공 하는 마지막 커밋 제스처를 클라이언트에 알립니다. `IVsFinalTextChangeCommitEvents`인터페이스는 실행 취소 또는 다시 실행 명령에 대 한 응답으로 발생 하지 않습니다. 이벤트는 실행 취소 관리자가 있는 버퍼에 대해서만 발생 합니다. `IVsFinalTextChangeCommitEvents` 는 편집을 완전히 제어 하는 언어 서비스 또는 기타 개체에만 사용 됩니다. VSPackage 인터페이스 또는 인터페이스 중 하나만 모니터링 해야 합니다 `IVsPreliminaryTextChangeCommitEvents` `IVsFinalTextChangeCommitEvents` .|  
  
## <a name="see-also"></a>관련 항목  
 [레거시 API를 사용 하 여 텍스트 버퍼에 액세스](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [방법: 레거시 API를 사용하여 텍스트 버퍼 이벤트에 등록](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
