---
title: SccUninitialize 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcb0b3a6718cc90db6f7176c823ccccbbfc05f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190844"
---
# <a name="sccuninitialize-function"></a>SccUninitialize 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 소스 제어 플러그 인을 종료 하기 위해 [Sccinitialize](../extensibility/sccinitialize-function.md) 에 대 한 이전 호출로 생성 된 모든 할당 또는 열린 연결을 정리 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 진행 [Sccinitialize](../extensibility/sccinitialize-function.md)에서 만든 소스 제어 플러그 인 컨텍스트 구조에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.  
  
|값|설명|  
|-----------|-----------------|  
|SCC_OK|정리를 완료 했습니다.|  
  
## <a name="remarks"></a>설명  
 원본 제어 플러그 인은 종료 하 고 플러그 인이 컨텍스트 구조에 할당 한 메모리를 확보 하기 위한 준비를 담당 합니다. 함수는 플러그 인의 지정 된 각 인스턴스에 대해 한 번씩 호출 됩니다. [Sccinitialize](../extensibility/sccinitialize-function.md) 에 대 한 호출은이 호출 앞에 나옵니다. 를 호출할 때 여전히 열려 있는 프로젝트가 없습니다 `SccUninitialize` .  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
