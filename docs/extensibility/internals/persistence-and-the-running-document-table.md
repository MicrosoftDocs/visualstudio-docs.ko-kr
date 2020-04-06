---
title: 지속성 및 실행 중인 문서 테이블 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba698f20b83d1a7af42aeca046aa2a8c943838ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706713"
---
# <a name="persistence-and-the-running-document-table"></a>지속성 및 실행 중인 문서 테이블
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE에서 프로젝트는 서비스를 사용하여 수행하는 프로젝트 항목의 지속성을 관리하는 데 전적으로 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>책임이 있습니다. 문서는 Visual Studio 환경에서 지속성의 기본 단위입니다. 프로젝트는 열려 있는 모든 문서의 상태를 추적하는 리소스인 RDT(실행 중인 문서 테이블)를 통해 문서의 열기, 저장 및 이름 바꾸기를 조정합니다.

## <a name="managing-persistence"></a>지속성 관리
 프로젝트는 인터페이스를 구현하여 환경의 지속성 서비스를 제어합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> 환경에서는 문서 자체를 유지하도록 직접 요청하지 않지만 소유 프로젝트(또는 계층 구조)에 문서를 저장하도록 요청합니다. 이렇게 하면 프로젝트가 프로젝트 항목 데이터를 로컬 파일, 원격 파일, 데이터베이스, 저장소 또는 기타 매체에 저장할 수 있습니다.

 글로벌 환경은 RDT를 유지합니다. 환경은 RDT의 열려 있는 모든 창 및 문서에 대한 항목을 유지 관리하므로 솔루션이 닫혀 있는 경우와 같은 특별한 알림을 받을 수 있습니다. 또한 RDT를 사용하면 환경이 **솔루션 탐색기**에서 해당 노드를 추적할 수 있습니다. RDT는 프로젝트 파일과 프로젝트 항목 문서를 포함하여 열려 있고 지속 가능한 개체당 하나의 레코드를 유지 관리합니다.

## <a name="see-also"></a>참조
- [문서 테이블 실행](../../extensibility/internals/running-document-table.md)
- [IDE의 선택 및 통화](../../extensibility/internals/selection-and-currency-in-the-ide.md)
