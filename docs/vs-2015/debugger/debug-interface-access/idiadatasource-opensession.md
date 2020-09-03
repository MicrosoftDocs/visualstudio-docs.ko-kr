---
title: 'IDiaDataSource:: openSession | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bec5507d15374e6e88afd4567d4b0fec9ca6cb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198596"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기호 쿼리를 위한 세션을 엽니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 ppSession  
 제한이 열려 있는 세션을 나타내는 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 다음 표에서는이 메서드에 사용할 수 있는 반환 값을 보여 줍니다.  
  
|값|설명|  
|-----------|-----------------|  
|E_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) 개체가 이전에 기호 소스를 사용 하 여 초기화 되지 않았습니다.|  
|E_INVALIDARG|잘못된 `ppSession` 매개 변수입니다.|  
|E_OUTOFMEMORY|메모리가 부족 하 여 세션을 열 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 이 메서드는 데이터 원본에 대 한 [IDiaSession](../../debugger/debug-interface-access/idiasession.md) 개체를 엽니다.  
  
 `IDiaSession` 개체는 데이터 원본에 대 한 쿼리를 구현 합니다. 세션은 각 디버그 기호 집합에 대해 하나의 주소 공간을 관리 합니다. 데이터 원본 기호에서 설명 하는 .exe 또는 .dll 파일이 여러 주소 범위에서 활성화 된 경우 (예: 여러 프로세스가 로드 되었으므로) 각 주소 범위에 대해 하나의 세션을 사용 해야 합니다.  
  
## <a name="example"></a>예제  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [설명은](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [.Pdb 파일 쿼리](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
