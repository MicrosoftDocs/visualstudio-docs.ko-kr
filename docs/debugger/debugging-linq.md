---
title: LINQ 디버그 | Microsoft Docs
description: Visual Studio에서 LINQ(언어 통합 쿼리)를 디버그합니다. LINQ 결과를 봅니다. LINQ 코드를 한 단계씩 실행할 때 동작 차이점을 이해합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 903ffb5d3187da3bda961caca42cf7436a816b6d
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728371"
---
# <a name="debugging-linq"></a>LINQ 디버깅
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]는 몇 가지 제한 사항이 있긴 하지만 LINQ(Language-Integrated Query) 코드의 디버깅을 지원합니다. 단계별 실행, 중단점 설정 및 디버거 창에서 결과 보기와 같은 대부분의 디버깅 기능이 LINQ 문에서 작동합니다. 이 항목에서는 LINQ 디버깅의 주요 제한 사항에 대해 설명합니다.

## <a name="viewing-linq-results"></a><a name="BKMK_ViewingLINQResults"></a> LINQ 결과 보기
 DataTips, 조사식 창 및 간략한 조사식 대화 상자를 사용하여 LINQ 명령문의 결과를 볼 수 있습니다. 소스 창을 사용할 때 포인터를 소스 창의 쿼리 위에 올려 놓으면 DataTip이 나타납니다. LINQ 변수를 복사하여 조사식 창이나 간략한 조사식 대화 상자에 붙여 넣을 수 있습니다.

 LINQ에서는 쿼리가 만들어지거나 선언될 때 계산되지 않고 쿼리가 사용될 때만 계산됩니다. 따라서 쿼리가 계산되기 전까지는 쿼리에 값이 없습니다. 쿼리 만들기 및 평가에 관한 자세한 내용은 [LINQ 쿼리 소개(C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) 또는 [첫 번째 LINQ 쿼리 작성](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query)을 참조하세요.

 쿼리 결과를 표시하려면 디버거에서 쿼리를 계산해야 합니다. 디버거에서 LINQ 쿼리 결과를 보면 이러한 암시적 계산이 수행되며, 여기에는 몇 가지 주의 사항이 있습니다.

- 쿼리를 계산할 때마다 일정 시간이 소요됩니다. 결과 노드를 확장할 때 일정 시간이 소요됩니다. 일부 쿼리의 경우 계산을 반복하면 성능이 상당히 저하될 수 있습니다.

- 쿼리를 계산할 때 데이터의 값이나 프로그램의 상태가 변경되는 예기치 않은 결과가 나타날 수 있습니다. 모든 쿼리에서 예기치 않은 결과가 나타나는 것은 아닙니다. 예기치 않은 결과가 나타나지 않고 쿼리를 안전하게 계산할 수 있는지 확인하려면 쿼리를 구현하는 코드를 이해해야 합니다.

## <a name="stepping-and-linq"></a><a name="BKMK_SteppingAndLinq"></a> 단계별 실행 및 LINQ
 LINQ 코드를 디버깅하는 경우 단계별 실행의 동작에 몇 가지 중요한 차이점이 있습니다.

### <a name="linq-to-sql"></a>LINQ to SQL
 LINQ to SQL 쿼리의 경우 디버거에서 조건자 코드를 제어할 수 없습니다. 따라서 조건자 코드를 한 단계씩 실행할 수 없습니다. 식 트리로 컴파일되는 모든 쿼리는 디버거에서 제어할 수 없는 코드를 생성합니다.

### <a name="stepping-in-visual-basic"></a>Visual Basic에서 단계별 실행
 Visual Basic 프로그램을 단계별로 실행할 때 디버거에서 쿼리 선언이 나오면 선언이 한 단계씩 실행되지 않고 전체 선언이 단일 문으로 강조 표시됩니다. 이는 쿼리가 호출될 때까지 쿼리가 계산되지 않기 때문입니다. 자세한 내용은 [Visual Basic의 LINQ 쿼리 소개](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)를 참조하세요.

 다음 예제 코드를 단계별로 실행하면 디버거에서 쿼리 선언(쿼리 생성)을 단일 문으로 강조 표시합니다.

```vb
Function MyFunction(ByVal x As Char)
    Return True
End Function

Sub Main()
    'Query creation
    Dim x = From it In "faoaoeua" _
            Where MyFunction(it) _
            Select New With {.a = it}

    ' Query execution
    For Each cur In x
        Console.WriteLine(cur.ToString())
    Next
End Sub
```

 다시 한 단계를 실행하면 디버거에서 `For Each cur In x`를 강조 표시합니다. 다음 단계에서는 `MyFunction` 함수를 단계별로 실행합니다. `MyFunction`을 단계별로 실행한 후에는 `Console.WriteLine(cur.ToSting())`으로 다시 이동합니다. 쿼리 선언의 조건자 코드는 디버거에서 계산되지만 어떠한 시점에서도 단계별로 실행되지 않습니다.

### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>단계별로 실행할 수 있도록 조건자를 함수로 대체(Visual Basic)
 디버깅을 위해 조건자 코드를 단계별로 실행해야 하는 경우 조건자를 원래 조건자 코드가 들어 있는 함수에 대한 호출로 대체할 수 있습니다. 예를 들어 다음과 같은 코드가 있다고 가정합니다.

```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt

For each item in query
      Console.WriteLine(item)
Next
```

 조건자 코드를 `IsEven`이라는 새 함수로 옮길 수 있습니다.

```vb
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt

For each item in query
      Console.WriteLine(item)
Next
...
Function IsEven(item As =Integer) as Boolean
      Return item Mod 2 = 0
End Function
```

 수정된 쿼리에서는 `IsEven`를 처리할 때마다 `items` 함수를 호출합니다. 디버거 창을 사용하여 각 항목이 지정된 조건에 맞는지 확인할 수 있고, `IsEven`의 코드를 단계별로 실행할 수 있습니다. 이 예제의 조건자는 아주 단순합니다. 그러나 복잡한 조건자를 디버깅해야 하는 경우에는 이 방법이 매우 유용할 수 있습니다.

## <a name="edit-and-continue-not-supported-for-linq"></a><a name="BKMK_EditandContinueNotSupportedforLINQ"></a> LINQ에 편집하며 계속하기가 지원되지 않음
 편집하며 계속하기는 제한 사항이 있는 LINQ 쿼리 변경을 지원합니다. 자세한 내용은 [EnC 지원 변경](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md)을 참조하세요.

## <a name="see-also"></a>참조

- [SQL 디버깅](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [디버거를 사용한 예외 관리](../debugger/managing-exceptions-with-the-debugger.md)
- [LINQ 쿼리 소개(C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Visual Basic의 LINQ 소개](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
