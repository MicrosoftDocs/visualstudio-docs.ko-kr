---
title: IDiaEnumDebugStreamData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData interface
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 378fc75c3bd392f228ea30d1736f059e0def6d52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695887"
---
# <a name="idiaenumdebugstreamdata"></a>IDiaEnumDebugStreamData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버그 데이터 스트림의 레코드에 대 한 액세스를 제공 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaEnumDebugStreamData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDiaEnumDebugStreamData` .  
  
|메서드|설명|  
|------------|-----------------|  
|[IDiaEnumDebugStreamData::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|이 열거자의 [IEnumVARIANT 인터페이스](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) 버전을 검색 합니다.|  
|[IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)|디버그 데이터 스트림의 레코드 수를 검색 합니다.|  
|[IDiaEnumDebugStreamData::get_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|디버그 데이터 스트림의 이름을 검색 합니다.|  
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|지정 된 레코드를 검색 합니다.|  
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|열거 된 시퀀스에서 지정 된 수의 레코드를 검색 합니다.|  
|[IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)|열거 시퀀스에서 지정 된 수의 레코드를 건너뜁니다.|  
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|열거 된 시퀀스를 시작 부분으로 다시 설정 합니다.|  
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|현재 열거자와 동일한 열거 시퀀스를 포함 하는 열거자를 만듭니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 디버그 데이터 스트림의 레코드 스트림을 나타냅니다. 각 레코드의 크기와 해석은 레코드가 제공 되는 데이터 스트림에 따라 달라 집니다. 이 인터페이스는 기호 파일의 원시 데이터 바이트에 대 한 액세스를 효과적으로 제공 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 [IDiaEnumDebugStreams:: Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md) 또는 [IDiaEnumDebugStreams:: Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md) 메서드를 호출 하 여 개체를 가져옵니다 `IDiaEnumDebugStreamData` .  
  
## <a name="example"></a>예  
 이 예제에서는 단일 데이터 스트림과 해당 레코드에 액세스 하는 방법을 보여 줍니다.  
  
```cpp#  
void PrintStreamData(IDiaEnumDebugStreamData* pStream)  
{  
    BSTR  wszName;  
    LONG  dwElem;  
    ULONG celt    = 0;  
    DWORD cbData;  
    DWORD cbTotal = 0;  
    BYTE  data[1024];  
  
    if(pStream->get_name(&wszName) != S_OK)  
    {  
        wprintf_s(L"ERROR - PrintStreamData() get_name\n");  
    }  
    else  
    {  
        wprintf_s(L"Stream: %s", wszName);  
        SysFreeString(wszName);  
    }  
    if(pStream->get_Count(&dwElem) != S_OK)  
    {  
        wprintf(L"ERROR - PrintStreamData() get_Count\n");  
    }  
    else  
    {  
        wprintf(L"(%d)\n", dwElem);  
    }  
    while(pStream->Next(1, sizeof(data), &cbData, (BYTE *)&data, &celt) == S_OK)  
    {  
        DWORD i;  
        for (i = 0; i < cbData; i++)  
        {  
            wprintf(L"%02X ", data[i]);  
            if(i && i % 8 == 7 && i+1 < cbData)  
            {  
                wprintf(L"- ");  
            }  
        }  
        wprintf(L"| ");  
        for(i = 0; i < cbData; i++)  
        {  
            wprintf(L"%c", iswprint(data[i]) ? data[i] : '.');  
        }  
        wprintf(L"\n");  
        cbTotal += cbData;  
    }  
    wprintf(L"Summary :\n\tSizeof(Elem) = %d\n\tNo of Elems = %d\n\n",  
            cbTotal/dwElem, dwElem);  
}  
```  
  
## <a name="requirements"></a>요구 사항  
 헤더: Dia2  
  
 라이브러리: diaguids  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>관련 항목  
 [인터페이스 (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreams:: Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
