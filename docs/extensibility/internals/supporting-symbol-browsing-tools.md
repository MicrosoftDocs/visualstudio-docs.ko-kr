---
title: 기호 검색 도구 지원 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbols, symbol-browsing tools
- browsers, symbol browsers
- symbol-browsing tools
- libraries
- IVsLibrary2 interface, symbol-browsing tools
- IVsSimpleLibrary2 interface, symbol-browsing tools
- symbol-browsing tools, library manager
- symbols
- libraries, symbol-browsing tools
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4998e47ccd6f99df2710833c18975d57e3bb92f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704776"
---
# <a name="supporting-symbol-browsing-tools"></a>기호 검색 도구 지원
**기호 결과** 도구 **개체 브라우저**, **클래스 뷰**, **호출 브라우저** 및 찾기 도구 Visual Studio에서 기호 검색 기능을 제공 합니다. 이러한 도구는 기호에 대 한 계층적 트리 뷰를 표시 하 고 트리에서 기호 간의 관계를 표시 합니다. 기호는 다양 한 구성 요소에 포함 된 네임 스페이스, 개체, 클래스, 클래스 멤버 및 기타 언어 요소를 나타낼 수 있습니다. 구성 요소에는 Visual Studio 프로젝트, 외부 .NET Framework 구성 요소 및 형식 (.tlb) 라이브러리가 포함 됩니다. 자세한 내용은 [코드 구조 보기](../../ide/viewing-the-structure-of-code.md)를 참조 하세요.

## <a name="symbol-browsing-libraries"></a>기호 검색 라이브러리
 언어 구현자는 구성 요소에서 기호를 추적 하는 라이브러리를 만들고 인터페이스 집합을 통해 Visual Studio 개체 관리자에 기호 목록을 제공 하 여 Visual Studio 기호 검색 기능을 확장할 수 있습니다. 라이브러리는 인터페이스를 통해 설명 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> . Visual Studio 개체 관리자는 라이브러리에서 데이터를 가져오고 구성 하 여 기호 검색 도구에서 새 데이터에 대 한 요청에 응답 합니다. 그런 다음 요청 된 데이터로 도구를 채우거 나 업데이트 합니다. Visual Studio 개체 관리자에 대 한 참조를 가져오려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> 서비스 ID를 `GetService` 메서드에 전달 합니다.

 각 라이브러리는 모든 라이브러리에 대 한 정보를 수집 하는 Visual Studio 개체 관리자를 사용 하 여 등록 해야 합니다. 라이브러리를 등록 하려면 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 합니다. Visual Studio 개체 관리자는 요청을 시작 하는 도구에 따라 적절 한 라이브러리를 찾고 데이터를 요청 합니다. 이 데이터는 인터페이스에서 설명 하는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 기호 목록에서 라이브러리와 개체 관리자 간에 이동 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]개체 관리자는 기호 검색 도구를 주기적으로 새로 고쳐 라이브러리에 포함 된 최신 데이터를 반영 하는 일을 담당 합니다.

 아래 다이어그램에는 라이브러리와 Visual Studio 개체 관리자 간 요청/데이터 교환 프로세스의 주요 요소에 대 한 샘플이 포함 되어 있습니다. 다이어그램의 인터페이스는 관리 코드 응용 프로그램의 일부입니다.

 ![라이브러리와 개체 관리자 간의 데이터 흐름](../../extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")

 Visual Studio 개체 관리자에 기호 목록을 제공 하려면 먼저 메서드를 호출 하 여 Visual Studio 개체 관리자에 라이브러리를 등록 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> . 라이브러리가 등록 된 후 Visual Studio 개체 관리자는 라이브러리의 기능에 대 한 특정 정보를 요청 합니다. 예를 들어 및 메서드를 호출 하 여 라이브러리 플래그와 지원 되는 범주를 요청 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> . 특정 시점에 도구 중 하나가이 라이브러리의 데이터를 요청 하는 경우 개체 관리자는 메서드를 호출 하 여 최상위 수준의 기호 목록을 요청 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> . 이에 대 한 응답으로 라이브러리는 기호 목록을 제조 하 고 인터페이스를 통해 Visual Studio 개체 관리자에 게 노출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]개체 관리자는 메서드를 호출 하 여 목록에 있는 항목 수를 결정 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> . 다음 요청은 모두 목록의 지정 된 항목과 관련 되며 각 요청에서 항목 인덱스 번호를 제공 합니다. Visual Studio 개체 관리자는 메서드를 호출 하 여 형식, 접근성 및 항목의 기타 속성에 대 한 정보를 수집 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> .

 메서드를 호출 하 여 항목의 이름을 결정 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> 하 고 메서드를 호출 하 여 아이콘 정보를 요청 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> . 아이콘은 항목 이름 왼쪽에 표시 되 고, 항목의 형식, 내게 필요한 옵션 및 기타 속성을 보여 줍니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]개체 관리자는 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> 하 여 지정 된 목록 항목이 확장 가능 하 고 자식 항목을 포함 하는지 여부를 확인 합니다. UI가 요소를 확장 하는 요청을 보내는 경우 개체 관리자는 메서드를 호출 하 여 기호에 대 한 자식 목록을 요청 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> . 이 프로세스는 트리의 각 부분에서 요청 시 빌드 될 때까지 계속 됩니다.

> [!NOTE]
> 네이티브 코드 기호 공급자를 구현 하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> 및 인터페이스를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> 합니다.

## <a name="see-also"></a>추가 정보
- [방법: 개체 관리자에 라이브러리 등록](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [방법: 라이브러리에서 제공하는 기호 목록을 개체 관리자에 노출](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [방법: 라이브러리의 기호 식별](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
