---
title: 기호 브라우징 도구 지원 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704776"
---
# <a name="supporting-symbol-browsing-tools"></a>기호 검색 도구 지원
**개체 브라우저,** **클래스 보기,** **호출 브라우저** 및 기호 **결과 찾기** 도구는 Visual Studio에서 기호 검색 기능을 제공합니다. 이러한 도구는 기호의 계층적 트리 뷰를 표시하고 트리의 기호 간의 관계를 표시합니다. 기호는 네임스페이스, 개체, 클래스, 클래스 멤버 및 다양한 구성 요소에 포함된 기타 언어 요소를 나타낼 수 있습니다. 구성 요소에는 Visual Studio 프로젝트, 외부 .NET Framework 구성 요소 및 형식(.tlb) 라이브러리가 포함됩니다. 자세한 내용은 [코드 구조 보기를](../../ide/viewing-the-structure-of-code.md)참조하십시오.

## <a name="symbol-browsing-libraries"></a>기호 브라우징 라이브러리
 언어 구현자는 구성 요소의 기호를 추적하고 인터페이스 집합을 통해 Visual Studio 개체 관리자에 기호 목록을 제공하는 라이브러리를 만들어 Visual Studio 심볼 브라우징 기능을 확장할 수 있습니다. 라이브러리는 인터페이스에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> 의해 설명됩니다. Visual Studio 개체 관리자는 라이브러리에서 데이터를 가져오고 구성하여 기호 검색 도구의 새 데이터에 대한 요청에 응답합니다. 이후에 요청된 데이터로 도구를 채우거나 업데이트합니다. Visual Studio 개체 관리자에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>대한 참조를 <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> 얻으려면 서비스 `GetService` ID를 메서드에 전달합니다.

 각 라이브러리는 모든 라이브러리에 대한 정보를 수집하는 Visual Studio 개체 관리자에 등록해야 합니다. 라이브러리를 등록하려면 메서드를 호출합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 요청을 시작하는 도구에 따라 Visual Studio 개체 관리자는 적절한 라이브러리를 찾아 데이터를 요청합니다. 데이터는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 인터페이스에서 설명하는 기호 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 목록에서 라이브러리와 개체 관리자 간에 이동합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 개체 관리자는 라이브러리에 포함된 최신 데이터를 반영하도록 심볼 검색 도구를 주기적으로 새로 고치는 것을 담당합니다.

 아래 다이어그램에는 라이브러리와 Visual Studio 개체 관리자 간의 요청/데이터 교환 프로세스의 주요 요소 샘플이 포함되어 있습니다. 다이어그램의 인터페이스는 관리 되는 코드 응용 프로그램의 일부입니다.

 ![라이브러리와 개체 관리자 간의 데이터 흐름](../../extensibility/internals/media/callbrowserdiagram.gif "콜브라우저다이어그램")

 Visual Studio 개체 관리자에 기호 목록을 제공하려면 먼저 메서드를 호출하여 Visual Studio 개체 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> 관리자에 라이브러리를 등록해야 합니다. 라이브러리를 등록한 후 Visual Studio 개체 관리자는 라이브러리 기능에 대한 특정 정보를 요청합니다. 예를 들어, 라이브러리 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> 플래그 및 메서드를 호출 하 여 지원 되는 범주를 요청 합니다. 도구 중 하나가 이 라이브러리에서 데이터를 요청하면 개체 관리자는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> 메서드를 호출하여 최상위 수준의 기호 목록을 요청합니다. 이에 대한 응답으로 라이브러리는 기호 목록을 제조하고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> 인터페이스를 통해 Visual Studio 개체 관리자에 노출합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 개체 관리자는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> 메서드를 호출하여 목록에 있는 항목 수를 결정합니다. 다음 의 모든 요청은 목록의 지정된 항목과 관련이 있으며 각 요청의 항목 인덱스 번호를 공급합니다. Visual Studio 개체 관리자는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> 메서드를 호출하여 항목의 형식, 접근성 및 기타 속성에 대한 정보를 수집합니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> 메서드를 호출하여 항목의 이름을 결정하고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> 메서드를 호출하여 아이콘 정보를 요청합니다. 아이콘은 항목 이름의 왼쪽에 표시되며 항목의 유형, 접근성 및 기타 속성을 표시합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 개체 관리자는 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> 호출하여 지정된 목록 항목을 확장할 수 있고 자식 항목이 있는지 확인합니다. UI가 요소를 확장하기 위한 요청을 보내는 경우 개체 관리자는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> 메서드를 호출하여 자식 기호 목록을 요청합니다. 이 프로세스는 필요에 따라 빌드되는 트리의 다른 부분으로 계속됩니다.

> [!NOTE]
> 네이티브 코드 기호 공급자를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> 구현하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> 및 인터페이스를 사용합니다.

## <a name="see-also"></a>참조
- [방법: 개체 관리자에 라이브러리 등록](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [방법: 라이브러리에서 제공하는 기호 목록을 개체 관리자에 노출](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
- [방법: 라이브러리의 기호 식별](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)
