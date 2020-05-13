---
title: DBG_ATTRIB_FLAGS | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c8b3f52eff80c187d3c43b87cea804ace483169
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737551"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 또는 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 인터페이스에 대한 다양한 특성에 대해 설명합니다. [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조의 구성원입니다.

## <a name="syntax"></a>구문

```cpp
#define DBG_ATTRIB_NONE                 0x0000000000000000,
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,

// Attributes about the object itself

#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,

// Attributes about the value of the object

#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,

// Attributes about field access types for the object

#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,

// Attributes for the storage types of the object

#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,

// Attributes for the type modifiers on the object

#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,

// Attributes that describe the type of object

#define DBG_ATTRIB_DATA                 0x0000010000000000,
#define DBG_ATTRIB_METHOD               0x0000020000000000,
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,
#define DBG_ATTRIB_CLASS                0x0000080000000000,
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,

// Miscellaneous attributes

#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000

typedef UINT64 DBG_ATTRIB_FLAGS;
```

```csharp
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,

// Attributes about the object itself

public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,

// Attributes about the value of the object

public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,

// Attributes about field access types for the object

public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,

// Attributes for the storage types of the object

public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,

// Attributes for the type modifiers on the object

public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,

// Attributes that describe the type of object

public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,

// Miscellaneous attributes

public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000
```

## <a name="members"></a>멤버
 `DBG_ATTRIB_NONE`\
 특성이 없음을 나타냅니다.

 `DBG_ATTRIB_ALL`\
 모든 특성을 나타냅니다.

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 참조 또는 속성에 자식이 있음을 나타냅니다.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 이 개체에 대한 ID가 만들어졌음을 나타냅니다.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 이 개체에 대한 ID를 만들 수 있음을 나타냅니다.

 `DBG_ATTRIB_VALUE_READONLY`\
 값이 읽기 전용임을 나타냅니다.

 `DBG_ATTRIB_VALUE_ERROR`\
 값이 오류임을 나타냅니다.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 평가에 부작용이 있음을 나타냅니다.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 이 속성은 실제로 오버로드의 컨테이너임을 나타냅니다.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 의 `DEBUG_PROPERTY_INFO::bstrValue` 값이 부울임을 나타냅니다.

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 의 값이 `DEBUG_PROPERTY_INFO::bstrValue` 부울 및 `TRUE`을 나타냅니다.

 `DBG_ATTRIB_VALUE_INVALID`\
 `DEBUG_PROPERTY_INFO::bstrValue`의 값이 유효하지 않음을 나타냅니다.

 `DBG_ATTRIB_VALUE_NAT`\
 의 값이 `DEBUG_PROPERTY_INFO::bstrValue` *"사물이 아님"(NAT)임을*나타냅니다. NAT는 지연된 투기적 예외를 나타내는 인텔 64비트 프로세서의 레지스터 플래그를 설명합니다.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 의 `DEBUG_PROPERTY_INFO::bstrValue` 값이 자동으로 확장되었을 수 있음을 나타냅니다.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 평가에 시간이 정해진 것을 나타냅니다.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 의 `DEBUG_PROPERTY_INFO::bstrValue` 값이 원시 문자열로 나타낼 수 있음을 나타냅니다.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 이 속성에 연결된 사용자 지정 뷰어가 하나 이상 있음을 나타냅니다.

 `DBG_ATTRIB_ACCESS_NONE`\
 의 `private`가거나 `protected` 형식 `public`액세스가 없는 개체를 나타냅니다.

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 공용 액세스 권한이 있는 개체를 나타냅니다.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 개인 액세스 권한이 있는 개체를 나타냅니다.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 보호 액세스 권한이 있는 개체를 나타냅니다.

 `DBG_ATTRIB_ACCESS_FINAL`\
 최종 액세스 권한이 있는 개체를 나타냅니다.

 `DBG_ATTRIB_ACCESS_ALL`\
 마스크는 에서 `DBG_ATTRIB_FLAGS`액세스 특성을 추출합니다.

 `DBG_ATTRIB_STORAGE_NONE`\
 지정된 저장소 유형이 없음을 나타냅니다.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 전역 스토리지를 나타냅니다.

 `DBG_ATTRIB_STORAGE_STATIC`\
 정적 스토리지를 나타냅니다.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 레지스터의 저장소를 나타냅니다.

 `DBG_ATTRIB_STORAGE_ALL`\
 마스크는 에서 `DBG_ATTRIB_FLAGS`저장소 특성을 추출합니다.

 `DBG_ATTRIB_TYPE_NONE`\
 형식 수정기가 없음을 나타냅니다.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 개체 유형이 가상임을 나타냅니다.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 개체 형식이 상수임을 나타냅니다.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 개체 유형이 동기화되어 있음을 나타냅니다.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 개체 유형이 휘발성임을 나타냅니다.

 `DBG_ATTRIB_TYPE_ALL`\
 마스크는 에서 `DBG_ATTRIB_FLAGS`형식 특성을 추출합니다.

 `DBG_ATTRIB_DATA`\
 이 개체가 데이터 필드임을 나타냅니다.

 `DBG_ATTRIB_METHOD`\
 이 개체가 메서드임을 나타냅니다.

 `DBG_ATTRIB_PROPERTY`\
 이 개체가 속성임을 나타냅니다.

 `DBG_ATTRIB_CLASS`\
 이 개체가 클래스임을 나타냅니다.

 `DBG_ATTRIB_BASECLASS`\
 이 개체가 기본 클래스임을 나타냅니다.

 `DBG_ATTRIB_INTERFACE`\
 이 개체가 인터페이스임을 나타냅니다.

 `DBG_ATTRIB_INNERCLASS`\
 이 개체가 내부 클래스임을 나타냅니다.

 `DBG_ATTRIB_MOSTDERIVED`\
 이 개체가 *'가장 파생된'임을*나타냅니다. "가장*많이 파생된"이라는*용어는 참조 유형이 아니라 개체의 실제 형식을 의미합니다.

 `DBG_ATTRIB_CHILD_ALL`\
 `DBG_ATTRIB_DATA` 의 마스크를 나타냅니다. `DBG_ATTRIB_MOSTDERIVED`

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 개체에 연결된 사용자 지정 뷰어가 여러 개 있음을 나타냅니다.

## <a name="remarks"></a>설명

> [!NOTE]
> 이 열거형의 값은 C#에 대한 어셈블리에 실제로 정의되지 않습니다. 대신 정의 원본 파일에 복사해야 합니다.

 이러한 플래그는 예를 들어 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)에 인수로 전달될 때 개체의 자식을 필터링하는 데도 사용됩니다. 값을 약간 으로 결합할 `OR`수 있습니다.

 플래그는 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] [IDebugProperty2 인터페이스에서 IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 가져오고 사용자 지정 뷰어 목록에 대해 [GetCustomViewerList를](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 호출하는 표시입니다. [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
