---
title: 지 속성 및 실행 중인 문서 테이블 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c422ad1735312c82c8dc027c4adf73c1b033685
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196090"
---
# <a name="persistence-and-the-running-document-table"></a>지속성 및 실행 중인 문서 테이블
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE에서 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 프로젝트는 서비스를 사용 하 여 수행 하는 프로젝트 항목의 지 속성을 완전히 관리 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> 합니다. 문서는 Visual Studio 환경에서 지 속성의 기본 단위입니다. 프로젝트는 열려 있는 모든 문서의 상태를 추적 하는 리소스인 RT (실행 문서 테이블)를 사용 하 여 문서 열기, 저장 및 이름 바꾸기를 조정 합니다.  
  
## <a name="managing-persistence"></a>지 속성 관리  
 프로젝트는 인터페이스를 구현 하 여 환경의 지 속성 서비스를 제어 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> . 환경에서는 문서를 직접 유지 하도록 요청 하는 대신 소유 하는 프로젝트 (또는 계층)에 문서를 저장 하 라는 메시지를 표시 합니다. 이렇게 하면 프로젝트에서 프로젝트 항목 데이터를 로컬 파일, 원격 파일, 데이터베이스, 리포지토리 또는 기타 미디어에 저장할 수 있습니다.  
  
 전역 환경에서는 RDT를 유지 관리 합니다. 환경에서는 RDT에서 열려 있는 모든 창 및 문서에 대 한 항목을 유지 관리 하 여 솔루션이 닫힌 경우와 같은 특수 알림을 받을 수 있습니다. 또한 RDT를 사용 하면 환경에서 **솔루션 탐색기**의 해당 노드를 추적할 수 있습니다. RDT는 프로젝트 파일 및 프로젝트 항목 문서를 포함 하 여 열려 있는 지속 개체 마다 하나의 레코드를 유지 관리 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [문서 테이블 실행](../../extensibility/internals/running-document-table.md)   
 [IDE의 선택 및 통화](../../extensibility/internals/selection-and-currency-in-the-ide.md)
