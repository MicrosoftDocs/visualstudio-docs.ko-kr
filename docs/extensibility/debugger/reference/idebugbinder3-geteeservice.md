---
title: 이데버그바인더3::겟E서비스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c08d7df4a6b05be489f6b9ab06569c085f3b1f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735832"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
이 메서드는 요청된 서비스를 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>매개 변수
`vendor`\
【인】 `GUID` 공급 업체 (null 값은 허용 됩니다).

`language`\
【인】 `GUID` (null 값은 허용됩니다)

`iid`\
【인】 `IID` 을 획득할 수 있습니다.

`ppService`\
【아웃】 요청된 서비스에 대한 인터페이스입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [IEEVisualizerService서비스제공자](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) 인터페이스 ()`IID_IEEVisualizerServiceProvider`에 `IID` 대해 전달하여 유형 시각화 도우미 서비스를 사용할 수 있는지 확인합니다. 이 경우 식 평가기는 형식 시각화 도우미를 지원하기 위해 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 인터페이스를 가져올 수 있습니다. 자세한 내용은 [데이터 시각화 및 보기를](../../../extensibility/debugger/visualizing-and-viewing-data.md) 참조하십시오.

## <a name="see-also"></a>참조
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md)
