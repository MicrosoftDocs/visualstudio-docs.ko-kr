---
title: 'CA2233: 작업을 오버플로 해서는 안 됩니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperationsShouldNotOverflow
- CA2233
helpviewer_keywords:
- OperationsShouldNotOverflow
- CA2233
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eff09fb8f4423560c4681c94507d909f5864c69e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545238"
---
# <a name="ca2233-operations-should-not-overflow"></a>CA2233: 연산은 오버플로되지 않아야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|OperationsShouldNotOverflow|
|CheckId|CA2233|
|범주|Microsoft 사용|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 메서드는 산술 연산을 수행 하며 오버플로를 방지 하기 위해 피연산자의 유효성을 검사 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 연산 결과가 관련 데이터 형식에 대해 가능한 값의 범위를 벗어나지 않도록 먼저 피연산자의 유효성을 검사 하지 않고 산술 연산을 수행 하면 안 됩니다. 실행 컨텍스트 및 관련 된 데이터 형식에 따라 산술 오버플로가 발생 하면 <xref:System.OverflowException?displayProperty=fullName> 또는 결과의 가장 중요 한 비트가 무시 될 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 작업을 수행 하기 전에 피연산자의 유효성을 검사 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 피연산자의 가능한 값이 산술 연산을 오버플로 하지 않을 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example-of-a-violation"></a>위반 예

### <a name="description"></a>설명
 다음 예제의 메서드는이 규칙을 위반 하는 정수를 조작 합니다. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 이를 발생 시키려면 정수 오버플로 **제거** 옵션을 사용 하지 않도록 설정 해야 합니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Usage.OperationOverflow#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/cs/FxCop.Usage.OperationOverflow.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflow#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflow/vb/FxCop.Usage.OperationOverflow.vb#1)]

### <a name="comments"></a>주석
 이 예제의 메서드가 전달 되 면 <xref:System.Int32.MinValue?displayProperty=fullName> 연산이 언더플로 됩니다. 이렇게 하면 결과가 가장 중요 한 비트를 삭제 합니다. 다음 코드에서는이를 수행 하는 방법을 보여 줍니다.

 [C#]

```
public static void Main()
{
    int value = int.MinValue;    // int.MinValue is -2147483648
    value = Calculator.Decrement(value);
    Console.WriteLine(value);
}
```

 .VB

```
Public Shared Sub Main()
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648
    value = Calculator.Decrement(value)
    Console.WriteLine(value)
End Sub
```

### <a name="output"></a>출력

```
2147483647
```

## <a name="fix-with-input-parameter-validation"></a>입력 매개 변수 유효성 검사를 사용 하 여 수정

### <a name="description"></a>설명
 다음 예에서는 입력 값의 유효성을 검사 하 여 이전 위반을 수정 합니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Usage.OperationOverflowFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/cs/FxCop.Usage.OperationOverflowFixed.cs#1)]
 [!code-vb[FxCop.Usage.OperationOverflowFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed/vb/FxCop.Usage.OperationOverflowFixed.vb#1)]

## <a name="fix-with-a-checked-block"></a>확인 된 블록으로 수정

### <a name="description"></a>설명
 다음 예제에서는 확인 된 블록에서 작업을 래핑하여 이전 위반을 수정 합니다. 작업에서 오버플로가 발생 하면 <xref:System.OverflowException?displayProperty=fullName> 이 throw 됩니다.

 에서 확인 된 블록은 지원 되지 않습니다 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

### <a name="code"></a>코드
 [!code-csharp[FxCop.Usage.OperationOverflowChecked#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked/cs/FxCop.Usage.OperationOverflowChecked.cs#1)]

## <a name="turn-on-checked-arithmetic-overflowunderflow"></a>선택 된 산술 연산 오버플로/언더플로 켜기
 C #에서 확인 된 산술 연산 오버플로/언더플로를 설정 하는 경우 확인 된 블록의 모든 정수 연산을 래핑하는 것과 같습니다.

 **C에서 확인 된 산술 연산 오버플로/언더플로를 켜려면 #**

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.

2. **빌드** 탭을 선택하고 **고급**을 클릭합니다.

3. **산술 연산 오버플로/언더플로 확인** 을 선택 하 고 **확인**을 클릭 합니다.

## <a name="see-also"></a>관련 항목
 <xref:System.OverflowException?displayProperty=fullName>[C # 연산자](https://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43) [Checked 및 Unchecked](https://msdn.microsoft.com/library/a84bc877-2c7f-4396-8735-1ce97c42f35e)
