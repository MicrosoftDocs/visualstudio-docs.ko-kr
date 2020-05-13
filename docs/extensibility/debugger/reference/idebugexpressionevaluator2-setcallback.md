---
title: IDebug표현평가자2::세트콜백 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 907fdaa928b3f84f6ff37490d5c54a9d48515053
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729340"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
식 평가기(EE)를 사용하면 DE(디버거 엔진)가 메트릭 설정을 읽는 데 사용할 콜백 인터페이스를 지정할 수 있습니다.

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
【인】 설정 콜백에 사용할 인터페이스입니다.

## <a name="return-value"></a>Return Value
성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
이 메서드는 식 계산자가 메트릭 설정을 읽는 데 사용할 수 있는 세션 디버그 관리자에 대 한 인터페이스를 제공 합니다. [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 원격 디버깅에서 컴퓨터에서 메트릭을 읽는 데 유용합니다.

## <a name="example"></a>예제
다음 예제에서는 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) 인터페이스를 노출 하는 **CEE** 개체에 대 한이 메서드를 구현 하는 방법을 보여 줍니다.

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

## <a name="see-also"></a>참조
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
