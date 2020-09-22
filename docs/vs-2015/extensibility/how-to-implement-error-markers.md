---
title: '방법: 오류 표식 구현 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2af9e0765fb5bc73a35bebfc2f50f5d2a41122d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841706"
---
# <a name="how-to-implement-error-markers"></a>방법: 오류 표식 구현
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

오류 표식 (또는 빨간색 물결선)은 구현 하기 위한 텍스트 편집기 사용자 지정이 가장 어렵습니다. 그러나 VSPackage 사용자에 게 제공 하는 혜택은 제공 하는 비용 보다 훨씬 더 클 수 있습니다. 오류 마커는 언어 파서가 하다 고 판단 물결선 또는 물결선 물결선으로 잘못 표시 되는 텍스트를 표시 합니다. 이 표시기는 프로그래머에 게 잘못 된 코드를 시각적으로 표시 하는 데 도움이 됩니다.  
  
 텍스트 표식을 사용 하 여 빨간색 물결 무늬 밑줄을 구현 합니다. 한 가지 규칙으로, 언어 서비스는 텍스트 버퍼에 빨간색 물결선 밑줄을 유휴 시간이 나 백그라운드 스레드에서 백그라운드 전달으로 추가 합니다.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>빨강 물결선 밑줄 기능을 구현 하려면  
  
1. 빨간색 물결선 밑줄을 표시할 텍스트를 선택 합니다.  
  
2. 형식의 표식을 만듭니다 `MARKER_CODESENSE_ERROR` . 자세한 내용은 [방법: 표준 텍스트 표식 추가](../extensibility/how-to-add-standard-text-markers.md)를 참조 하세요.  
  
3. 그런 다음 인터페이스 포인터를 전달 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 합니다.  
  
   이 프로세스를 사용 하 여 지정 된 표식에서 팁 텍스트 또는 특별 한 상황에 맞는 메뉴를 만들 수도 있습니다. 자세한 내용은 [방법: 표준 텍스트 표식 추가](../extensibility/how-to-add-standard-text-markers.md)를 참조 하세요.  
  
   오류 표식을 표시 하려면 다음 개체가 필요 합니다.  
  
- 파서입니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>다시 구문 분석할 줄을 식별 하기 위해 줄 정보의 변경 기록을 유지 하는 작업 공급자 (즉,의 구현)입니다.  
  
- 을 사용 하 여 뷰에서 캐럿 변경 이벤트를 캡처하는 텍스트 뷰 필터입니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A> .  
  
  파서, 작업 공급자 및 필터는 오류 표식을 가능 하 게 하는 데 필요한 인프라를 제공 합니다. 다음 단계는 오류 표식을 표시 하는 프로세스를 제공 합니다.  
  
1. 필터링 되는 뷰에서 필터는 해당 뷰의 데이터와 연결 된 작업 공급자에 대 한 포인터를 가져옵니다.  
  
    > [!NOTE]
    > 메서드 팁, 문 완성, 오류 표식 등에 대해 동일한 명령 필터를 사용할 수 있습니다.  
  
2. 필터가 다른 줄로 이동 했음을 나타내는 이벤트를 수신 하면 오류가 있는지 확인 하기 위해 작업이 생성 됩니다.  
  
3. 작업 처리기는 줄이 변경 되었는지 여부를 확인 합니다. 이 경우 줄에서 오류를 구문 분석 합니다.  
  
4. 오류가 발견 되 면 작업 공급자는 작업 항목 인스턴스를 만듭니다. 이 인스턴스는 환경에서 텍스트 보기의 오류 표식으로 사용 하는 텍스트 표식을 만듭니다.  
  
## <a name="see-also"></a>참고 항목  
 [레거시 API에서 텍스트 표식 사용](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [방법: 표준 텍스트 표식 추가](../extensibility/how-to-add-standard-text-markers.md)   
 [방법: 사용자 지정 텍스트 표식 만들기](../extensibility/how-to-create-custom-text-markers.md)   
 [방법: 텍스트 표식 사용](../extensibility/how-to-use-text-markers.md)
