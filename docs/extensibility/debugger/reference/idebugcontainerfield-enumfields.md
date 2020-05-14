---
title: 아이디버그 컨테이너필드::에넘필즈 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afc461d52f81afc2c2e7127a90313bea7b9dacf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733229"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
컨테이너 필드에 대한 열거수를 만듭니다.

## <a name="syntax"></a>구문

```cpp
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

## <a name="parameters"></a>매개 변수
`dwKindFilter`\
【인】 필드를 선택하는 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 상수의 조합입니다. 필드 종류는 클래스 또는 기본 요소와 같은 저장소 형식 또는 로컬, 매개 변수 또는 "this" 포인터와 같은 특정 정보를 설명할 수 있습니다.

`dwModifiersFilter`\
【인】 다음에 사용할 필드를 선택하는 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) 상수의 조합입니다. 필드 수정자는 공용 또는 개인과 같은 액세스 권한 또는 가상, 정적 또는 최종 과 같은 저장소 정보일 수 있습니다.

`pszNameFilter`\
【인】 누거할 필드의 이름입니다. 모든 필드를 반환해야 하는 경우 null 값이 될 수 있습니다.

`nameMatch`\
【인】 검색이 대/소문자를 구분하는지 여부를 제어하는 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) 열거형의 값입니다.

`ppEnum`\
【아웃】 필드 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환합니다. 필드가 없는 경우 null 값을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 필드가 없는 경우 S_OK 반환하거나 S_FALSE. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 예를 `dwModifiersFilter`들어 `pszNameFilter` , "MyMethod"라는 모든 공용 가상 메서드를 선택하기 위해 에서 및 매개 변수를 결합할 수 있습니다. `dwKindFilter`

## <a name="see-also"></a>참조
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
