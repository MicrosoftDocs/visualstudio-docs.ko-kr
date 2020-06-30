---
title: 'CA2001: 문제가 있는 메서드를 호출 하지 마세요. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba64c27cde5f335f32cca362417078a5c9ed13e3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538582"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: 문제가 있는 메서드는 호출하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|범주|Microsoft.Reliability|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 멤버에서 잠재적 위험이나 문제가 있는 메서드를 호출합니다.

## <a name="rule-description"></a>규칙 설명
 불필요 하 고 잠재적으로 위험한 메서드 호출을 방지 합니다.

 멤버가 다음 메서드 중 하나를 호출 하면이 규칙의 위반이 발생 합니다.

|메서드|설명|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|GC를 호출 합니다. Collect는 응용 프로그램 성능에 큰 영향을 줄 수 있으며 거의 필요 하지 않습니다. 자세한 내용은 MSDN의 [Turiani의 Performance Tidbits](https://docs.microsoft.com/archive/blogs/ricom/when-to-call-gc-collect) 블로그 항목을 참조 하세요.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|스레드의 일시 중단 및 다시 시작은 예측할 수 없는 동작으로 인해 더 이상 사용 되지 않습니다.  네임 스페이스의 다른 클래스 (예 <xref:System.Threading> :, 및)를 사용 <xref:System.Threading.Monitor> 하 여 스레드를 <xref:System.Threading.Mutex> <xref:System.Threading.Semaphore> 동기화 하거나 리소스를 보호 합니다.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Safehandle.dangerousgethandle 메서드는 유효 하지 않은 핸들을 반환할 수 있기 때문에 보안 위험을 초래 합니다. <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> Safehandle.dangerousgethandle 메서드를 안전 하 게 사용 하는 방법에 대 한 자세한 내용은 및 메서드를 참조 하세요.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|이러한 메서드는 예기치 않은 위치에서 어셈블리를 로드할 수 있습니다. 예를 들어 어셈블리를 로드 하는 메서드에 대 한 자세한 내용은 Suzanne 쿡의 .NET CLR Notes 블로그 게시물 [assembly.loadfile And LoadFrom](https://docs.microsoft.com/archive/blogs/suzcook/loadfile-vs-loadfrom) (MSDN 웹 사이트에서 [바인딩 컨텍스트 선택](https://docs.microsoft.com/archive/blogs/suzcook/choosing-a-binding-context) )를 참조 하세요.|
|[CoSetProxyBlanket](https://msdn.microsoft.com/library/ms692692.aspx) (ole32.lib)<br /><br /> [CoInitializeSecurity](https://msdn.microsoft.com/library/ms693736.aspx) (ole32.lib)|사용자 코드는 관리 되는 프로세스에서 실행을 시작 하는 시간을 기준으로 CoSetProxyBlanket를 안정적으로 호출 하는 것이 너무 늦습니다. CLR (공용 언어 런타임)은 사용자 P/Invoke가 성공할 수 없도록 하는 초기화 작업을 수행 합니다.<br /><br /> 관리 되는 응용 프로그램에 대해 CoSetProxyBlanket를 호출 해야 하는 경우 네이티브 코드 (c + +) 실행 파일을 사용 하 여 프로세스를 시작 하 고 네이티브 코드에서 CoSetProxyBlanket를 호출한 다음 프로세스에서 관리 되는 코드 응용 프로그램을 시작 하는 것이 좋습니다. 런타임 버전 번호를 지정 해야 합니다.|

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 위험 또는 문제가 있는 메서드에 대 한 호출을 제거 하거나 바꿉니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 문제가 있는 방법에 대 한 대안을 사용할 수 없는 경우에만이 규칙에서 메시지를 표시 하지 않아야 합니다.

## <a name="see-also"></a>참고 항목
 [안정성 경고](../code-quality/reliability-warnings.md)
