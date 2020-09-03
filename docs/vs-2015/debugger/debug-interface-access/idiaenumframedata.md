---
title: IDiaEnumFrameData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData interface
ms.assetid: 2ca7fd5a-b2fa-4b3a-9492-0263eafc435b
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b3e2436d4b4eed6ac86591821090c89a538e06b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190788"
---
# <a name="idiaenumframedata"></a>IDiaEnumFrameData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

데이터 원본에 포함 된 다양 한 프레임 데이터 요소를 열거 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaEnumFrameData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDiaEnumFrameData` .  
  
|메서드|설명|  
|------------|-----------------|  
|[IDiaEnumFrameData::get__NewEnum](../../debugger/debug-interface-access/idiaenumframedata-get-newenum.md)|`IEnumVARIANT Interface`이 열거자의 버전을 검색 합니다.|  
|[IDiaEnumFrameData::get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md)|프레임 데이터 요소의 수를 검색 합니다.|  
|[IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)|인덱스를 사용 하 여 프레임 데이터 요소를 검색 합니다.|  
|[IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)|열거형 시퀀스에서 지정 된 수의 프레임 데이터 요소를 검색 합니다.|  
|[IDiaEnumFrameData::Skip](../../debugger/debug-interface-access/idiaenumframedata-skip.md)|열거형 시퀀스에서 지정 된 수의 프레임 데이터 요소를 건너뜁니다.|  
|[IDiaEnumFrameData::Reset](../../debugger/debug-interface-access/idiaenumframedata-reset.md)|열거형 시퀀스를 시작 부분으로 다시 설정 합니다.|  
|[IDiaEnumFrameData::Clone](../../debugger/debug-interface-access/idiaenumframedata-clone.md)|현재 열거자와 동일한 열거 상태를 포함 하는 열거자를 만듭니다.|  
|[IDiaEnumFrameData::frameByRVA](../../debugger/debug-interface-access/idiaenumframedata-framebyrva.md)|RVA (상대 가상 주소)를 기준으로 프레임을 반환 합니다.|  
|[IDiaEnumFrameData::frameByVA](../../debugger/debug-interface-access/idiaenumframedata-framebyva.md)|VA (가상 주소)를 기준으로 프레임을 반환 합니다.|  
  
## <a name="remarks"></a>설명  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [IDiaSession:: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) 메서드에서이 인터페이스를 가져옵니다. 자세한 내용은 예제를 참조 하세요.  
  
## <a name="example"></a>예  
 이 예제에서는 (함수)를 가져오고 `GetEnumFrameData` ( `ShowFrameData` 함수) 인터페이스를 사용 하는 방법을 보여 줍니다 `IDiaEnumFrameData` . 함수의 예는 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) 인터페이스를 참조 하세요 `PrintFrameData` .  
  
```cpp#  
  
      IDiaEnumFrameData* GetEnumFrameData(IDiaSession *pSession)  
{  
    IDiaEnumFrameData* pUnknown    = NULL;  
    REFIID             iid         = __uuidof(IDiaEnumFrameData);  
    IDiaEnumTables*    pEnumTables = NULL;  
    IDiaTable*         pTable      = NULL;  
    ULONG              celt        = 0;  
  
    if (pSession->getEnumTables(&pEnumTables) != S_OK)  
    {  
        wprintf(L"ERROR - GetTable() getEnumTables\n");  
        return NULL;  
    }  
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)  
    {  
        // There is only one table that matches the given iid  
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);  
        pTable->Release();  
        if (hr == S_OK)  
        {  
            break;  
        }  
    }  
    pEnumTables->Release();  
    return pUnknown;  
}  
  
void ShowFrameData(IDiaSession *pSession)  
{  
    IDiaEnumFrameData* pEnumFrameData = GetEnumFrameData(pSession);;  
  
    if (pEnumFrameData != NULL)  
    {  
        IDiaFrameData* pFrameData;  
        ULONG celt = 0;  
  
        while(pEnumFrameData->Next(1, &pFrameData, &celt) == S_OK &&  
              celt == 1)  
        {  
            PrintFrameData(pFrameData);  
            pFrameData->Release();  
        }  
        pEnumFrameData->Release();   
    }  
}  
```  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** Dia2  
  
 **라이브러리:** diaguids  
  
 **DLL:** msdia80.dll  
  
## <a name="see-also"></a>관련 항목  
 [인터페이스 (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession:: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
