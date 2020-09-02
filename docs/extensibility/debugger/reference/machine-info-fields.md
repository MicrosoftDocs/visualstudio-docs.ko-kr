---
title: MACHINE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MACHINE_INFO_FIELDS
helpviewer_keywords:
- MACHINE_INFO_FIELDS enumeration
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89a2552bb6a8bea88f54a897b829ab89b30ff413
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714513"
---
# <a name="machine_info_fields"></a>MACHINE_INFO_FIELDS
특정 컴퓨터에 대해 검색할 정보의 종류를 지정 합니다.

## <a name="syntax"></a>Syntax

```cpp
enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
typedef DWORD MACHINE_INFO_FIELDS;
```

```csharp
public enum enum_MACHINE_INFO_FIELDS { 
   MCIF_NAME  = 0x00000001,
   MCIF_FLAGS = 0x00000002,
   MCIF_ALL   = 0x00000003
};
```

## <a name="fields"></a>필드
 `MCIF_NAME`\
 구조에서 필드를 초기화/사용 `bstrName` 합니다.

 `MCIF_FLAGS`\
 구조에서 필드를 초기화/사용 `Flags` 합니다.

 `MIF_ALL`\
 구조체의 모든 필드를 초기화/사용 합니다.

## <a name="remarks"></a>설명
 이러한 값은 [Getmachineinfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md) 메서드에 전달 되어 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) 구조체에서 초기화할 멤버를 표시 합니다.

 또한 `Fields` 구조체의 멤버에서 사용 `MACHINE_INFO` 되어 사용 되는 필드와 유효한 필드를 표시 합니다.

 이러한 플래그는 비트와 함께 사용할 수 있습니다 `OR` .

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)
- [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)
