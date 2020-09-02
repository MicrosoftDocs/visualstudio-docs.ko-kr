---
title: 'IDebugProperty2:: EnumChildren | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cd5b29978b6b67cc80e95b86603b0caf487c26c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164951"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

속성의 자식 목록을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT EnumChildren (   
   DEBUGPROP_INFO_FLAGS      dwFields,  
   DWORD                     dwRadix,  
   REFGUID                   guidFilter,  
   DBG_ATTRIB_FLAGS          dwAttribFilter,  
   LPCOLESTR                 pszNameFilter,  
   DWORD                     dwTimeout,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumChildren (   
   enum_DEBUGPROP_INFO_FLAGS   dwFields,  
   uint                        dwRadix,  
   ref Guid                    guidFilter,  
   uint                        dwAttribFilter,  
   string                      pszNameFilter,  
   uint                        dwTimeout,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwFields`  
 진행 열거 된 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조체에서 채울 필드를 지정 하는 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) 열거형의 플래그 조합입니다.  
  
 `dwRadix`  
 진행 숫자 정보의 서식을 지정 하는 데 사용할 기 수를 지정 합니다.  
  
 `guidFilter`  
 진행 `dwAttribFilter` `pszNameFilter` 열거 될 자식을 선택 하기 위해 및 매개 변수와 함께 사용 되는 필터의 GUID입니다 `DEBUG_PROPERTY_INFO` . 예를 들어 `guidFilterLocals` 지역 변수에 대 한 필터입니다.  
  
 `dwAttribFilter`  
 진행 열거할 개체 형식 (예: [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) `DBG_ATTRIB_METHOD` 이 속성의 자식일 수 있는 모든 메서드)을 지정 하는 DBG_ATTRIB_FLAGS 열거형의 플래그 조합입니다. `guidFilter`및 `pszNameFilter` 매개 변수와 함께 사용 됩니다.  
  
 `pszNameFilter`  
 진행 `guidFilter` `dwAttribFilter` 열거 될 자식을 선택 하기 위해 및 매개 변수와 함께 사용 되는 필터의 이름입니다 `DEBUG_PROPERTY_INFO` . 예를 들어 "MyX" 라는 이름의 모든 자식에 대해이 매개 변수를 "MyX" 필터로 설정 합니다.  
  
 `dwTimeout`  
 진행 이 메서드에서 반환 될 때까지 대기할 최대 시간 (밀리초)을 지정 합니다. `INFINITE`무기한 대기 하려면를 사용 합니다.  
  
 `ppEnum`  
 제한이 자식 속성의 목록을 포함 하는 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
