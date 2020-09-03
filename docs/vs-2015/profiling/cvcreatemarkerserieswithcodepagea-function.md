---
title: CvCreateMarkerSeriesWithCodePageA 함수 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 635a872372ab775eceb00854a616884f3fc19fef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155524"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

지정된 공급자 및 지정된 코드 페이지에 대한 표식 계열을 만듭니다. 이 함수는 표식 API ANSI 함수에 의해 작성되는 텍스트에 대한 코드 페이지를 명시적으로 지정하는 데 사용할 수 있습니다. 코드 페이지 설정은 추적을 캡처한 후 서로 다른 로캘/언어의 다양한 컴퓨터에서 분석하는 경우에 유용할 수 있습니다. 기본적으로 GetACP() 함수에서 반환한 코드 페이지가 사용됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pProvider`  
 이전에 CvInitProvider에서 초기화한 공급자 개체입니다. NULL일 수 없습니다.  
  
 `pSeriesName`  
 표식 계열 이름입니다. NULL일 수 없지만 빈 문자열을 사용할 수 있습니다.  
  
 `nTextCodePage`  
 유효한 코드 페이지입니다.  
  
 `ppMarkerSeries`  
 표식 계열 컨텍스트를 저장할 출력 변수의 주소입니다. NULL일 수 없습니다.  
  
## <a name="return-value"></a>반환 값  
 표식 계열이 성공적으로 생성된 경우 S_OK이고, 오류가 발생한 경우 오류 코드입니다. SUCCEEDED/FAILED 매크로를 사용하여 오류 조건을 확인할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** cvmarkers.h  
  
## <a name="see-also"></a>관련 항목  
 [C + + 라이브러리 참조](../profiling/cpp-library-reference.md)
