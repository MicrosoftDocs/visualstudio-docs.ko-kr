---
title: IDiaPropertyStorage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage interface
ms.assetid: d3197a38-5973-4e56-873e-4f1b84c3f674
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 29832934b848729879ee1ba802c70f85117efd2a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537630"
---
# <a name="idiapropertystorage"></a>IDiaPropertyStorage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

DIA 속성 집합의 영구적 속성을 읽을 수 있습니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaPropertyStorage : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDiaPropertyStorage` .  
  
|메서드|설명|  
|------------|-----------------|  
|[IDiaPropertyStorage::Enum](../../debugger/debug-interface-access/idiapropertystorage-enum.md)|이 집합 내에 있는 속성의 열거자에 대 한 포인터를 가져옵니다.|  
|[IDiaPropertyStorage::ReadBOOL](../../debugger/debug-interface-access/idiapropertystorage-readbool.md)|`BOOL`속성 집합의 값을 읽습니다.|  
|[IDiaPropertyStorage::ReadBSTR](../../debugger/debug-interface-access/idiapropertystorage-readbstr.md)|`BSTR`속성 집합의 값을 읽습니다.|  
|[IDiaPropertyStorage::ReadDWORD](../../debugger/debug-interface-access/idiapropertystorage-readdword.md)|`DWORD`속성 집합의 값을 읽습니다.|  
|[IDiaPropertyStorage::ReadLONG](../../debugger/debug-interface-access/idiapropertystorage-readlong.md)|`LONG`속성 집합의 값을 읽습니다.|  
|[IDiaPropertyStorage::ReadMultiple](../../debugger/debug-interface-access/idiapropertystorage-readmultiple.md)|속성 집합의 속성 값을 읽습니다.|  
|[IDiaPropertyStorage::ReadPropertyNames](../../debugger/debug-interface-access/idiapropertystorage-readpropertynames.md)|지정 된 속성 식별자에 해당 하는 문자열 이름을 가져옵니다.|  
|[IDiaPropertyStorage::ReadULONGLONG](../../debugger/debug-interface-access/idiapropertystorage-readulonglong.md)|`ULONGLONG`속성 집합의 값을 읽습니다.|  
  
## <a name="remarks"></a>설명  
 속성 집합 내의 각 속성은 `ULONG` 해당 집합에 고유한 4 바이트 값인 속성 식별자 (ID)로 식별 됩니다. 인터페이스를 통해 노출 되는 속성은 `IDiaPropertyStorage` 부모 인터페이스에서 사용할 수 있는 속성에 해당 합니다. 예를 들어 인터페이스를 통해 이름으로 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 인터페이스의 속성에 액세스할 수 있습니다 `IDiaPropertyStorage` . 그러나 속성에 액세스할 수 있지만 속성이 특정 개체에 대해 유효한 것은 아닙니다 `IDiaSymbol` .  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 다른 인터페이스에서 메서드를 호출 하 여이 인터페이스를 가져옵니다 `QueryInterface` . 인터페이스에 대해 쿼리할 수 있는 인터페이스는 `IDiaPropertyStorage` 다음과 같습니다.  
  
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
  
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
  
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
  
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
  
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
  
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
  
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
  
## <a name="example"></a>예  
 이 예제에서는 개체에 의해 노출 되는 모든 속성을 표시 하는 함수를 보여 줍니다 `IDiaPropertyStorage` . IDiaInjectedSource 인터페이스에서 인터페이스를 가져오는 방법에 대 한 예제는 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) 인터페이스를 참조 하세요 `IDiaPropertyStorage` . [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
  
```cpp#  
void PrintPropertyStorage(IDiaPropertyStorage* pPropertyStorage)  
{  
    IEnumSTATPROPSTG* pEnumProps;  
    STATPROPSTG       prop;  
    DWORD             celt = 1;  
  
    if (pPropertyStorage->Enum(&pEnumProps) == S_OK)  
    {  
        while (pEnumProps->Next(celt, &prop, &celt) == S_OK)  
        {  
            PROPSPEC pspec = { PRSPEC_PROPID, prop.propid };  
            PROPVARIANT vt = { VT_EMPTY };  
  
            if (pPropertyStorage->ReadMultiple( 1, &pspec, &vt) == S_OK)  
            {  
                switch( vt.vt ){  
                    case VT_BOOL:  
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bVal ? L"true" : L"false" );  
                        break;  
                    case VT_I2:  
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.iVal );  
                        break;  
                    case VT_UI2:  
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.uiVal );  
                        break;  
                    case VT_I4:  
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.intVal );  
                        break;  
                    case VT_UI4:  
                        wprintf( L"%32s:\t 0x%0x\n", prop.lpwstrName, vt.uintVal );  
                        break;  
                    case VT_UI8:  
                        wprintf( L"%32s:\t 0x%x\n", prop.lpwstrName, vt.uhVal.QuadPart );  
                        break;  
                    case VT_BSTR:  
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bstrVal );  
                        break;  
                    case VT_UNKNOWN:  
                        wprintf( L"%32s:\t %p\n", prop.lpwstrName, vt.punkVal );  
                        break;  
                    case VT_SAFEARRAY:  
                        break;  
                    default:  
                       break;  
                }  
                VariantClear((VARIANTARG*) &vt);  
            }  
        }  
        pEnumProps->Release();  
    }  
}  
```  
  
## <a name="requirements"></a>요구 사항  
 헤더: Dia2  
  
 라이브러리: diaguids  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>관련 항목  
 [인터페이스 (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession:: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
