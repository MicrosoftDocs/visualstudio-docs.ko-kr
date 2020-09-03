---
title: 레거시 언어 서비스의 문 완성 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704937"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>레거시 언어 서비스의 명령문 완성
문 완성은 언어 서비스에서 사용자가 핵심 편집기에서 입력을 시작한 언어 키워드나 요소를 완료 하는 데 도움이 되는 프로세스입니다. 이 항목에서는 문 완성이 작동 하는 방식과 언어 서비스에서이를 구현 하는 방법에 대해 설명 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 문 완성을 구현 하는 새로운 방법에 대해 자세히 알아보려면 [연습: 문 완성 표시](../../extensibility/walkthrough-displaying-statement-completion.md)를 참조 하세요.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="implementing-statement-completion"></a>문 완성 구현
 핵심 편집기에서 문 완성은 대화형으로 보다 쉽고 빠르게 코드를 작성할 수 있는 특수 한 UI를 활성화 합니다. 문 완성 기능을 사용 하면 필요에 따라 관련 개체 또는 클래스를 표시 하 여 특정 요소를 기억할 필요가 없도록 하거나 도움말 참조 항목에서 조회 해야 할 필요가 없습니다.

 문 완성을 구현 하려면 언어에 구문 분석 될 수 있는 문 완성 트리거가 있어야 합니다. 예를 들어 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 는 점 (.) 연산자를 사용 하 고는 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 화살표 (->) 연산자를 사용 합니다. 언어 서비스에서는 둘 이상의 트리거를 사용 하 여 문 완성을 시작할 수 있습니다. 이러한 트리거는 명령 필터에서 프로그래밍 됩니다.

## <a name="command-filters-and-triggers"></a>명령 필터 및 트리거
 명령 필터는 트리거 또는 트리거의 발생을 차단 합니다. 명령 필터를 뷰에 추가 하려면 인터페이스를 구현 하 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 고 메서드를 호출 하 여 뷰에 연결 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> . <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>문 완성, 오류 표식 및 메서드 팁과 같은 언어 서비스의 모든 측면에 동일한 명령 필터 ()를 사용할 수 있습니다. 자세한 내용은 [레거시 언어 서비스 명령 가로채기](../../extensibility/internals/intercepting-legacy-language-service-commands.md)를 참조 하세요.

 편집기에서 트리거를 입력 하는 경우 (특히 텍스트 버퍼) 언어 서비스는 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 합니다. 이렇게 하면 사용자가 문 완성 후보에서 선택할 수 있도록 편집기에서 UI를 표시 합니다. 이 메서드를 사용 하려면 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 및 플래그를 <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> 매개 변수로 구현 해야 합니다. 완료 항목 목록이 스크롤 목록 상자에 나타납니다. 사용자가 계속 해 서 입력 하면 목록 상자 내에서 선택한 항목이 가장 최근에 입력 한 문자와 가장 일치 하는 항목을 반영 하도록 업데이트 됩니다. 핵심 편집기는 문 완성을 위해 UI를 구현 하지만 언어 서비스는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 문에 대 한 후보 완료 항목 집합을 정의 하기 위해 인터페이스를 구현 해야 합니다.

## <a name="see-also"></a>추가 정보
- [레거시 언어 서비스 명령 가로채기](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
