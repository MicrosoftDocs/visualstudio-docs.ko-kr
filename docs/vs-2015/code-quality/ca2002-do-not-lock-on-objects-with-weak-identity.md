---
title: 'CA2002: 약한 id를 가진 개체를 잠그지 않음 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 79f97de740ace9ccb59b13b3e4e30b34f38eb2f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534669"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: 약한 ID를 가진 개체를 잠그지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|범주|Microsoft.Reliability|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 스레드가 약한 id를 가진 개체에 대 한 잠금을 획득 하려고 합니다.

## <a name="rule-description"></a>규칙 설명
 애플리케이션 도메인 경계를 가로질러 직접 액세스할 수 있는 개체를 약한 ID를 가진 개체라고 합니다. 약한 ID를 가진 개체에 대해 잠금을 가져오려고 시도하는 스레드는 같은 개체에 대해 잠금을 가진 다른 애플리케이션 도메인의 스레드에 의해 차단될 수 있습니다. 다음 형식은 약한 id를 가지 며 규칙에 따라 플래그가 지정 됩니다.

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.String>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 설명 섹션의 목록에 없는 형식의 개체를 사용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="related-rules"></a>관련 규칙
 [CA2213: 삭제 가능한 필드는 삭제해야 합니다.](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>예
 다음 예제에서는 규칙을 위반 하는 일부 개체 잠금을 보여 줍니다.

 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/cs/FxCop.Reliability.LockWeakObjects.cs#1)]
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/vb/FxCop.Reliability.LockWeakObjects.vb#1)]

## <a name="see-also"></a>관련 항목
 <xref:System.Threading.Monitor> <xref:System.AppDomain>
 [Lock 문](https://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) [SyncLock 문](https://msdn.microsoft.com/library/14501703-298f-4d43-b139-c4b6366af176)
