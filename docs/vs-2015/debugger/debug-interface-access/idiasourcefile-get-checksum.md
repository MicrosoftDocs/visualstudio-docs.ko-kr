---
title: IDiaSourceFile::get_checksum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f87f5cdd937c0e172e7b96cf0858423b14686d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190747"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

체크섬 바이트를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cbData`  
 진행 데이터 버퍼의 크기 (바이트)입니다.  
  
 `pcbData`  
 제한이 체크섬 바이트의 수를 반환 합니다. 이 매개 변수는 `NULL`일 수 없습니다.  
  
 `data`  
 [in, out] 체크섬 바이트로 채워지는 버퍼입니다. 이 매개 변수가 이면는 `NULL` `pcbData` 필요한 바이트 수를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 체크섬 바이트를 생성 하는 데 사용 된 체크섬 알고리즘의 유형을 확인 하려면 [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) 메서드를 호출 합니다.  
  
 체크섬은 일반적으로 소스 파일의 이미지에서 생성 되므로 소스 파일의 변경 내용이 체크섬 바이트의 변경 내용에 반영 됩니다. 체크섬 바이트가 파일의 로드 된 이미지에서 생성 된 체크섬과 일치 하지 않으면 파일이 손상 되거나 변조 된 것으로 간주 됩니다.  
  
 일반적인 체크섬의 크기는 32 바이트이 하 이지만이 체크섬의 최대 크기인 것으로 가정 하지는 않습니다. 매개 변수를로 설정 하 여 `data` `NULL` 체크섬을 검색 하는 데 필요한 바이트 수를 가져옵니다. 그런 다음 적절 한 크기의 버퍼를 할당 하 고 새 버퍼를 사용 하 여이 메서드를 한 번 더 호출 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
