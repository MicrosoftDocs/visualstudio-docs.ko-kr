---
title: SYMBOL_SEARCH_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SYMBOL_SEARCH_INFO_FIELDS
helpviewer_keywords:
- SYMBOL_SEARCH_INFO_FIELDS enumeration
ms.assetid: bce35af0-722d-46d4-afa6-eaae598c51ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bf8a1ad8a5dabc663ef29f5f2c36fdf0fbd8b786
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713475"
---
# <a name="symbol_search_info_fields"></a>SYMBOL_SEARCH_INFO_FIELDS
검색할 기호 정보의 종류를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};
typedef DWORD SYMBOL_SEARCH_INFO_FIELDS;
```

```csharp
public enum enum_SYMBOL_SEARCH_INFO_FIELDS
{
   SSIF_NONE                = 0x00000000,
   SSIF_VERBOSE_SEARCH_INFO = 0x00000001
};

```

## <a name="fields"></a>필드
 `SSIF_NONE`\
 플래그가 없음을 나타냅니다.

 `SSIF_VERBOSE_SEARCH_INFO`\
 기호를 찾는 데 사용 되는 모든 검색 경로를 반환 합니다.

## <a name="remarks"></a>설명
 이러한 플래그는 반환 되는 정보의 양을 확인 하기 위해 [Get기호 정보](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) 메서드에 매개 변수로 전달 됩니다.

> [!NOTE]
> 현재만 `SSIF_VERBOSE_SEARCH_INFO` 지원 되며 `dwFlags` 에 대 한 매개 변수로 지정 해야 합니다 `IDebugModule3::GetSymbolInfo` . 다른 모든 값은 오류를 반환 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
