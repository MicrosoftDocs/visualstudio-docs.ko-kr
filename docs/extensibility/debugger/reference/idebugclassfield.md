---
description: 이 인터페이스는 클래스를 형식으로 나타냅니다.
title: IDebugClassField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField
helpviewer_keywords:
- IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dfb07f066d65ed48678c814444881cb004f14697
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088473"
---
# <a name="idebugclassfield"></a>IDebugClassField
이 인터페이스는 클래스를 형식으로 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugClassField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자는 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스를 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다. 이 인터페이스는 클래스 형식을 나타내는 특수화입니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 여러 인터페이스에는 [Idebugsymbolprovider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [idebugsymbolprovider](../../../extensibility/debugger/reference/idebugmethodfield.md)및 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)를 포함 하 여이 인터페이스를 반환할 수 있는 메서드가 있습니다. 또한 [Getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드가 플래그를 반환 하는 경우 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스에서이 인터페이스를 가져올 수 있습니다 `FIELD_TYPE_CLASS` .

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 및 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) 인터페이스의 메서드 외에도이 인터페이스는 다음을 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|이 클래스의 기본 클래스에 대 한 열거자를 만듭니다.|
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|특정 인터페이스가 클래스에 정의 되어 있는지 여부를 확인 합니다.|
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|이 클래스의 중첩 된 클래스에 대 한 열거자를 만듭니다.|
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|이 클래스를 포함 하는 클래스를 가져옵니다.|
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|이 클래스에서 구현 하는 인터페이스에 대 한 열거자를 만듭니다.|
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|이 클래스의 생성자에 대 한 열거자를 만듭니다.|
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|기본 인덱서의 이름을 가져옵니다.|
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|이 클래스의 중첩 된 열거자에 대 한 열거자를 만듭니다.|

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
