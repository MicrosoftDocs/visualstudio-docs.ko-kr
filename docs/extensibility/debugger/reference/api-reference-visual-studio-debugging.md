---
title: API 참조(비주얼 스튜디오 디버깅) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a2df6d82099a927664620e19096107f283afada
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738183"
---
# <a name="api-reference-visual-studio-debugging"></a>API 참조(Visual Studio 디버깅)
참조 섹션에는 API의 개념적 개요, 모든 API 요소에 대한 구문 및 사용법을 보여 주는 가이드 및 다양한 코드 예제가 포함되어 있습니다. 모든 참조는 범주별로 사전순으로 나열됩니다.

 다음 표에서는 메서드에서 반환하는 공통 `HRESULT` 값을 보여 주습니다.

|이름|설명|값|
|----------|-----------------|-----------|
|S_OK|성공했습니다.|0x00000000|
|E_UNEXPECTED|예기치 않은 오류가 발생했습니다.|0x8000FFFF|
|E_NOTIMPL|구현되지 않았습니다.|0x80004001|
|E_OUTOFMEMORY|작업을 완료하기에 메모리가 부족합니다.|0x8007000E|
|E_INVALIDARG|하나 이상의 인수가 유효하지 않습니다.|0x80070057|
|E_NOINTERFACE|이러한 인터페이스는 지원되지 않습니다.|0x80004002|
|E_POINTER|포인터가 잘못되었습니다.|0x80004003|
|E_HANDLE|잘못된 핸들입니다.|0x80070006|
|E_ABORT|작업이 중단되었습니다.|0x80004004|
|E_FAIL|예기치 않은 오류가 발생했습니다.|0x80004005|
|E_ACCESSDENIED|일반 액세스거부 오류.|0x80070005|

> [!NOTE]
> 디버깅 메서드가 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] `S_OK`반환되면 모든 out 매개 변수 포인터가 유효하다고 가정합니다. `S_OK`
>
> [!NOTE]
> 유효하지 `NULL` 않거나 [out] 매개 변수로 인해 IDE가 충돌할 수 있습니다.

## <a name="see-also"></a>참조
- [인터페이스](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [디버깅을 위한 SDK 도우미](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Visual Studio 디버거 확장성](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
