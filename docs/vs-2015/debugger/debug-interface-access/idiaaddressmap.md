---
title: IDiaAddressMap | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 012d6b1ca06b06f56239048fee712d898a79efa9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547509"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

DIA SDK에서 디버그 개체의 가상 및 상대 가상 주소를 계산 하는 방법에 대 한 제어를 제공 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서는의 메서드를 보여 줍니다 `IDiaAddressMap` .  
  
|메서드|설명|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|특정 세션에 대 한 주소 맵이 설정 되었는지 여부를 나타냅니다.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|주소 맵을 사용 하 여 기호 주소를 변환 해야 하는지 여부를 지정 합니다.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|상대 가상 주소의 계산과 사용이 사용 되는지 여부를 나타냅니다.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|클라이언트에서 상대 가상 주소의 계산을 사용 하거나 사용 하지 않도록 설정할 수 있습니다.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|현재 이미지 맞춤을 검색 합니다.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|이미지 맞춤을 설정 합니다.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|상대 가상 주소를 변환할 수 있도록 이미지 헤더를 설정 합니다.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|이미지 레이아웃 번역을 지 원하는 주소 맵을 제공 합니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스에서 제공 하는 컨트롤은 사용자가 제공 하는 두 데이터 집합 (이미지 헤더 및 주소 맵)으로 캡슐화 됩니다. 대부분의 클라이언트는 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드를 사용 하 여 이미지에 대 한 적절 한 디버그 정보를 찾고 메서드는 일반적으로 필요한 모든 헤더와 맵 데이터를 검색할 수 있습니다. 그러나 일부 클라이언트는 특수 처리를 구현 하 고 데이터를 검색 합니다. 이러한 클라이언트는 인터페이스의 메서드를 사용 `IDiaAddressMap` 하 여 DIA SDK에 검색 결과를 제공 합니다.  
  
## <a name="notes-for-callers"></a>호출자 참고 사항  
 이 인터페이스는 DIA session 개체에서 사용할 수 있습니다. 클라이언트는 `QueryInterface` DIA session 개체 인터페이스 (일반적으로 [IDiaSession](../../debugger/debug-interface-access/idiasession.md))에서 메서드를 호출 하 여 `IDiaAddressMap` 인터페이스를 검색 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Dia2  
  
 라이브러리: diaguids  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>관련 항목  
 [인터페이스 (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
