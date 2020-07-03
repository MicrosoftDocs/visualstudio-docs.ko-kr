---
title: 언어 서비스에서 개요 지원 제공 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 450ef1430e86467d116cc635a27600756bc36075
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905283"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>방법: 레거시 언어 서비스에서 확장 된 개요 지원 제공
**정의로 축소** 명령을 지 원하는 것 이상으로 언어에 대 한 개요 지원을 확장 하는 두 가지 옵션이 있습니다. 편집기에서 제어 하는 개요 영역을 추가 하 고 클라이언트 제어 개요 영역을 추가할 수 있습니다.

## <a name="adding-editor-controlled-outline-regions"></a>편집기에서 제어 하는 개요 영역 추가
 이 방법을 사용 하 여 개요 영역을 만든 다음, 해당 지역이 확장, 축소 등 인지 여부를 편집기에서 처리할 수 있습니다. 개요 지원을 제공 하기 위한 두 가지 옵션 중에서이 옵션은 가장 강력 하지 않습니다. 이 옵션의 경우를 사용 하 여 지정 된 텍스트 범위에 새 개요 영역을 만듭니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> . 이 영역을 만든 후 해당 동작은 편집기에 의해 제어 됩니다. 편집기에서 제어 하는 개요 영역을 구현 하려면 다음 절차를 따르십시오.

### <a name="to-implement-an-editor-controlled-outline-region"></a>편집기에서 제어 하는 개요 영역을 구현 하려면

1. `QueryService`에 대 한 호출<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     이는에 대 한 포인터를 반환 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> 합니다.

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>을 호출 하 여 지정 된 텍스트 버퍼에 대 한 포인터를 전달 합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>버퍼의 개체에 대 한 포인터를 반환 합니다.

3. 에 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 대 한 포인터에 대해를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> 합니다.

4. 를 호출 하 여 한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 번에 하나 이상의 새 개요 영역을 추가 합니다.

     이 메서드를 사용 하 여 윤곽선으로 지정할 텍스트의 범위, 기존 개요 영역을 제거 하거나 유지할지 여부 및 개요 영역을 기본적으로 확장 하거나 축소할지 여부를 지정할 수 있습니다.

## <a name="add-client-controlled-outline-regions"></a>클라이언트 제어 개요 영역 추가
 이 방법을 사용 하 여 및 언어 서비스에서 사용 하는 것과 같은 클라이언트 제어 (또는 스마트) 개요를 구현할 수 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 있습니다. 자체 개요를 관리 하는 언어 서비스는 오래 된 개요 영역을 제거 하 고 필요에 따라 새 개요 영역을 만들기 위해 텍스트 버퍼 내용을 모니터링 합니다.

### <a name="to-implement-a-client-controlled-outline-region"></a>클라이언트 제어 개요 영역을 구현 하려면

1. `QueryService`에 대해를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 합니다. 이는에 대 한 포인터를 반환 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> 합니다.

2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>을 호출 하 여 지정 된 텍스트 버퍼에 대 한 포인터를 전달 합니다. 이는 버퍼에 대 한 숨겨진 텍스트 세션이 이미 있는지 여부를 확인 합니다.

3. 텍스트 세션이 이미 있는 경우에는 만들 필요가 없으며 기존 개체에 대 한 포인터가 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 반환 됩니다. 이 포인터를 사용 하 여 개요 영역을 열거 하 고 만들 수 있습니다. 그렇지 않으면를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 하 여 버퍼에 대 한 숨겨진 텍스트 세션을 만듭니다. 개체에 대 한 포인터가 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 반환 됩니다.

    > [!NOTE]
    > 를 호출 하는 경우 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 숨겨진 텍스트 클라이언트 (개체)를 지정할 수 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> . 이 클라이언트는 숨겨진 텍스트 또는 개요 영역을 사용자가 확장 하거나 축소할 때 사용자에 게 알립니다.

4. Call <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> structure) 매개 변수: <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> 구조체의 멤버에 값을 지정 `iType` 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 숨겨진 지역이 아니라 개요 영역을 만드는 중임을 표시 합니다. 해당 지역이 구조 멤버에서 클라이언트 제어 또는 편집기 제어 인지 여부를 지정 `dwBehavior` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 합니다. 스마트 개요 구현은 편집기와 클라이언트에서 제어 하는 개요 영역을 혼합 하 여 포함할 수 있습니다. 구조 멤버에서 개요 영역이 축소 될 때 표시 되는 배너 텍스트 (예: "...")를 지정 합니다. `pszBanner` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 숨겨진 영역에 대 한 편집기의 기본 배너 텍스트는 "..."입니다.
