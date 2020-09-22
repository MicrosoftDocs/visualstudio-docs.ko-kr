---
title: '방법: 텍스트 표식 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 25c3c4f3a3d9a253b9ec671892d0d44ccf9ca3ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841683"
---
# <a name="how-to-use-text-markers"></a>방법: 텍스트 표식 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 표식을 적용 하 여 개체를 편집할 수 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
## <a name="procedures"></a>프로시저  
  
#### <a name="to-apply-text-markers"></a>텍스트 표식을 적용 하려면  
  
1. 클래스의 인스턴스를 가져옵니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> .  
  
    > [!NOTE]
    > 핵심 편집기는 편집 중인 모든 문서에 표준 텍스트 표식을 자동으로 적용 하며 표준 텍스트 표식을 명시적으로 적용할 필요가 없습니다.  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>작업할 텍스트 표식의를 사용 하 여 메서드를 호출 하 여 원하는 표식의 표식 유형 ID를 가져옵니다 `GUID` .  
  
    > [!NOTE]
    > `GUID`텍스트 표식을 제공 하는 서비스 또는 VSPackage의를 사용 하지 마십시오.  
  
3. 메서드를 매개 변수로 호출 하 여 가져온 표식 유형 ID를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A> 메서드를 호출 하거나 메서드를 호출 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> 지정 된 텍스트 영역에 텍스트 마커를 적용 합니다.  
  
#### <a name="to-add-features-to-text-markers"></a>텍스트 표식에 기능을 추가 하려면  
  
1. 도구 설명, 특수 상황에 맞는 메뉴 또는 특수 한 상황에 대 한 처리기와 같은 추가 기능을 텍스트 표식에 추가 하는 것이 좋을 수 있습니다. 이를 수행하려면:  
  
2. 인터페이스를 구현 하는 개체를 만듭니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
3. 추가 기능이 필요한 경우 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced> 인터페이스를 구현 하는 동일한 개체에서 및 인터페이스를 구현 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> .  
  
4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>만든 인터페이스를 메서드에 대 한 호출에 전달 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 하거나 텍스트 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> 표식을 지정 된 텍스트 영역에 적용 하는 데 사용 되는 메서드를 전달 합니다.  
  
5. 텍스트 표식 영역에 상황에 맞는 메뉴 지원을 추가 하는 경우 메뉴를 만들어야 합니다.  
  
     상황에 맞는 메뉴를 만드는 방법에 대 한 자세한 내용은 [상황에 맞는](../extensibility/context-menus.md)메뉴를 참조 하세요.  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]환경에서는 제공 된 인터페이스의 메서드 (예: 메서드) <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A> 또는 메서드 (필요한 경우)를 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> .  
  
## <a name="see-also"></a>참고 항목  
 [레거시 API에서 텍스트 표식 사용](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [방법: 표준 텍스트 표식 추가](../extensibility/how-to-add-standard-text-markers.md)   
 [방법: 사용자 지정 텍스트 표식 만들기](../extensibility/how-to-create-custom-text-markers.md)   
 [방법: 오류 표식 구현](../extensibility/how-to-implement-error-markers.md)
