---
title: SetWefProcessId 메서드
description: SetWefProcessId 메서드가 WEF (웹 확장 프레임 워크) 콘텐츠를 실행 하는 프로세스 식별자를 제공 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 523279d70215af90ea070ea8272a5221d9947582
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524322"
---
# <a name="setwefprocessid-method"></a>SetWefProcessId 메서드
  WEF (웹 확장 프레임 워크) 콘텐츠를 실행 하는 프로세스 식별자를 제공 합니다.

## <a name="syntax"></a>구문

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>매개 변수

|매개 변수|Description|
|---------------|-----------------|
|*dwProcessId*|WEF 콘텐츠를 실행 하는 데 사용 되는 프로세스 식별자입니다.|

## <a name="return-value"></a>반환 값
 메서드가 성공적으로 완료되었는지 여부를 나타내는 HRESULT 값입니다.

## <a name="remarks"></a>설명
 WEF 콘텐츠 프로세스가 생성 된 후 WEF 콘텐츠가 실행 되기 전에이 메서드를 호출 해야 합니다.

 개발 환경에서 WEF 콘텐츠 프로세스에 디버거를 연결 하려면 환경에서이 메서드를 구현할 때이 작업을 수행 해야 합니다.
