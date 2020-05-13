---
title: 'IDebugEngine3:: Set기호 경로 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3ea3086931ab655209a5ca26d4d1527462fb205
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476806"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

디버깅 기호를 검색 하는 경로를 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`szSymbolSearchPath`|진행 기호 검색 경로를 포함 하는 문자열입니다. 자세한 내용은 "주의"를 참조 하세요. Null일 수 없습니다.|  
|`szSymbolCachePath`|진행 기호를 캐시할 수 있는 로컬 경로를 포함 하는 문자열입니다. Null일 수 없습니다.|  
|`Flags`|진행 사용 되지 않음 항상 0으로 설정 합니다.|  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>주의  
 문자열 `szSymbolSearchPath`은 기호를 검색 하기 위해 세미콜론으로 구분 된 하나 이상의 경로 목록입니다. 이러한 경로는 로컬 경로, UNC 스타일 경로 또는 URL이 될 수 있습니다. 이러한 경로는 다양 한 형식을 혼합 하 여 사용할 수도 있습니다. 경로가 UNC (예: \\\Symserver\Symbols) 인 경우 디버그 엔진은 경로가 기호 서버에 대 한 경로 인지 확인 하 고 해당 서버에서 기호를 로드 하 여 `szSymbolCachePath`에서 지정 된 경로에 캐시할 수 있어야 합니다.  
  
 기호 경로에는 하나 이상의 캐시 위치가 포함 될 수도 있습니다. 캐시는 우선 순위가 가장 높은 우선 순위에 우선 순위 대로 나열 되며 * 기호로 구분 됩니다. 예를 들면 다음과 같습니다.  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com  
```  
  
 [Loadsymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) 메서드는 기호의 실제 로드를 수행 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Loadsymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
