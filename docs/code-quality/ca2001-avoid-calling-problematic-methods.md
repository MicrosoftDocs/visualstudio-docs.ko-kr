---
title: 'CA2001: 문제가 있는 메서드는 호출하지 마세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95209067f3821b6446b64dc7990e189720d20cea
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233189"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: 문제가 있는 메서드는 호출하지 마세요.

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|범주|Microsoft.Reliability|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

멤버에서 잠재적 위험이나 문제가 있는 메서드를 호출합니다.

## <a name="rule-description"></a>규칙 설명

불필요 하 고 잠재적으로 위험한 메서드 호출을 방지 합니다. 멤버가 다음 메서드 중 하나를 호출 하면이 규칙의 위반이 발생 합니다.

|메서드|설명|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|GC를 호출 합니다. Collect는 응용 프로그램 성능에 큰 영향을 줄 수 있으며 거의 필요 하지 않습니다. 자세한 내용은 MSDN의 [Turiani의 Performance Tidbits](http://go.microsoft.com/fwlink/?LinkId=169256) 블로그 항목을 참조 하세요.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|스레드의 일시 중단 및 다시 시작은 예측할 수 없는 동작으로 인해 더 이상 사용 되지 않습니다.  <xref:System.Threading> 네임 스페이스의 다른 클래스 (예 <xref:System.Threading.Monitor>:, <xref:System.Threading.Mutex>및 <xref:System.Threading.Semaphore>)를 사용 하 여 스레드를 동기화 하거나 리소스를 보호 합니다.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Safehandle.dangerousgethandle 메서드는 유효 하지 않은 핸들을 반환할 수 있기 때문에 보안 위험을 초래 합니다. Safehandle.dangerousgethandle 메서드를 안전 <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> 하 게 사용 하는 방법에 대 한 자세한 내용은 및메서드를참조하세요.<xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A>|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|이러한 메서드는 예기치 않은 위치에서 어셈블리를 로드할 수 있습니다. 예를 들어, suzanne 쿡의 .net CLR Notes 블로그 게시물 [assembly.loadfile vs. 어셈블리](http://go.microsoft.com/fwlink/?LinkId=164450) 를 로드 하는 메서드에 대 한 정보에 대 한 [바인딩 컨텍스트를](http://go.microsoft.com/fwlink/?LinkId=164451) LoadFrom 및 선택 합니다.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) Ole32.lib<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) Ole32.lib|사용자 코드는 관리 되는 프로세스에서 실행을 시작 하는 시간을 기준으로 CoSetProxyBlanket를 안정적으로 호출 하는 것이 너무 늦습니다. CLR (공용 언어 런타임)은 사용자 P/Invoke가 성공할 수 없도록 하는 초기화 작업을 수행 합니다.<br /><br /> 관리 되는 응용 프로그램에 대해 CoSetProxyBlanket를 호출 해야 하는 경우 네이티브 코드 (C++) 실행 파일을 사용 하 여 프로세스를 시작 하 고 네이티브 코드에서 CoSetProxyBlanket를 호출한 다음 프로세스에서 관리 코드 응용 프로그램을 시작 하는 것이 좋습니다. 런타임 버전 번호를 지정 해야 합니다.|

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 위험 또는 문제가 있는 메서드에 대 한 호출을 제거 하거나 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

문제가 있는 방법에 대 한 대안을 사용할 수 없는 경우에만이 규칙에서 메시지를 표시 하지 않아야 합니다.

## <a name="see-also"></a>참고 항목

- [안정성 경고](../code-quality/reliability-warnings.md)