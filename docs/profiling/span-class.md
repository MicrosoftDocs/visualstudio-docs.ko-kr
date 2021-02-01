---
title: span 클래스 | Microsoft Docs
description: span 클래스 및 해당 클래스로 애플리케이션의 단계를 정의하는 방법을 알아봅니다. 또한 span 클래스 퍼블릭 생성자 및 상속 계층 구조에 관해 알아봅니다.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span
helpviewer_keywords:
- Concurrency::diagnostic::span class
ms.assetid: 527826a8-2590-43ad-b907-7bc0b7288e92
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ca1e674b13877ff8a8864c3b7447f15fd0307d7
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720048"
---
# <a name="span-class"></a>span 클래스
애플리케이션의 단계를 정의합니다.

## <a name="syntax"></a>구문

```cpp
class span;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|Name|설명|
|----------|-----------------|
|[span::span 생성자](../profiling/span-span-constructor.md)|`span` 클래스의 새 인스턴스를 초기화합니다.|
|[span::~span 소멸자](../profiling/span-tilde-span-destructor.md)|`span` 개체를 제거하고 해당 리소스를 해제합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조
 `span`

## <a name="requirements"></a>요구 사항
 **헤더:** *cvmarkersobj.h*

 **네임스페이스:** Concurrency::diagnostic

## <a name="see-also"></a>추가 정보
- [진단 네임스페이스](../profiling/diagnostic-namespace.md)