---
title: 동시성 네임스페이스(동시성 시각화 도우미) | Microsoft 문서
description: C++에서 동시 프로그램을 작성하려면 C++용 동시성 프레임워크인 동시성 런타임에 대한 액세스를 제공하는 동시성 네임스페이스를 사용합니다.
custom.ms: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: 001fbfce-a278-4502-aa27-26d65dd61453
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 884af287ced5a13cf4483e01617ffaf594d03e66
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941205"
---
# <a name="concurrency-namespace-concurrency-visualizer"></a>동시성 네임스페이스(동시성 시각화 도우미)
`Concurrency` 네임스페이스는 C++용 동시 프로그래밍 프레임워크인 동시성 런타임에 액세스하는 데 사용할 수 있는 클래스와 함수를 제공합니다. 자세한 내용은 [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)을 참조하세요.

## <a name="syntax"></a>구문

```cpp
namespace Concurrency;
```

## <a name="members"></a>구성원

### <a name="namespaces"></a>네임스페이스

|이름|설명|
|----------|-----------------|
|[diagnostic 네임스페이스](../profiling/diagnostic-namespace.md)|`diagnostics` 네임스페이스는 동시성 시각화 도우미 표식을 내보내는 기능을 제공합니다.|

## <a name="requirements"></a>요구 사항
 **헤더:** cvmarkersobj.h

## <a name="see-also"></a>참고 항목
- [C 라이브러리 참조](../profiling/c-library-reference.md)