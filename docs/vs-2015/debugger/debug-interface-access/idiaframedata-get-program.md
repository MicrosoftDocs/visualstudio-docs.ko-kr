---
title: IDiaFrameData::get_program | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d87f5c7fda25a901d44b9f511b9a92eb4471f845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180009"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

현재 함수를 호출 하기 전에 레지스터 집합을 계산 하는 데 사용 되는 프로그램 문자열을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 제한이 프로그램 문자열을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`이 속성이 지원 되지 않으면를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 프로그램 문자열은 프롤로그를 설정 하기 위해 해석 되는 매크로의 시퀀스입니다. 예를 들어 일반적인 스택 프레임은 프로그램 문자열을 사용할 수 있습니다 `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` . 형식은 역방향 폴란드어 표기법입니다. 여기서 연산자는 피연산자를 따릅니다. `T0` 스택의 임시 변수를 나타냅니다. 이 예제에서는 다음 단계를 수행합니다.  
  
1. 레지스터의 내용을 `ebp` 로 이동 `T0` 합니다.  
  
2. `4`의 값에를 추가 `T0` 하 여 주소를 생성 하 고 해당 주소에서 값을 가져온 다음 register에 값을 저장 `eip` 합니다.  
  
3. 에 저장 된 주소에서 값을 가져오고 `T0` 해당 값을 register에 저장 `ebp` 합니다.  
  
4. `8`의 값에을 추가 하 `T0` 고 레지스터에 해당 값을 저장 `esp` 합니다.  
  
   프로그램 문자열은 CPU와 현재 스택 프레임이 나타내는 함수에 대해 설정 된 호출 규칙에 따라 다릅니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
