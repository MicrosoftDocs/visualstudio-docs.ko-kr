---
title: 'IDebugContainerField:: EnumFields | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 485de4bdc9ff5b17c056c0db4e2930f5c6986fe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205309"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

컨테이너의 필드에 대 한 열거자를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT EnumFields(   
   FIELD_KIND         dwKindFilter,  
   FIELD_MODIFIERS    dwModifiersFilter,  
   LPCOLESTR          pszNameFilter,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumFields(  
   enum_ FIELD_KIND      dwKindFilter,   
   enum_ FIELD_MODIFIERS dwModifiersFilter,   
   string                pszNameFilter,   
   NAME_MATCH            nameMatch,   
   out IEnumDebugFields  ppEnum  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwKindFilter`  
 진행 열거할 필드를 선택 하는 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 상수의 조합입니다. 필드 종류는 클래스 또는 기본 형식, 로컬, 매개 변수, "this" 포인터 등의 특정 정보 등의 저장소 형식을 설명할 수 있습니다.  
  
 `dwModifiersFilter`  
 진행 열거할 필드를 선택 하는 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) 상수의 조합입니다. 필드 한정자는 공용 또는 개인 또는 저장소 정보 (예: 가상, 정적 또는 최종)에 대 한 액세스 권한을 가질 수 있습니다.  
  
 `pszNameFilter`  
 진행 열거할 필드의 이름입니다. 모든 필드가 반환 되는 경우 null 값이 될 수 있습니다.  
  
 `nameMatch`  
 진행 검색에서 대/소문자를 구분 하는지 여부를 제어 하는 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) 열거형의 값입니다.  
  
 `ppEnum`  
 제한이 필드 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환 합니다. 필드가 없으면 null 값을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK 또는 S_FALSE (필드가 없는 경우)를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 예를 들어 `dwKindFilter` ,, `dwModifiersFilter` 및 `pszNameFilter` 매개 변수를 결합 하 여 "MyMethod" 라는 모든 공용 가상 메서드를 선택할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
