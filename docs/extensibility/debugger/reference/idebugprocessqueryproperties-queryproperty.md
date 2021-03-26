---
description: 이 메서드는 디버깅 프로세스의 지정 된 속성 값을 쿼리 합니다.
title: 'IDebugProcessQueryProperties:: QueryProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties::QueryProperty
ms.assetid: 9a91707d-a590-44ef-b122-69d9816a7a79
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9814ff2dd377d1a10895f6ec5ba0818f480bfcf3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081401"
---
# <a name="idebugprocessquerypropertiesqueryproperty"></a>IDebugProcessQueryProperties::QueryProperty
이 메서드는 디버깅 프로세스의 지정 된 속성 값을 쿼리 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT QueryProperty(
   PROCESS_PROPERTY_TYPE  dwPropType,
   VARIANT               *pvarPropValue);
```

```csharp
int QueryProperty(
   enum_PROCESS_PROPERTY_TYPE dwPropType,
   out object                 pvarPropValue);
```

## <a name="parameters"></a>매개 변수
`dwPropType`\
진행 쿼리 된 속성의 정의입니다. 값은 다음과 같습니다.

- PROCESS_PROPERTY_COMMAND_LINE = 1

- PROCESS_PROPERTY_CURRENT_DIRECTORY = 2

- PROCESS_PROPERTY_ENVIRONMENT_VARIABLES = 3

`pvarPropValue`\
제한이 속성의 값입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 거의 사용 되지 않습니다.

## <a name="see-also"></a>참조
- [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)
