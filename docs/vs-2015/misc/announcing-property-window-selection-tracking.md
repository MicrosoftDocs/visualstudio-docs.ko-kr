---
title: 속성 창 선택 항목 추적 발표 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 6296993d3a1f5039024556f09b721daa82ca4f53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002445"
---
# <a name="announcing-property-window-selection-tracking"></a>속성 창 선택 영역 추적 발표
**속성 창이 나** **속성 페이지 (예: 속성을** 보려는 폼, 텍스트 또는 선택 항목)를 사용 하려면 선택 영역을 조정 하는 방법에 대 한 완전 한 지식이 있어야 합니다. 예를 들어 단일 선택 항목이 나 여러 항목을 선택 했는지 여부를 알고 있어야 합니다. 그런 다음 인터페이스를 사용 하 여 IDE에 선택 유형 (단일 또는 여러)을 발표 해야 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 합니다. 이 인터페이스는 **속성** 창에 필요한 정보를 제공 합니다.  
  
### <a name="to-announce-selection-to-the-environment"></a>선택 항목을 환경에 알리기  
  
1. `QueryInterface`에 대해를 호출 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 합니다.  
  
    1. 이렇게 하려면 보기를 만들 때 보기에 전달 된 사이트 포인터를 사용 합니다.  
  
    2. `QueryService`서비스의 뷰에서를 호출 `SID_STrackSelection` 합니다.  
  
         이는에 대 한 포인터를 반환 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 합니다.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>선택 항목이 변경 될 때마다 메서드를 호출 하 고를 구현 하는 개체에 대 한 포인터를 전달 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 합니다.  
  
     선택 컨테이너 개체는 단일 또는 여러 선택 항목을 사용할 수 있으며 개체에 선택 정보를 포함 합니다 `IDispatch` . 메서드를 호출 하면 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 선택이 변경 되었음을 **속성** 창에 알립니다. 그러면 **속성** 창에서 개체를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 단일 또는 다중 선택이 발생 했는지 여부와 실제 개체 선택 항목을 확인 합니다.  
  
     다중 선택을 지정 하는 경우 **속성** 창에서 개체에 대 한 공용 속성 간의 교차를 찾습니다. 단일 개체 선택 항목을 지정 하는 경우 **속성** 창에는 하나의 개체에 대 한 모든 속성이 표시 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [속성 확장](../extensibility/internals/extending-properties.md)   
 [속성 페이지](../extensibility/internals/property-pages.md)