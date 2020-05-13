---
title: 아이더버그클래스필드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b0e4cd7c851e65edf299f45ec97273804c25d8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734295"
---
# <a name="idebugclassfield"></a>IDebugClassField
이 인터페이스는 클래스를 형식으로 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 기호 공급자는 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스를 구현하는 동일한 개체에 이 인터페이스를 구현합니다. 이 인터페이스는 클래스 형식을 나타내는 특수화입니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 인터페이스의 숫자는 [IDebugSymbol공급자,](../../../extensibility/debugger/reference/idebugsymbolprovider.md) [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)및 [IDebugCustomAttribute를](../../../extensibility/debugger/reference/idebugcustomattribute.md)포함하여이 인터페이스를 반환 할 수있는 메서드가 있습니다. 또한 [QueryInterface를](/cpp/atl/queryinterface) 사용하여 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드가 플래그를 `FIELD_TYPE_CLASS`반환하는 경우 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스에서 이 인터페이스를 가져올 수 있습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 및 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스의 메서드 외에도 다음을 구현합니다.

|방법|설명|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|이 클래스의 기본 클래스에 대한 열거수를 만듭니다.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|특정 인터페이스가 클래스에 정의되어 있는지 여부를 결정합니다.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|이 클래스의 중첩된 클래스에 대한 열거수를 만듭니다.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|이 클래스를 둘러싸는 클래스를 가져옵니다.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|이 클래스에서 구현한 인터페이스에 대한 열거형기를 만듭니다.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|이 클래스의 생성자에 대한 열거수를 만듭니다.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|기본 인덱서의 이름을 가져옵니다.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|이 클래스의 중첩 된 열거형에 대 한 열거자를 만듭니다.|

## <a name="requirements"></a>요구 사항
 헤더: sh.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
