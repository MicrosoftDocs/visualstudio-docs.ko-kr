---
title: 사용자 지정 문서 저장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d41b075111797a12d68b4aa30c23e3cbacd8058a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843336"
---
# <a name="saving-a-custom-document"></a>사용자 지정 문서 저장
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

환경에서는 **저장**, 다른 **이름으로 저장**및 **모두 저장** 명령을 처리 합니다. 사용자가 **파일** 메뉴에서 **저장**, 다른 **이름으로 저장** **또는 모두 저장** 을 클릭 하거나 솔루션을 닫을 때 모두 저장을 클릭 하면 다음 프로세스가 발생 합니다.  
  
 ![고객 편집기 저장](../../extensibility/internals/media/private.gif "Private")  
사용자 지정 편집기에 대 한 저장, 다른 이름으로 저장 및 모든 명령 처리 저장  
  
 이 프로세스는 다음 단계에 자세히 설명 되어 있습니다.  
  
1. **저장** 및 다른 **이름으로 저장** 명령의 경우 환경에서는이 서비스를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 활성 문서 창을 확인 하 여 저장 해야 하는 항목을 확인 합니다. 활성 문서 창을 알고 있으면 환경에서 실행 중인 문서 테이블의 문서에 대 한 계층 포인터 및 항목 식별자 (itemID)를 찾습니다. 자세한 내용은 [문서 테이블 실행](../../extensibility/internals/running-document-table.md)을 참조 하세요.  
  
     모두 저장 명령의 경우 환경에서는 실행 중인 문서 테이블의 정보를 사용 하 여 저장할 모든 항목의 목록을 컴파일합니다.  
  
2. 솔루션은 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 호출을 받으면 선택 된 항목 집합을 반복 합니다. 즉, 서비스에서 제공 하는 여러 선택 항목을 반복 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> .  
  
3. 솔루션은 선택 영역의 각 항목에 대해 계층 포인터를 사용 하 여 메서드를 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 저장 메뉴 명령을 사용할지 여부를 결정 합니다. 하나 이상의 항목이 변경 된 경우 저장 명령이 사용 됩니다. 계층 구조에서 표준 편집기를 사용 하는 경우 계층은 메서드를 호출 하 여 더티 상태 쿼리를 편집기에 위임 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> .  
  
4. 변경 된 각 항목에 대해 솔루션은 계층 포인터를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 해당 계층에서 메서드를 호출 합니다.  
  
     사용자 지정 편집기의 경우 문서 데이터 개체와 프로젝트 간의 통신은 전용입니다. 따라서 이러한 두 개체 사이에 특별 한 지 속성 우려 사항이 처리 됩니다.  
  
    > [!NOTE]
    > 사용자 고유의 지 속성을 구현 하는 경우 메서드를 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> 시간을 절약 해야 합니다. 이 메서드는 파일을 저장 하는 것이 안전한 지 확인 합니다. 예를 들어 파일이 읽기 전용이 아닙니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)
