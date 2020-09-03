---
title: 'CA2202: 개체를 여러 번 삭제 하지 마십시오. Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 31bf7fe33aa59c3a713d2da81ddbd11ed6899723
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546291"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: 개체를 여러 번 삭제하지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 메서드 구현에는 같은 개체에 대 한 여러 호출을 발생 시킬 수 있는 코드 경로 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 또는 일부 형식에 대 한 Close () 메서드와 같은 Dispose와 동일한 개체가 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명
 올바르게 구현 된 <xref:System.IDisposable.Dispose%2A> 메서드는 예외를 throw 하지 않고 여러 번 호출할 수 있습니다. 그러나이는 보장 되지 않으며,를 생성 하지 않도록 하려면 <xref:System.ObjectDisposedException?displayProperty=fullName> <xref:System.IDisposable.Dispose%2A> 개체에 대해를 두 번 이상 호출 하면 안 됩니다.

## <a name="related-rules"></a>관련 규칙
 [CA2000: 범위를 벗어나기 전에 개체를 삭제하세요.](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 코드 경로에 관계 없이 <xref:System.IDisposable.Dispose%2A> 개체에 대해 한 번만 호출 되도록 구현을 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 개체의를 <xref:System.IDisposable.Dispose%2A> 안전 하 게 호출할 수 있는 것으로 알려진 경우에도 나중에 구현이 변경 될 수 있습니다.

## <a name="example"></a>예
 중첩 `using` 된 문 ( `Using` Visual Basic)은 CA2202 경고 위반을 일으킬 수 있습니다. 중첩 된 내부 문의 IDisposable 리소스가 `using` 외부 문의 리소스를 포함 하는 경우 `using` 중첩 된 `Dispose` 리소스의 메서드는 포함 된 리소스를 해제 합니다. 이러한 상황이 발생 하면 `Dispose` 외부 문의 메서드는 `using` 해당 리소스를 두 번 삭제 하려고 시도 합니다.

 다음 예제에서 <xref:System.IO.Stream> 외부 using 문으로 만든 개체는 개체가 포함 된 개체의 Dispose 메서드에 있는 using 문 끝에서 해제 됩니다 <xref:System.IO.StreamWriter> `stream` . 외부 문의 끝에 개체를 `using` `stream` 두 번 해제 합니다. 두 번째 릴리스는 CA2202를 위반 하는 것입니다.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>예
 이 문제를 해결 하려면 `try` / `finally` 외부 문 대신 블록을 사용 `using` 합니다. 블록에서 `finally` `stream` 리소스가 null이 아닌지 확인 합니다.

```
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>관련 항목
 <xref:System.IDisposable?displayProperty=fullName> [삭제 패턴](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
