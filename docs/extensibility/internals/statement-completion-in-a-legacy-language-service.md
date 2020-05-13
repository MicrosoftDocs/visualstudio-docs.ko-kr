---
title: 레거시 언어 서비스의 성명서 완료 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbeb360cf5bc0f74d6b2d9b93086382dd35da988
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704937"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>레거시 언어 서비스의 명령문 완성
명령문 완성은 언어 서비스를 통해 사용자가 핵심 편집기에서 입력하기 시작한 언어 키워드 또는 요소를 완료하는 데 도움이 되는 프로세스입니다. 이 항목에서는 명령문 완성의 작동 방식과 언어 서비스에서 문 완성을 구현하는 방법에 대해 설명합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 명령문 완료를 구현하는 새로운 방법에 대한 자세한 내용은 [연습: 명령문 완료 표시](../../extensibility/walkthrough-displaying-statement-completion.md)를 참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

## <a name="implementing-statement-completion"></a>구현 문 완료
 핵심 편집기에서 문 완성은 대화형으로 코드를 보다 쉽고 빠르게 작성하는 데 도움이 되는 특수 UI를 활성화합니다. 명령문 완성은 필요한 경우 관련 개체 또는 클래스를 표시하여 특정 요소를 기억하거나 도움말 참조 항목에서 찾을 필요가 없도록 하는 데 도움이 됩니다.

 문 완성을 구현하려면 언어에 구문 분석할 수 있는 문 완료 트리거가 있어야 합니다. 예를 들어 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 점(.) 연산자는 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 화살표(->) 연산자입니다. 언어 서비스는 두 개 이상의 트리거를 사용하여 명령문 완료를 시작할 수 있습니다. 이러한 트리거는 명령 필터에 프로그래밍됩니다.

## <a name="command-filters-and-triggers"></a>명령 필터 및 트리거
 명령 필터는 트리거 또는 트리거의 발생을 가로채는 것입니다. 뷰에 명령 필터를 추가하려면 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 구현하고 메서드를 호출하여 뷰에 연결합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 명령 완료, 오류 마커<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>및 메서드 팁과 같은 언어 서비스의 모든 측면에 대해 동일한 명령 필터 () 를 사용할 수 있습니다. 자세한 내용은 [레거시 언어 서비스 명령 가로채기 를](../../extensibility/internals/intercepting-legacy-language-service-commands.md)참조하십시오.

 트리거가 편집기에 입력되면(특히 텍스트 버퍼) 언어 서비스가 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 호출합니다. 이렇게 하면 편집기에서 UI를 불러오므로 사용자가 문 완료 후보에서 선택할 수 있습니다. 이 메서드를 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 하 <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> 고 매개 변수로 플래그를 사용 해야 합니다. 완료 항목 목록이 스크롤 목록 상자에 나타납니다. 사용자가 계속 입력하면 목록 상자 내의 선택 영역이 가장 최근에 입력된 문자와 가장 일치하는 일치 항목을 반영하도록 업데이트됩니다. 핵심 편집기는 명령문 완료를 위해 UI를 구현하지만 언어 서비스는 명령문에 대한 후보 완료 항목 집합을 정의하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 인터페이스를 구현해야 합니다.

## <a name="see-also"></a>참조
- [레거시 언어 서비스 명령 가로채기](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
