---
title: 안정성 경고
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4b888dbbe7a26e5ff333ec39aa0fdfcec90b429
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586206"
---
# <a name="reliability-warnings"></a>안정성 경고

안정성 경고는 올바른 메모리 및 스레드 사용량과 같은 라이브러리 및 응용 프로그램 안정성을 지원 합니다. 안정성 규칙은 다음과 같습니다.

|규칙|설명|
|----------|-----------------|
|[CA2000: 범위를 벗어나기 전에 개체를 삭제하세요.](../code-quality/ca2000.md)|개체의 종료자가 실행되지 못하도록 하는 예외 이벤트가 발생할 수 있기 때문에 개체에 대한 모든 참조가 범위를 벗어나기 전에 개체를 명시적으로 삭제해야 합니다.|
|[CA2001: 문제가 있는 메서드는 호출하지 마세요.](../code-quality/ca2001.md)|멤버에서 잠재적 위험이나 문제가 있는 메서드를 호출합니다.|
|[CA2002: 약한 ID를 가진 개체를 잠그지 마십시오.](../code-quality/ca2002.md)|애플리케이션 도메인 경계를 가로질러 직접 액세스할 수 있는 개체를 약한 ID를 가진 개체라고 합니다. 약한 ID를 가진 개체에 대해 잠금을 가져오려고 시도하는 스레드는 같은 개체에 대해 잠금을 가진 다른 애플리케이션 도메인의 스레드에 의해 차단될 수 있습니다.|
|[CA2003: 파이버를 스레드로 취급하지 마세요.](../code-quality/ca2003.md)|관리 되는 스레드가 Win32 스레드로 처리 되 고 있습니다.|
|[CA2004: GC.KeepAlive에 대한 호출을 제거하세요.](../code-quality/ca2004.md)|SafeHandle 사용으로 변환 하는 경우 GC에 대 한 모든 호출을 제거 합니다. KeepAlive (개체). 이 경우 클래스는 GC를 호출할 필요가 없습니다. KeepAlive는 종료 자가 없지만 SafeHandle을 사용 하 여이에 대 한 OS 핸들을 마무리 한다고 가정 합니다.|
|[CA2006: SafeHandle을 사용하여 네이티브 리소스를 캡슐화하세요.](../code-quality/ca2006.md)|관리 코드에 IntPtr을 사용하는 것은 잠재적인 보안 및 안정성 문제를 나타냅니다. IntPtr을 사용할 때마다 SafeHandle 또는 유사한 기술을 대신 사용해야 하는지 여부를 결정하도록 검토해야 합니다.|
|[CA2007: 작업을 직접 대기하지 마세요.](../code-quality/ca2007.md)|비동기 메서드는 [awaits](/dotnet/csharp/language-reference/keywords/await) 를 <xref:System.Threading.Tasks.Task> 직접 기다립니다 합니다.|
|[CA2009: ImmutableCollection 값에 대해 ToImmutableCollection를 호출 하지 마십시오.](../code-quality/ca2009.md)|`ToImmutable`네임 스페이스의 <xref:System.Collections.Immutable> 변경할 수 없는 컬렉션에 대해 메서드를 불필요 하 게 호출 했습니다.|
