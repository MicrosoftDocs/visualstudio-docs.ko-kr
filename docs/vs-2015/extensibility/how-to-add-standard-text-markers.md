---
title: '방법: 표준 텍스트 표식 추가 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841366"
---
# <a name="how-to-add-standard-text-markers"></a>방법: 표준 텍스트 표식 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음 절차를 사용 하 여 핵심 편집기에서 제공 하는 기본 텍스트 표식 유형 중 하나를 만들 수 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 있습니다.  
  
### <a name="to-create-a-text-marker"></a>텍스트 표식을 만들려면  
  
1. 하나 또는 두 차원 좌표계를 사용 하는지에 따라 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> 메서드 또는 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> 하 여 새 텍스트 표식을 만듭니다.  
  
     이 메서드 호출에서 표식 형식, 표식을 만들 텍스트 범위 및 인터페이스를 지정 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 합니다. 그런 다음이 메서드는 새로 만든 텍스트 표식에 대 한 포인터를 반환 합니다. 표식 유형은 열거형에서 가져옵니다 <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>표식 이벤트를 알리도록 하려면 인터페이스를 지정 합니다.  
  
    > [!NOTE]
    > 주 UI 스레드에서만 텍스트 표식을 만듭니다. 핵심 편집기는 텍스트 버퍼의 내용을 사용 하 여 텍스트 표식을 만들고 텍스트 버퍼는 스레드로부터 안전 하지 않습니다.  
  
## <a name="adding-a-custom-command"></a>사용자 지정 명령 추가  
 인터페이스를 구현 `IVsTextMarkerClient` 하 고 표식에서 포인터를 제공 하면 여러 가지 방법으로 표식 동작이 향상 됩니다. 먼저, 표식을 위한 팁을 제공 하 고 명령을 실행할 수 있습니다. 이를 통해 개별 표식에 대 한 이벤트 알림을 수신 하 고 표식에 대 한 사용자 지정 상황에 맞는 메뉴를 만들 수도 있습니다. 다음 절차를 사용 하 여 사용자 지정 명령을 마커 상황에 맞는 메뉴에 추가할 수 있습니다.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>상황에 맞는 메뉴에 사용자 지정 명령을 추가 하려면  
  
1. 상황에 맞는 메뉴가 표시 되기 전에 환경에서는 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> 하 고 영향을 받는 텍스트 표식과 상황에 맞는 메뉴의 명령 항목 수에 대 한 포인터를 전달 합니다.  
  
     예를 들어 상황에 맞는 메뉴의 중단점 관련 명령에는 다음 스크린샷에 표시 된 것 처럼 **새 중단점**을 통해 **중단점 제거** 가 포함 됩니다.  
  
     ![마커 상황에 맞는 메뉴](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2. 사용자 지정 명령의 이름을 나타내는 일부 텍스트를 다시 전달 합니다. 예를 들어, **중단점 제거** 는 환경에서 아직 제공 하지 않은 경우 사용자 지정 명령 일 수 있습니다. 또한 명령이 지원 되는지, 사용 가능 하 고 사용 하도록 설정 되 고, 또는 on off로 설정 된 경우에도 다시 전달 합니다. 환경에서는이 정보를 사용 하 여 상황에 맞는 메뉴에 사용자 지정 명령을 올바른 방식으로 표시 합니다.  
  
3. 명령을 실행 하기 위해 환경에서는 메서드를 호출 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> 텍스트 표식에 대 한 포인터와 상황에 맞는 메뉴에서 선택한 명령의 수를 전달 합니다.  
  
     이 호출에서이 정보를 사용 하 여 사용자 지정 명령이 지정 하는 텍스트 표식의 동작을 실행할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [레거시 API에서 텍스트 표식 사용](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [방법: 오류 마커 구현](../extensibility/how-to-implement-error-markers.md)   
 [방법: 사용자 지정 텍스트 표식 만들기](../extensibility/how-to-create-custom-text-markers.md)   
 [방법: 텍스트 표식 사용](../extensibility/how-to-use-text-markers.md)
