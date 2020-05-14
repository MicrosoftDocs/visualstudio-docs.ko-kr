---
title: 아이디버그레퍼런스2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52f655afd35ed316080a3a85ccfae047aa50d87f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720268"
---
# <a name="idebugreference2"></a>IDebugReference2
이 인터페이스는 스택 프레임 속성 또는 다른 속성에 대한 참조를 나타냅니다.

> [!NOTE]
> `IDebugReference2`나중에 사용할 수 있는 예약이 이며 `E_NOTIMPL`모든 메서드를 반환 합니다.

## <a name="syntax"></a>구문

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE는 특정 종류의 값에 대한 참조를 나타내기 위해 이 인터페이스를 구현합니다. 예를 들어, 값은 식 평가의 결과로 숫자 값, 메모리를 표시하는 데 사용되는 메모리 컨텍스트 또는 레지스터 및 해당 값의 목록일 수 있습니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스를 얻으려면 [GetReference를](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) 호출합니다. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) 및 [GetDerivedMostReference도](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) 이 인터페이스를 반환합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugReference2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|이 참조를 설명하는 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조를 가져옵니다.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|문자열에서 이 참조값을 설정합니다.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|다른 참조에서 이 참조의 값을 설정합니다.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|이 참조의 자식을 수반합니다.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|이 참조의 부모를 가져옵니다.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|이 참조의 가장 파생된 참조를 가져옵니다.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|이 참조가 참조하는 메모리 바이트를 가져옵니다.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|이 참조에 대한 메모리 컨텍스트를 가져옵니다.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|이 참조의 크기를 바이트로 가져옵니다.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|이 참조 유형을 설정합니다.|
|[비교](../../../extensibility/debugger/reference/idebugreference2-compare.md)|이 참조를 다른 참조와 비교합니다.|

## <a name="remarks"></a>설명

> [!NOTE]
> "속성"의 이러한 사용은 클래스의 멤버 변수를 의미하는 것과 혼동해서는 안되지만 이러한 엔터티를 `IDebugReference2` 나타낼 수 있습니다.

- [IDebugProperty2는](../../../extensibility/debugger/reference/idebugproperty2.md) 속성을 나타내고 `IDebugReference2` 속성에 대한 참조를 나타내며, 일반적으로 디버깅 중인 프로그램의 개체에 대한 참조입니다.

 속성과 참조의 주요 차이점은 속성이 개체의 명명된 인스턴스를 참조하는 반면 참조는 명명되지 않은 인스턴스를 참조한다는 것입니다. 예를 들어 속성은 프로그램의 힙에 있는 개체를 로 `"a.b"`참조할 수 있습니다. 다른 속성은 와 동일한 `"c.d"`개체를 참조할 수 있습니다. 이 속성을 참조하는 방법은 `"a.b"` 해당 `"c.d"` 속성을 사용하거나 범위에 있어야 합니다. 이 동일한 개체에 대한 참조는 이름이 없습니다. 해당 개체에 대한 메모리가 유효한 한 개체를 참조할 수 있습니다.

 인터페이스는 `IDebugProperty2` 이름, 형식 및 주소가 있는 값으로 생각할 수 있습니다. 반면에 AN은 `IDebugReference2`형식과 주소로 생각할 수 있습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [Get참조](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
