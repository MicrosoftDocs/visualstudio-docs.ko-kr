---
title: StartTrackingContextWithRoot | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StartTrackingContextWithRoot
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68e80da01a0ab1ad59bbb5bdb06c92c1a11a8ac1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182317"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

루트 마커를 지정하는 지시 파일을 사용하여 추적 컨텍스트를 시작합니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### <a name="parameters"></a>매개 변수  
 [in] `intermediateDirectory`  
 추적 로그를 저장할 디렉터리입니다.  
  
 [in] `taskName`  
 추적 컨텍스트를 식별합니다. 이 이름은 로그 파일 이름을 만드는 데 사용됩니다.  
  
 [in] `rootMarkerResponseFile`  
 루트 마커가 포함된 지시 파일의 경로 이름입니다. 루트 이름은 컨텍스트에 대한 모든 추적을 그룹화하는 데 사용됩니다.  
  
## <a name="return-value"></a>반환 값  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->)를 사용 하 여<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->)를 설정 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** FileTracker.h  
  
## <a name="see-also"></a>관련 항목  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
