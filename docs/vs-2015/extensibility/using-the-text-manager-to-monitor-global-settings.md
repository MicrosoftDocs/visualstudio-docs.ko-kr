---
title: 텍스트 관리자를 사용 하 여 전역 설정 모니터링 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - monitor global settings
- editors [Visual Studio SDK], legacy - text manager
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ece51450b8344ae4715a912399ec538171a26a5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695464"
---
# <a name="using-the-text-manager-to-monitor-global-settings"></a>텍스트 관리자를 사용하여 글로벌 설정 모니터링
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

핵심 편집기를 구현 하는 경우 이러한 변경 내용이 편집기의 인스턴스에 영향을 줄 수 있으므로 전역 설정에 대 한 변경 내용을 모니터링 해야 합니다. 텍스트 관리자에 의해 발생 한 이벤트를 수신 하 여 변경 내용을 추적할 수 있습니다. 예를 들어, 핵심 편집기에서 구성 요소의 모양이 나 동작에 대 한 전역 기본 설정을 지정 하는 경우 (예: 해당 문서 데이터 개체) 텍스트 관리자는이 정보를 저장 하 고 영향을 받는 모든 클라이언트에 전달 합니다.  
  
## <a name="text-manager-functions"></a>텍스트 관리자 함수  
 텍스트 관리자는 다음을 포함 하 여 여러 설정에 대 한 이벤트를 발생 시킵니다.  
  
- 버퍼가 소스 코드 제어 아래에 있는지 여부  
  
- 파일 변경 알림을 등록 하는 방법  
  
- 특정 버퍼와 연결 된 뷰를 추적 하는 방법  
  
- 텍스트 색 지정 기본 설정  
  
- 탭 및 공간 기본 설정 비교  
  
  지정 된 언어에 고유한 기본 설정은 텍스트 관리자에서 관리 되지 않습니다. 이러한 설정은 각 언어 서비스에서 관리 해야 합니다.  
  
  텍스트 관리자에 대 한 이벤트 알림은 인터페이스에 의해 제공 됩니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> . 텍스트 관리자에서 발생 하는 이벤트를 처리 하기 위해 클라이언트 개체에서이 인터페이스를 구현 합니다. 텍스트 관리자에서 인터페이스를 사용 하 여 이러한 이벤트에 등록 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [핵심 편집기 내부](../extensibility/inside-the-core-editor.md)   
 [편집기 기능](https://msdn.microsoft.com/bdac940d-1f14-4019-a01f-fd0bb3dc7198)
