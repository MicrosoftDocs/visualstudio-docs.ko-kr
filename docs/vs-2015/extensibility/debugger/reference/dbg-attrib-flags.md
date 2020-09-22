---
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74694c903040b278ed8864b46756cac66381405a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841499"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 또는 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 인터페이스에 대 한 다양 한 특성을 설명 합니다. [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조체의 멤버입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
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
  
## <a name="members"></a>구성원  
 DBG_ATTRIB_NONE  
 특성이 없음을 나타냅니다.  
  
 DBG_ATTRIB_ALL  
 모든 특성을 나타냅니다.  
  
 DBG_ATTRIB_OBJ_IS_EXPANDABLE  
 참조 또는 속성에 자식이 있음을 나타냅니다.  
  
 DBG_ATTRIB_OBJ_HAS_ID  
 이 개체에 대 한 ID가 생성 되었음을 나타냅니다.  
  
 DBG_ATTRIB_OBJ_CAN_HAVE_ID  
 이 개체의 ID를 만들 수 있음을 나타냅니다.  
  
 DBG_ATTRIB_VALUE_READONLY  
 값이 읽기 전용임을 나타냅니다.  
  
 DBG_ATTRIB_VALUE_ERROR  
 값이 오류 임을 나타냅니다.  
  
 DBG_ATTRIB_VALUE_SIDE_EFFECT  
 평가 결과에 부작용이 있음을 나타냅니다.  
  
 DBG_ATTRIB_OVERLOADED_CONTAINER  
 이 속성이 실질적으로 오버 로드의 컨테이너 임을 나타냅니다.  
  
 DBG_ATTRIB_VALUE_BOOLEAN  
 의 값 `DEBUG_PROPERTY_INFO::bstrValue` 이 부울 임을 나타냅니다.  
  
 DBG_ATTRIB_VALUE_BOOLEAN_TRUE  
 의 값 `DEBUG_PROPERTY_INFO::bstrValue` 이 부울 및 임을 나타냅니다 `TRUE` .  
  
 DBG_ATTRIB_VALUE_INVALID  
 `DEBUG_PROPERTY_INFO::bstrValue`의 값이 유효하지 않음을 나타냅니다.  
  
 DBG_ATTRIB_VALUE_NAT  
 의 값 `DEBUG_PROPERTY_INFO::bstrValue` 이 "*사물*" (NAT) 임을 나타냅니다. NAT는 지연 된 잘못 된 예외를 나타내는 Intel 64 비트 프로세서의 레지스터 플래그를 설명 합니다.  
  
 DBG_ATTRIB_VALUE_AUTOEXPANDED  
 의 값이 자동 확장 되었을 수 있음을 나타냅니다 `DEBUG_PROPERTY_INFO::bstrValue` .  
  
 DBG_ATTRIB_VALUE_TIMEOUT  
 평가 시간이 초과 되었음을 나타냅니다.  
  
 DBG_ATTRIB_VALUE_RAW_STRING  
 의 값을 `DEBUG_PROPERTY_INFO::bstrValue` 원시 문자열로 나타낼 수 있음을 나타냅니다.  
  
 DBG_ATTRIB_VALUE_CUSTOM_VIEWER  
 이 속성에 연결 된 사용자 지정 뷰어가 하나 이상 있음을 나타냅니다.  
  
 DBG_ATTRIB_ACCESS_NONE  
 `public`, 및 형식 액세스를 모두 포함 하지 않는 개체를 나타냅니다 `private` `protected` .  
  
 DBG_ATTRIB_ACCESS_PUBLIC  
 공용 액세스 권한이 있는 개체를 나타냅니다.  
  
 DBG_ATTRIB_ACCESS_PRIVATE  
 개인 액세스 권한이 있는 개체를 나타냅니다.  
  
 DBG_ATTRIB_ACCESS_PROTECTED  
 보호 액세스 권한이 있는 개체를 나타냅니다.  
  
 DBG_ATTRIB_ACCESS_FINAL  
 최종 액세스 권한이 있는 개체를 나타냅니다.  
  
 DBG_ATTRIB_ACCESS_ALL  
 액세스 특성을 추출할 마스크 `DBG_ATTRIB_FLAGS` 입니다.  
  
 DBG_ATTRIB_STORAGE_NONE  
 지정 된 저장소 유형이 없음을 나타냅니다.  
  
 DBG_ATTRIB_STORAGE_GLOBAL  
 전역 스토리지를 나타냅니다.  
  
 DBG_ATTRIB_STORAGE_STATIC  
 정적 스토리지를 나타냅니다.  
  
 DBG_ATTRIB_STORAGE_REGISTER  
 레지스터의 저장소를 나타냅니다.  
  
 DBG_ATTRIB_STORAGE_ALL  
 저장소 특성을 추출 하는 마스크 `DBG_ATTRIB_FLAGS` 입니다.  
  
 DBG_ATTRIB_TYPE_NONE  
 형식 한정자가 없음을 나타냅니다.  
  
 DBG_ATTRIB_TYPE_VIRTUAL  
 개체의 형식이 가상 임을 나타냅니다.  
  
 DBG_ATTRIB_TYPE_CONSTANT  
 개체 형식이 상수임을 나타냅니다.  
  
 DBG_ATTRIB_TYPE_SYNCHRONIZED  
 개체의 형식이 동기화 됨을 나타냅니다.  
  
 DBG_ATTRIB_TYPE_VOLATILE  
 개체의 형식이 휘발성 임을 나타냅니다.  
  
 DBG_ATTRIB_TYPE_ALL  
 형식 특성을 추출할 마스크 `DBG_ATTRIB_FLAGS` 입니다.  
  
 DBG_ATTRIB_DATA  
 이 개체가 데이터 필드 임을 나타냅니다.  
  
 DBG_ATTRIB_METHOD  
 이 개체가 메서드 임을 나타냅니다.  
  
 DBG_ATTRIB_PROPERTY  
 이 개체가 속성 임을 나타냅니다.  
  
 DBG_ATTRIB_CLASS  
 이 개체가 클래스 임을 나타냅니다.  
  
 DBG_ATTRIB_BASECLASS  
 이 개체가 기본 클래스 임을 나타냅니다.  
  
 DBG_ATTRIB_INTERFACE  
 이 개체가 인터페이스 임을 나타냅니다.  
  
 DBG_ATTRIB_INNERCLASS  
 이 개체가 내부 클래스 임을 나타냅니다.  
  
 DBG_ATTRIB_MOSTDERIVED  
 이 개체가 '*가장 많이 파생*됨 ' 임을 나타냅니다. "가장 많이*파생*된" 용어는 해당 참조의 형식이 아니라 개체의 실제 형식을 의미 합니다.  
  
 DBG_ATTRIB_CHILD_ALL  
 에서의 마스크를 `DBG_ATTRIB_DATA` 나타냅니다 `DBG_ATTRIB_MOSTDERIVED` .  
  
 DBG_ATTRIB_MULTI_CUSTOM_VIEWERS  
 개체에 연결 된 여러 사용자 지정 뷰어가 있음을 나타냅니다.  
  
## <a name="remarks"></a>설명  
  
> [!NOTE]
> 이 열거형의 값은 c #에 대 한 어셈블리에 실제로 정의 되어 있지 않습니다. 대신, 소스 파일에 정의를 복사 해야 합니다.  
  
 이러한 플래그는 개체의 자식을 필터링 하는 데에도 사용 됩니다. 예를 들어 [enumchildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)에 인수로 전달 될 때 사용 됩니다. 값을 비트와 함께 사용할 수 있습니다 `OR` .  
  
 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`플래그는 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스에서 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 가져오고 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 를 호출 하 여 사용자 지정 뷰어 목록을 표시 한다는 것을 나타냅니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
