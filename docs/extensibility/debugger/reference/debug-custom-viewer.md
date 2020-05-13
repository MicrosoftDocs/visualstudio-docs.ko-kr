---
title: DEBUG_CUSTOM_VIEWER | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUG_CUSTOM_VIEWER
helpviewer_keywords:
- DEBUG_CUSTOM_VIEWER structure
ms.assetid: 8e0ef3f0-0107-48e8-a037-6e52b4c4ed9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3de9b8f7ef30cffbdd78399dc831060e413ba51b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737538"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
사용자 지정 뷰어 또는 형식 시각화 도우미를 식별하는 구조체입니다.

## <a name="syntax"></a>구문

```cpp
typedef struct tagDEBUG_CUSTOM_VIEWER {
    DWORD dwID;
    BSTR  bstrMenuName;
    BSTR  bstrDescription;
    GUID  guidLang;
    GUID  guidVendor;
    BSTR  bstrMetric;
} DEBUG_CUSTOM_VIEWER;
```

```csharp
public struct DEBUG_CUSTOM_VIEWER {
    public uint   dwID;
    public string bstrMenuName;
    public string bstrDescription;
    public Guid   guidLang;
    public Guid   guidVendor;
    public string bstrMetric;
};
```

## <a name="members"></a>멤버
`dwID`\
하나의 구현된 여러 뷰어 또는 시각화 `GUID`도우미를 구분하는 ID입니다.

`bstrMenuName`\
드롭다운 메뉴에 표시되는 텍스트입니다.

`bstrDescription`\
사용자 지정 뷰어 또는 형식 시각화 도우미에 대한 설명입니다(사용하지 않는 경우 null 값이어야 합니다).

`guidLang`\
제공식 평가자의 언어입니다.

`guidVendor`\
제공 식 평가기의 공급업체입니다.

`bstrMetric`\
사용자 지정 뷰어 또는 형식 `CLSID` 시각화 도우미가 저장되는 메트릭입니다.

## <a name="remarks"></a>설명
이 구조의 목록은 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 메서드(및 확장별로 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) 메서드)를 호출하여 반환됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
