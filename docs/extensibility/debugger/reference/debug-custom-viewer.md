---
title: DEBUG_CUSTOM_VIEWER | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737538"
---
# <a name="debug_custom_viewer"></a>DEBUG_CUSTOM_VIEWER
사용자 지정 뷰어 또는 형식 시각화 도우미를 식별 하는 구조체입니다.

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
하나에 의해 구현 된 여러 뷰어 또는 시각화 도우미를 구분 하는 ID `GUID` 입니다.

`bstrMenuName`\
드롭다운 메뉴에 표시 되는 텍스트입니다.

`bstrDescription`\
사용자 지정 뷰어 또는 형식 시각화 도우미에 대 한 설명입니다 (사용 하지 않을 경우 null 값 이어야 함).

`guidLang`\
식 계산기를 제공 하는 언어입니다.

`guidVendor`\
식 계산기를 제공 하는 공급 업체입니다.

`bstrMetric`\
사용자 지정 뷰어 또는 형식 시각화 도우미가 `CLSID` 저장 되는 메트릭입니다.

## <a name="remarks"></a>설명
이 구조체의 목록은 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 메서드를 호출 하 여 반환 되 고, 확장을 통해 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) 메서드를 호출 하 여 반환 됩니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)
