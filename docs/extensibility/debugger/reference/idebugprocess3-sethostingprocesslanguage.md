---
title: IDebugProcess3:SetHostingProcessLanguage | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a16f2c39fa2d53ffc4d113666ef7630557e61861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723572"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
이 메서드는 프로세스가 아래에 호스팅되는 언어를 설정합니다. 그런 다음 DE(디버그 엔진)에서 이 언어를 사용하여 적절한 식 계산기를 로드할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetHostingProcessLanguage(
   REFGUID guidLang
);
```

```csharp
int SetHostingProcessLanguage(
   ref Guid guidLang
);
```

## <a name="parameters"></a>매개 변수
`guidLang`\
【인】 `GUID` DE가 사용해야 하는 언어의 DE가 기본 언어를 `Guid.Empty` 사용하도록 (C++) 또는 (C#)를 지정합니다. `GUID_NULL`

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
- [GetHostingProcessLanguage는](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) 현재 언어 설정을 검색하는 데 사용할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)
