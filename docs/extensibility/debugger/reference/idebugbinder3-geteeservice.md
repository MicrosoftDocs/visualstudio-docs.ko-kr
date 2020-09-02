---
title: 'IDebugBinder3:: GetEEService | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735832"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
이 메서드는 요청 된 서비스를 반환 합니다.

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
[in] `GUID` 공급 업체의 (null 값이 허용 되는 경우)

`language`\
[in] `GUID` 언어의 (null 값이 허용 되는 경우)

`iid`\
[in] `IID` 가져올 서비스의입니다.

`ppService`\
제한이 요청 된 서비스에 대 한 인터페이스입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 `IID` [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) 인터페이스 ()에 대 한를 전달 `IID_IEEVisualizerServiceProvider` 하 여 형식 시각화 도우미 서비스를 사용할 수 있는지 확인 합니다. 그렇다면 식 계산기는 형식 시각화 도우미를 지원 하기 위해 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 인터페이스를 가져올 수 있습니다. 자세한 내용은 [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md) 를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md)
