---
title: 레거시 언어 서비스에서 숨겨진 텍스트 지원 제공
description: 편집기에서 제어 하거나 클라이언트에서 제어 하는 숨겨진 텍스트 영역을 추가 하 여 레거시 언어 서비스에서 숨겨진 텍스트 지원을 제공 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2bb6d9c3c4f01c0e84c6ab437e352a86bf00448f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078736"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>방법: 레거시 언어 서비스에서 숨겨진 텍스트 지원 제공
개요 영역 외에도 숨겨진 텍스트 영역을 만들 수 있습니다. 숨겨진 텍스트 영역은 클라이언트 제어 또는 편집기에서 제어 될 수 있으며 텍스트 영역을 완전히 숨기는 데 사용 됩니다. 편집기는 숨겨진 영역을 가로 선으로 표시 합니다. 이에 대 한 예는 HTML 편집기의 **스크립트 전용** 뷰입니다.

## <a name="to-implement-a-hidden-text-region"></a>숨겨진 텍스트 영역을 구현 하려면

1. `QueryService`에 대해를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 합니다.

     이는에 대 한 포인터를 반환 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> 합니다.

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>을 호출 하 여 지정 된 텍스트 버퍼에 대 한 포인터를 전달 합니다. 이는 버퍼에 대 한 숨겨진 텍스트 세션이 이미 있는지 여부를 확인 합니다.

3. 하나는 이미 있는 경우 만들 필요가 없으며 기존 개체에 대 한 포인터가 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 반환 됩니다. 이 포인터를 사용 하 여 숨겨진 텍스트 영역을 열거 하 고 만듭니다. 그렇지 않으면를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 하 여 버퍼에 대 한 숨겨진 텍스트 세션을 만듭니다.

     개체에 대 한 포인터가 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 반환 됩니다.

    > [!NOTE]
    > 를 호출 하는 경우 `CreateHiddenTextSession` 숨겨진 텍스트 클라이언트를 지정할 수 있습니다 (즉, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> ). 숨겨진 텍스트 클라이언트는 숨겨진 텍스트 또는 개요를 사용자가 확장 하거나 축소할 때 사용자에 게 알립니다.

4. 을 호출 하 여 한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> 번에 하나 이상의 새 개요 영역을 추가 하 고 `reHidReg` ( <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> ) 매개 변수에서 다음 정보를 지정 합니다.

    1. `hrtConcealed`구조체의 멤버에 값을 지정 `iType` 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 윤곽선 영역이 아니라 숨겨진 영역을 만들고 있음을 표시 합니다.

        > [!NOTE]
        > 숨겨진 영역을 숨기면 편집기는 숨겨진 영역 주위에 줄을 자동으로 표시 하 여 현재 상태를 나타냅니다.

    2. 해당 지역이 구조 멤버에서 클라이언트 제어 또는 편집기 제어 인지 여부를 지정 `dwBehavior` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 합니다. 스마트 개요 구현은 편집기와 클라이언트에서 제어 하는 개요 및 숨겨진 텍스트 영역을 혼합 하 여 포함할 수 있습니다.
