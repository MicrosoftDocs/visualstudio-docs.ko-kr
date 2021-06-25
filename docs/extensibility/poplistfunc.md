---
title: POPLISTFUNC | Microsoft Docs
description: 소스 제어 플러그 인에서 파일 또는 디렉터리 목록을 업데이트하는 데 사용되는 POPLISTFUNC 콜백 함수에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- POPDIRLISTFUNC
helpviewer_keywords:
- POPLISTFUNC callback function
ms.assetid: b2199fd5-d707-4628-92dd-e2a01e2f507a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b52ed40397793b44f8a9c7ed9c36aa5996ae0176
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900384"
---
# <a name="poplistfunc"></a>POPLISTFUNC
이 콜백은 IDE에 의해 [SccPopulateList에](../extensibility/sccpopulatelist-function.md) 제공되며 소스 제어 플러그 인에서 파일 또는 디렉터리 목록을 업데이트하는 데 `SccPopulateList` 사용됩니다(함수에도 제공).

 사용자가 IDE에서 **Get** 명령을 선택하면 IDE는 사용자가 얻을 수 있는 모든 파일의 목록 상자를 표시합니다. 아쉽게도 IDE는 사용자가 얻을 수 있는 모든 파일의 정확한 목록을 알지 못합니다. 플러그 인에만 이 목록이 있습니다. 다른 사용자가 소스 코드 제어 프로젝트에 파일을 추가한 경우 이러한 파일이 목록에 표시되어야 하지만 IDE는 해당 파일에 대해 알지 못합니다. IDE는 사용자가 얻을 수 있다고 생각하는 파일 목록을 작성합니다. 사용자에게 이 목록을 표시하기 전에 [SccPopulateList를](../extensibility/sccpopulatelist-function.md) `,` 호출하여 소스 제어 플러그 인에 목록에서 파일을 추가하고 삭제할 수 있는 기회를 제공합니다.

## <a name="signature"></a>서명
 소스 제어 플러그 인은 다음 프로토타입을 통해 IDE 구현 함수를 호출하여 목록을 수정합니다.

```cpp
typedef BOOL (*POPLISTFUNC) (
   LPVOID pvCallerData,
   BOOL fAddRemove,
   LONG nStatus,
   LPSTR lpFileName
);
```

## <a name="parameters"></a>매개 변수
 pvCallerData `pvCallerData` 호출자(IDE)가 [SccPopulateList](../extensibility/sccpopulatelist-function.md)에 전달한 매개 변수입니다. 소스 제어 플러그 인은 이 매개 변수의 내용에 대해 아무 것도 가정하지 않아야 합니다.

 fAddRemove 이면 `TRUE` `lpFileName` 파일 목록에 추가해야 하는 파일입니다. 이면 `FALSE` `lpFileName` 파일 목록에서 삭제해야 하는 파일입니다.

 의 nStatus `lpFileName` `SCC_STATUS` 상태(비트의 조합입니다. 자세한 내용은 [파일 상태 코드](../extensibility/file-status-code-enumerator.md) 참조).

 lpFileName 목록에서 추가하거나 삭제할 파일 이름의 전체 디렉터리 경로입니다.

## <a name="return-value"></a>반환 값

|값|설명|
|-----------|-----------------|
|`TRUE`|플러그 인은 이 함수를 계속 호출할 수 있습니다.|
|`FALSE`|IDE 쪽에 문제가 발생했습니다(예: 메모리 부족 상황). 플러그 인은 작업을 중지해야 합니다.|

## <a name="remarks"></a>설명
 소스 제어 플러그 인이 파일 목록에 추가하거나 파일 목록에서 삭제하려는 각 파일에 대해 이 함수를 호출하여 를 `lpFileName` 전달합니다. `fAddRemove`플래그는 목록에 추가할 새 파일 또는 삭제할 이전 파일을 나타냅니다. `nStatus`매개 변수는 파일의 상태를 제공합니다. SCC 플러그 인이 파일 추가 및 삭제를 완료하면 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 호출에서 반환됩니다.

> [!NOTE]
> `SCC_CAP_POPULATELIST`기능 비트는 Visual Studio 필요합니다.

## <a name="see-also"></a>참조
- [IDE에서 구현하는 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)
- [파일 상태 코드](../extensibility/file-status-code-enumerator.md)
