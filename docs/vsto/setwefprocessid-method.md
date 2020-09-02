---
title: SetWefProcessId 메서드
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
ms.openlocfilehash: 13a6748e2e3b66f581a3c72c1f847e0329189e64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537334"
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

|매개 변수|설명|
|---------------|-----------------|
|*dwProcessId*|WEF 콘텐츠를 실행 하는 데 사용 되는 프로세스 식별자입니다.|

## <a name="return-value"></a>반환 값
 메서드가 성공적으로 완료되었는지 여부를 나타내는 HRESULT 값입니다.

## <a name="remarks"></a>설명
 WEF 콘텐츠 프로세스가 생성 된 후 WEF 콘텐츠가 실행 되기 전에이 메서드를 호출 해야 합니다.

 개발 환경에서 WEF 콘텐츠 프로세스에 디버거를 연결 하려면 환경에서이 메서드를 구현할 때이 작업을 수행 해야 합니다.
