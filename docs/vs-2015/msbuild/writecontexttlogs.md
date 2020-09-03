---
title: WriteContextTLogs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- WriteContextTLogs
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7bba9c5b46aa01cddca4de5c8e1347b540999289
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156455"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

현재 컨텍스트에 대한 로그 파일을 작성합니다.  
  
## <a name="syntax"></a>구문  
  
```  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>매개 변수  
 [in] `intermediateDirectory`  
 추적 로그를 저장할 디렉터리입니다.  
  
 [in] `tlogRootName`  
 로그 파일 이름의 루트 이름입니다.  
  
## <a name="return-value"></a>반환 값  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->)를 사용 하 여<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->)를 설정 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** FileTracker.h  
  
## <a name="see-also"></a>관련 항목  
 [WriteAllTLogs](../msbuild/writealltlogs.md)
