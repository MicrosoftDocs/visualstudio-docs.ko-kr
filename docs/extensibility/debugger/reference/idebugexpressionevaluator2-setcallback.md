---
description: 식 계산기 (EE)에서 디버거 엔진 (DE)이 메트릭 설정을 읽는 데 사용할 콜백 인터페이스를 지정할 수 있도록 합니다.
title: 'IDebugExpressionEvaluator2:: SetCallback | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc858ab5d26ccffe33d26296e033ac577ddba440
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152392"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
식 계산기 (EE)에서 디버거 엔진 (DE)이 메트릭 설정을 읽는 데 사용할 콜백 인터페이스를 지정할 수 있도록 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetCallback (
    IDebugSettingsCallback2* pCallback
);
```

```csharp
int SetCallback (
    IDebugSettingsCallback2 pCallback
);
```

## <a name="parameters"></a>매개 변수
`pCallback`\
진행 설정 콜백에 사용할 인터페이스입니다.

## <a name="return-value"></a>반환 값
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
이 메서드는 식 계산기가 메트릭 설정을 읽는 데 사용할 수 있는 세션 디버그 관리자에 대 한 인터페이스를 제공 합니다. 원격 디버깅에서 컴퓨터의 메트릭을 읽는 데 유용 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 합니다.

## <a name="example"></a>예
다음 예제에서는 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) 인터페이스를 노출 하는 **CEE** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)
{
    // precondition
    INVARIANT( this );

    // function body
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)
    {
        EEDomain::fSetCallback DomainVal =
        {
            in_pCallback
        };

        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);
        ENSURE( bSuccess );
    }

    // postcondition
    INVARIANT( this );

    return S_OK;
}
```

## <a name="see-also"></a>참고 항목
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
