---
title: IDiaSourceFile::get_checksumType | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f859bce63e2976b23ab613e249dad41b2bc63486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190706"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

체크섬 형식을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 제한이 체크섬 유형을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 체크섬 유형은 체크섬 알고리즘에 매핑될 수 있는 값입니다. 예를 들어 표준 PDB 파일 형식은 일반적으로 다음 값 중 하나를 사용할 수 있습니다.  
  
|체크섬 형식|CryptoAPI 레이블|설명|  
|-------------------|---------------------|-----------------|  
|0|\<none>|체크섬이 없습니다.|  
|1|`CALG_MD5`|MD5 해시 알고리즘을 사용 하 여 생성 된 체크섬입니다.|  
|2|`CALG_SHA1`|SHA1 해시 알고리즘을 사용 하 여 생성 된 체크섬입니다.|  
  
 `CryptoAPI`레이블은 열거형에서 가져온 것 `ALG_ID` 입니다. 해시 알고리즘에 대 한 자세한 내용은 `CryptoAPI` Microsoft의 섹션을 참조 하십시오 [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] .  
  
 소스 파일에 대 한 실제 체크섬 바이트를 가져오려면 [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) 메서드를 호출 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)
