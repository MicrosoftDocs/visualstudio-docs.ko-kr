---
title: '방법: 레거시 언어 서비스의 개요 지원 | 마이크로 소프트 문서'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707912"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>방법: 레거시 언어 서비스의 개요 지원
개요는 텍스트의 다른 영역을 확장하거나 축소하는 데 사용됩니다. 개요가 사용되는 방식은 다른 언어에 따라 다르게 정의될 수 있습니다. 자세한 내용은 [개요](../../ide/outlining.md)를 참조하세요.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 개요를 구현하는 새로운 방법에 대한 자세한 내용은 [연습: 개요](../../extensibility/walkthrough-outlining.md)를 참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

 다음은 언어 서비스에 대해 이 명령을 지원하는 방법을 보여 줍니다.

## <a name="to-support-outlining"></a>개요를 지원하려면

1. 언어 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> 서비스 개체에 구현합니다.

2. 현재 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 개요 세션 개체를 호출하여 새 윤곽선 영역을 추가합니다.

## <a name="robust-programming"></a>강력한 프로그래밍
 사용자가 **개요** 메뉴에서 **정의에 축소를** 선택하면 IDE는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> 언어 서비스를 호출합니다.

 이 메서드가 호출되면 IDE는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 포인터(텍스트 버퍼에 대한 포인터)와 (현재 개요 세션에 대한 포인터)을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> 전달합니다.

 매개 변수에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 이러한 영역을 지정하여 여러 윤곽선 영역에 대한 메서드를 호출할 수 있습니다. `rgOutlnReg` 매개 `rgOutlnReg` 변수는 <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> 구조입니다. 이 프로세스를 사용하면 특정 영역이 확장또는 축소되는지 여부와 같이 숨겨진 영역의 다른 특성을 지정할 수 있습니다.

> [!NOTE]
> 줄 바호 문자를 숨길 때는 주의해야 합니다. 숨겨진 텍스트는 첫 번째 줄의 시작부분에서 섹션의 마지막 줄의 마지막 문자까지 확장되어 마지막 줄이 표시되어야 합니다.

## <a name="see-also"></a>참조
- [방법: 레거시 언어 서비스에 숨겨진 텍스트 지원 제공](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [방법: 레거시 언어 서비스에서 확장된 개요 지원 제공](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
