---
title: 언어 서비스에서 개요 지원 제공 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 37deafa92477289a2124ecee101dd254e68ef01d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707964"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>방법: 레거시 언어 서비스에서 확장된 개요 지원 제공
정의축소 명령을 지원하는 것 외에도 언어에 대한 개요 지원을 확장하는 두 가지 옵션이 **있습니다.** 편집기 제어 개요 영역을 추가하고 클라이언트 제어 개요 영역을 추가할 수 있습니다.

## <a name="adding-editor-controlled-outline-regions"></a>편집기 제어 개요 영역 추가
 이 방법을 사용하여 윤곽선 영역을 만든 다음 편집기에서 영역이 확장, 축소되는지 여부를 처리하는 등의 작업을 할 수 있습니다. 개요 지원을 제공하기 위한 두 가지 옵션 중 이 옵션은 가장 강력하지 않습니다. 이 옵션의 경우 을 사용하여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>지정된 텍스트 범위 에 대해 새 윤곽선 영역을 만듭니다. 이 영역을 만든 후 해당 동작은 편집기에서 제어합니다. 다음 절차를 사용하여 편집기 제어 개요 영역을 구현합니다.

### <a name="to-implement-an-editor-controlled-outline-region"></a>편집기 제어 개요 영역을 구현하려면

1. 전화 `QueryService` 걸기<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     그러면 에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>대한 포인터가 반환됩니다.

2. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, 지정된 텍스트 버퍼에 대한 포인터전달. 이렇게 하면 버퍼에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 대 한 개체에 대 한 포인터가 반환 됩니다.

3. 에 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 대한 포인터를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>호출합니다.

4. 한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 번에 하나 이상의 새 윤곽선 영역을 추가하려면 호출합니다.

     이 방법을 사용하면 윤곽선에 텍스트 범위를 지정할 수 있으며, 기존 윤곽선 영역이 제거또는 보존되는지 여부 및 윤곽선 영역이 기본적으로 확장 또는 축소되는지 여부를 지정할 수 있습니다.

## <a name="add-client-controlled-outline-regions"></a>클라이언트 제어 개요 영역 추가
 이 방법을 사용하여 클라이언트 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 제어(또는 스마트) 및 언어 서비스에서 사용하는 것과 같은 개요를 구현합니다. 자체 개요를 관리하는 언어 서비스는 텍스트 버퍼 내용을 모니터링하여 유효하지 않을 때 이전 윤곽선 영역을 삭제하고 필요에 따라 새 윤곽선 영역을 만듭니다.

### <a name="to-implement-a-client-controlled-outline-region"></a>클라이언트 제어 개요 영역을 구현하려면

1. 을 `QueryService` <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>호출합니다. 그러면 에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>대한 포인터가 반환됩니다.

2. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, 지정된 텍스트 버퍼에 대한 포인터전달. 이렇게 하면 버퍼에 대해 숨겨진 텍스트 세션이 이미 있는지 여부가 결정됩니다.

3. 텍스트 세션이 이미 있는 경우 텍스트 세션을 만들 필요가 없으며 기존 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 개체에 대한 포인터가 반환됩니다. 이 포인터를 사용하여 윤곽선 영역을 열거하고 만듭니다. 그렇지 않으면 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 버퍼에 대한 숨겨진 텍스트 세션을 만들려면 호출합니다. 개체에 대한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 포인터가 반환됩니다.

    > [!NOTE]
    > 호출할 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>때 숨겨진 텍스트 클라이언트(즉, 개체)를 지정할 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient> 수 있습니다. 이 클라이언트는 사용자가 숨겨진 텍스트 또는 윤곽선 영역을 확장하거나 축소할 때 이를 사용자에게 보올합니다.

4. 구조 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> 호출) 매개변수: <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 구조의 `iType` 멤버에 값을 지정하여 숨겨진 영역이 아닌 윤곽선 영역을 작성하고 있음을 나타냅니다. 이 지역이 구조의 `dwBehavior` 멤버에서 클라이언트 제어 또는 편집기 제어인지 여부를 지정합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 스마트 개요 구현에는 편집기 및 클라이언트 제어 개요 영역이 혼합되어 포함될 수 있습니다. <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 구조의 `pszBanner` 구성원에서 "..."와 같이 윤곽선 영역이 축소될 때 표시되는 배너 텍스트를 지정합니다. 숨겨진 영역에 대한 편집자의 기본 배너 텍스트는 "..."입니다.
