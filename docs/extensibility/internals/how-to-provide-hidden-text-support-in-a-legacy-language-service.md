---
title: 레거시 언어 서비스에서 숨겨진 텍스트 지원 제공
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9d5fe85932f87eb68b6b5a0f5868ebbf8f2b5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707922"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>방법: 레거시 언어 서비스에 숨겨진 텍스트 지원 제공
윤곽선 영역 외에 숨겨진 텍스트 영역을 만들 수 있습니다. 숨겨진 텍스트 영역은 클라이언트가 제어하거나 편집기로 제어할 수 있으며 텍스트 영역을 완전히 숨기는 데 사용됩니다. 편집기는 숨겨진 영역을 가로 선으로 표시합니다. 예를 들어 HTML 편집기의 **스크립트 전용** 보기입니다.

## <a name="to-implement-a-hidden-text-region"></a>숨겨진 텍스트 영역을 구현하려면

1. 을 `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>호출합니다.

     그러면 에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>대한 포인터가 반환됩니다.

2. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, 지정된 텍스트 버퍼에 대한 포인터전달. 이렇게 하면 버퍼에 대해 숨겨진 텍스트 세션이 이미 있는지 여부가 결정됩니다.

3. 이미 있는 경우 하나를 만들 필요가 없으며 기존 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 개체에 대한 포인터가 반환됩니다. 이 포인터를 사용하여 숨겨진 텍스트 영역을 등록하고 만듭니다. 그렇지 않으면 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 버퍼에 대한 숨겨진 텍스트 세션을 만들려면 호출합니다.

     개체에 대한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 포인터가 반환됩니다.

    > [!NOTE]
    > 호출할 `CreateHiddenTextSession`때 숨겨진 텍스트 클라이언트(즉, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>)를 지정할 수 있습니다. 숨겨진 텍스트 클라이언트는 사용자가 숨겨진 텍스트 또는 개요를 확장하거나 축소할 때 사용자에게 알려주습니다.

4. 호출을 호출하여 한 번에 하나 이상의 새 윤곽선 영역을<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>추가하고 () 매개 변수에 다음 정보를 지정합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> `reHidReg`

    1. 구조의 `hrtConcealed` `iType` 멤버에 값을 지정하여 윤곽선 영역이 아닌 숨겨진 영역을 작성하고 있음을 나타냅니다. <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>

        > [!NOTE]
        > 숨겨진 영역이 숨김되면 편집기는 숨겨진 영역 주위의 선을 자동으로 표시하여 해당 영역의 존재를 나타냅니다.

    2. 이 지역이 구조의 `dwBehavior` 멤버에서 클라이언트 제어 또는 편집기 제어인지 여부를 지정합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 스마트 개요 구현에는 편집기 및 클라이언트 제어 개요 및 숨겨진 텍스트 영역이 혼합되어 포함될 수 있습니다.
