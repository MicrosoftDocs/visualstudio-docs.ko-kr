---
title: IDiaSectionContrib | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib interface
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc263d7238166f4f381bac35f0482ca2433f7b33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150473"
---
# <a name="idiasectioncontrib"></a>IDiaSectionContrib
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

섹션 기여를 설명 하는 데이터를 검색 합니다. 즉, compiland 이미지에 적용 되는 연속 메모리 블록입니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaSectionContrib : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDiaSectionContrib` .  
  
|메서드|설명|  
|------------|-----------------|  
|[IDiaSectionContrib::get_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|이 섹션을 제공한 compiland 기호에 대 한 참조를 검색 합니다.|  
|[IDiaSectionContrib::get_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|기여 주소의 섹션 부분을 검색 합니다.|  
|[IDiaSectionContrib::get_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|기여 주소의 오프셋 부분을 검색 합니다.|  
|[IDiaSectionContrib::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-relativevirtualaddress.md)|기여에 대 한 이미지의 RVA (상대 가상 주소)를 검색 합니다.|  
|[IDiaSectionContrib::get_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|기여의 VA (가상 주소)를 검색 합니다.|  
|[IDiaSectionContrib::get_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|섹션에서 바이트 수를 검색 합니다.|  
|[IDiaSectionContrib::get_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|섹션에서 메모리를 페이징할 수 없는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|섹션을 다음 메모리 경계로 패딩 하지 않아야 하는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_code](../../debugger/debug-interface-access/idiasectioncontrib-get-code.md)|섹션에 실행 코드가 포함 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|섹션에 16 비트 코드가 포함 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|섹션에 초기화 된 데이터가 포함 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_uninitializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-uninitializeddata.md)|섹션에 초기화 되지 않은 데이터가 포함 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|섹션에 설명 또는 비슷한 정보가 포함 되어 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|메모리 내 이미지의 일부가 만들어지기 전에 섹션을 제거할지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|섹션이 COMDAT 레코드 인지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|섹션을 삭제할 수 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|섹션을 캐시할 수 없는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|섹션을 메모리에서 공유할 수 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|섹션이 코드를 실행할 수 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|섹션을 읽을 수 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|섹션을 쓸 수 있는지 여부를 나타내는 플래그를 검색 합니다.|  
|[IDiaSectionContrib::get_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|섹션에 있는 데이터의 CRC (순환 중복 검사)를 검색 합니다.|  
|[IDiaSectionContrib::get_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|섹션에 대 한 재배치 정보의 CRC를 검색 합니다.|  
|[IDiaLineNumber::get_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|섹션에 대 한 compiland 식별자를 검색 합니다.|  
  
## <a name="remarks"></a>설명  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 이 인터페이스는 [IDiaEnumSectionContribs:: Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) 및 [IDiaEnumSectionContribs:: Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md) 메서드를 호출 하 여 가져옵니다. 인터페이스 가져오기에 대 한 예제는 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) 인터페이스를 참조 하세요 `IDiaSectionContrib` .  
  
## <a name="example"></a>예  
 이 함수는 연결 된 기호와 함께 각 섹션의 주소를 표시 합니다. 인터페이스를 얻는 방법에 대 한 자세한 내용은 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) 인터페이스를 참조 하세요 `IDiaSectionContrib` .  
  
```cpp#  
void PrintSectionContrib(IDiaSectionContrib* pSecContrib, IDiaSession* pSession)  
{  
    if (pSecContrib != NULL && pSession != NULL)  
    {  
        DWORD rva;  
        if ( pSecContrib->get_relativeVirtualAddress( &rva ) == S_OK )  
        {  
            printf( "\taddr: 0x%.8X", rva );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                        name != NULL ? name : L"",  
                        szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
        else  
        {  
            DWORD isect;  
            DWORD offset;  
            pSecContrib->get_addressSection( &isect );  
            pSecContrib->get_addressOffset( &offset );  
            printf( "\taddr: 0x%.4X:0x%.8X", isect, offset );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( SUCCEEDED( psession->findSymbolByAddr(  
                                              isect,  
                                              offset,  
                                              SymTagNull,  
                                              &pSym )  
                          )  
               )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                    name != NULL ? name : L"",  
                    szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>요구 사항  
 헤더: Dia2  
  
 라이브러리: diaguids  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>관련 항목  
 [인터페이스 (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaEnumSectionContribs:: Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)   
 [IDiaEnumSectionContribs::Next](../../debugger/debug-interface-access/idiaenumsectioncontribs-next.md)
