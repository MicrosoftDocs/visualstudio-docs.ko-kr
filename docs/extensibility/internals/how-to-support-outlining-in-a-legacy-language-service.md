---
title: '방법: 레거시 언어 서비스에서 개요 지원 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28396d513c83ed83e2769e75a6020a98b10251b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707912"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>방법: 레거시 언어 서비스에서 개요 지원
개요는 텍스트의 여러 영역을 확장 하거나 축소 하는 데 사용 됩니다. 개요를 사용 하는 방법은 언어 마다 다르게 정의할 수 있습니다. 자세한 내용은 [개요](../../ide/outlining.md)를 참조하세요.

 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 개요를 구현 하는 새로운 방법에 대해 자세히 알아보려면 [연습: 개요](../../extensibility/walkthrough-outlining.md)를 참조 하세요.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

 다음은 해당 언어 서비스에 대해이 명령을 지 원하는 방법을 보여 줍니다.

## <a name="to-support-outlining"></a>개요를 지원 하려면

1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>언어 서비스 개체에 대해를 구현 합니다.

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>현재 개요 세션 개체에 대해를 호출 하 여 새 개요 영역을 추가 합니다.

## <a name="robust-programming"></a>강력한 프로그래밍
 사용자가 **개요** 메뉴에서 **정의로 축소** 를 선택 하면 IDE는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> 언어 서비스에서를 호출 합니다.

 이 메서드가 호출 되 면 IDE는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 포인터 (텍스트 버퍼에 대 한 포인터) 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (현재 개요 세션에 대 한 포인터)를 전달 합니다.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>매개 변수에 이러한 영역을 지정 하 여 여러 개요 영역에 대해 메서드를 호출할 수 있습니다 `rgOutlnReg` . `rgOutlnReg`매개 변수는 <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> 구조체입니다. 이 프로세스를 통해 특정 지역이 확장 또는 축소 되는지 여부와 같은 숨겨진 영역의 다른 특성을 지정할 수 있습니다.

> [!NOTE]
> 줄 바꿈 문자를 숨길 때는 주의 해야 합니다. 숨겨진 텍스트는 최종 줄 바꿈 문자를 표시 하는 첫 번째 줄의 첫 번째 줄부터 마지막 줄의 마지막 문자로 확장 해야 합니다.

## <a name="see-also"></a>추가 정보
- [방법: 레거시 언어 서비스에서 숨겨진 텍스트 지원 제공](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [방법: 레거시 언어 서비스에서 확장 된 개요 지원 제공](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
