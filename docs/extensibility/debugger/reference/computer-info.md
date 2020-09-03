---
title: COMPUTER_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27794dff51646b72dbbfda81ead02e5206ade78b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737660"
---
# <a name="computer_info"></a>COMPUTER_INFO
디버거가 실행 되 고 있는 컴퓨터에 대해 설명 합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagCOMPUTER_INFO
{
    WORD wProcessorArchitecture;
    WORD wSuiteMask;
    DWORD dwOperatingSystemVersion;
} COMPUTER_INFO;
```

```csharp
public struct COMPUTER_INFO
{
    public ushort wProcessorArchitecture;
    public ushort wSuiteMask;
    public uint dwOperatingSystemVersion;
}
```

## <a name="members"></a>멤버
`wProcessorArchitecture`\
마이크로프로세서의 아키텍처를 식별 합니다.

`wSuiteMask`\
도구 모음 마스크를 식별 합니다.

`dwOperatingSystemVersion`\
운영 체제 버전 번호입니다.

## <a name="remarks"></a>설명
이 구조는 [Getcomputerinfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md) 메서드에 의해 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: Msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
