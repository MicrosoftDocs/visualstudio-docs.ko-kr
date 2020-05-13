---
title: 사용자 지정 문서 저장 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f04d588b4becfa778407269849032ea8ec56fb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705610"
---
# <a name="saving-a-custom-document"></a>사용자 지정 문서 저장
환경은 **저장,** **로 저장**및 **모두 저장** 명령을 처리합니다. 사용자가 **파일** 메뉴에서 **저장**, **로 저장** **또는 모두 저장을** 클릭하거나 솔루션을 닫으면 모두 저장이 발생합니다.

 ![고객 편집기 저장](../../extensibility/internals/media/private.gif "Private") 사용자 지정 편집기의 모든 명령 처리, 저장, 현재 저장, 저장

 이 프로세스는 다음 단계에 자세히 설명되어 있습니다.

1. **Save** as 및 **Save** As 명령의 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 경우 환경은 서비스를 사용하여 활성 문서 창을 결정하므로 저장할 항목을 결정합니다. 활성 문서 창이 알려지면 환경은 실행 중인 문서 테이블에서 문서에 대한 계층 구조 포인터 및 항목 식별자(itemID)를 찾습니다. 자세한 내용은 [문서 테이블 실행](../../extensibility/internals/running-document-table.md)을 참조하십시오.

     모두 저장 명령의 경우 환경은 실행 중인 문서 테이블의 정보를 사용하여 저장할 모든 항목 목록을 컴파일합니다.

2. 솔루션이 호출을 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 받으면 선택한 항목 집합(즉, <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 서비스에서 노출되는 여러 선택)을 통해 이어놓습니다.

3. 선택 영역의 각 항목에서 솔루션은 계층 포인터를 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 메서드를 호출하여 메뉴 저장 명령을 사용하도록 설정할지 여부를 결정합니다. 하나 이상의 항목이 더러워지면 저장 명령이 활성화됩니다. 계층 구조가 표준 편집기를 사용하는 경우 계층 은 메서드를 호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> 편집기로 더티 상태를 쿼리하는 대리자를 위임합니다.

4. 더러워지는 각 선택된 항목에서 솔루션은 계층 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 포인터를 사용하여 적절한 계층에서 메서드를 호출합니다.

     사용자 지정 편집기의 경우 문서 데이터 개체와 프로젝트 간의 통신은 비공개입니다. 따라서 이러한 두 개체 간에 특수한 지속성 문제가 처리됩니다.

    > [!NOTE]
    > 사용자 고유의 지속성을 구현하는 경우 시간을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> 절약하기 위해 메서드를 호출해야 합니다. 이 메서드는 파일을 저장하는 것이 안전한지 확인합니다(예: 파일이 읽기 전용이 아님).

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)
