---
title: 표준 문서 저장 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8d50a9e62e69f925564717020a51f88620f5f3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705545"
---
# <a name="saving-a-standard-document"></a>표준 문서 저장
환경은 저장, 현재 저장 및 저장 명령을 처리합니다. 사용자가 **파일** 메뉴에서 **모두** 저장 , **'로** **저장'을**선택하거나 솔루션을 닫으면 **모두 저장이**발생합니다.

 ![표준 편집기](../../extensibility/internals/media/public.gif "Public") 표준 편집기의 모든 명령 처리저장, 현재 저장 및 저장

 이 프로세스는 다음 단계에 자세히 설명되어 있습니다.

1. **로스** **로** 저장 명령을 선택하면 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 서비스를 사용하여 활성 문서 창을 결정하므로 저장할 항목을 결정합니다. 활성 문서 창이 알려지면 환경은 실행 중인 문서 테이블에서 문서에 대한 계층 구조 포인터 및 항목 식별자(itemID)를 찾습니다. 자세한 내용은 [문서 테이블 실행](../../extensibility/internals/running-document-table.md)을 참조하십시오.

    모두 **저장** 명령을 선택하면 환경은 실행 중인 문서 테이블의 정보를 사용하여 저장할 모든 항목 목록을 컴파일합니다.

2. 솔루션이 호출을 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 받으면 선택한 항목 집합(즉, <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 서비스에서 노출되는 여러 선택)을 통해 이어놓습니다.

3. 선택 영역의 각 항목에서 솔루션은 계층 포인터를 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> 메서드를 호출하여 메뉴 **저장** 명령을 사용하도록 설정할지 여부를 결정합니다. 하나 이상의 항목이 더러워지면 **저장** 명령이 활성화됩니다. 계층 구조가 표준 편집기를 사용하는 경우 계층 은 메서드를 호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> 편집기로 더티 상태를 쿼리하는 대리자를 위임합니다.

4. 더러워지는 각 선택된 항목에서 솔루션은 계층 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 포인터를 사용하여 적절한 계층에서 메서드를 호출합니다.

    계층 구조에서 표준 편집기를 사용하여 문서를 편집하는 것이 일반적입니다. 이 경우 해당 편집기의 문서 데이터 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 개체는 인터페이스를 지원해야 합니다. 메서드 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> 받으면 프로젝트는 문서 데이터 개체의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> 메서드를 호출하여 문서가 저장되고 있음을 편집자에게 알려야 합니다. 편집기를 사용하면 인터페이스를 호출하여 `Query Service` 환경이 다른 대화 상자 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> **저장상자를** 처리할 수 있습니다. 그러면 인터페이스에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 대한 포인터가 반환됩니다. 그런 다음 편집기는 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> 호출하여 매개 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 변수를 사용하여 `pPersistFile` 편집기의 구현에 포인터를 전달해야 합니다. 그런 다음 환경은 저장 작업을 수행하고 편집기의 다른 대화 상자 **저장** 상자를 제공합니다. 그런 다음 환경은 을 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>사용하여 편집기로 다시 호출합니다.

5. 사용자가 제목없는 문서 (즉, 이전에 저장되지 않은 문서)를 저장하려고하면 As로 저장 명령이 실제로 수행됩니다.

6. As로 저장 명령의 경우 환경은 사용자에게 파일 이름을 묻는 메시지를 표시하는 대화 상자로 저장합니다.

    파일 이름이 변경된 경우 계층 구조는 VSFPROPID_MkDocument 호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A>문서 프레임의 캐시된 정보를 업데이트해야 합니다.

   As **저장** 명령이 문서의 위치를 이동하고 계층 구조가 문서 위치에 중요한 경우 계층 구조는 열린 문서 창의 소유권을 다른 계층으로 넘겨줄 책임이 있습니다. 예를 들어, 프로젝트가 프로젝트가 프로젝트와 관련하여 내부 파일또는 외부 파일(기타 파일)인지 를 추적하는 경우 발생합니다. 다음 절차를 사용하여 파일의 소유권을 기타 파일 프로젝트로 변경합니다.

## <a name="changing-file-ownership"></a>파일 소유권 변경

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>파일 소유권을 기타 파일 프로젝트로 변경하려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> 인터페이스에 대한 쿼리 서비스입니다.

     에 대한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> 포인터가 반환됩니다.

2. 을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> 호출하는 ",`pszMkDocumentNew`") `punkWindowFrame`방법" 메서드를 호출하여 문서를 새 계층구조로 전송합니다. Save As 명령을 수행하는 계층구조는 이 메서드를 호출합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [프로젝트 항목 열기 및 저장](../../extensibility/internals/opening-and-saving-project-items.md)
