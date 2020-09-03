---
title: 무명 메서드 및 코드 분석 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49da7d5e7f6a7731a708accb3d52fb6383ff1017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652218"
---
# <a name="anonymous-methods-and-code-analysis"></a>무명 메서드 및 코드 분석
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*무명 메서드* 는 이름이 없는 메서드입니다. 무명 메서드는 코드 블록을 대리자 매개 변수로 전달 하는 데 가장 자주 사용 됩니다.

 이 항목에서는 코드 분석에서 익명 메서드와 관련 된 경고 및 메트릭을 처리 하는 방법에 대해 설명 합니다.

## <a name="anonymous-methods-declared-in-a-member"></a>멤버에 선언 된 무명 메서드
 메서드 또는 접근자와 같이 멤버에 선언 된 무명 메서드에 대 한 경고 및 메트릭은 메서드를 선언 하는 멤버와 연결 됩니다. 메서드를 호출 하는 멤버와 연결 되지 않습니다.

 예를 들어 다음 클래스에서 **anonymousMethod** 선언에 있는 모든 경고는 **Method1** 에 대해 발생 하 고 **Method2**는 그렇지 않습니다.

```vb

      Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass

    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End SubSub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    void Method1()
    {
        Delegate anonymousMethod = delegate()
        {
          Console.WriteLine("");
        }
        Method2(anonymousMethod);
    }

    void Method2(Delegate anonymousMethod)
    {
        anonymousMethod();
    }
}
```

## <a name="inline-anonymous-methods"></a>인라인 무명 메서드
 필드에 대 한 인라인 할당으로 선언 된 무명 메서드에 대 한 경고 및 메트릭은 생성자와 연결 됩니다. 필드가 (에서)로 선언 된 경우 `static` `Shared` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 경고 및 메트릭은 클래스 생성자와 연결 되 고, 그렇지 않으면 인스턴스 생성자와 연결 됩니다.

 예를 들어 다음 클래스에서 **anonymousMethod1** 선언에 있는 모든 경고는 **클래스**의 암시적으로 생성 된 기본 생성자에 대해 발생 합니다. 반면 **anonymousMethod2** 에 있는 해당 클래스는 암시적으로 생성 된 클래스 생성자에 대해 적용 됩니다.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5

Sub Method1()
    anonymousMethod1(10)
    anonymousMethod2(10)
End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    Delegate anonymousMethod1 = delegate()
    {
       Console.WriteLine("");
    }

    static Delegate anonymousMethod2 = delegate()
    {
       Console.WriteLine("");
    }

    void Method()
    {
       anonymousMethod1();
       anonymousMethod2();
    }
}
```

 클래스에는 여러 생성자가 있는 필드에 값을 할당 하는 인라인 무명 메서드가 포함 될 수 있습니다. 이 경우 해당 생성자가 동일한 클래스의 다른 생성자에 연결 되지 않으면 경고 및 메트릭이 모든 생성자와 연결 됩니다.

 예를 들어 다음 클래스에서 **anonymousMethod** 선언에 있는 모든 경고는 클래스 ( **int)** 및 클래스 ( **문자열)** 에 대해 발생 하지만 **클래스 ()** 에 대해서는 발생 하지 않아야 합니다.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass

Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)
value > 5

SubNew()
    New(CStr(Nothing))
End SubSub New(ByVal a As Integer)
End SubSub New(ByVal a As String)
End SubEnd Class
```

```csharp

      delegate void Delegate();
class Class
{
    Delegate anonymousMethod = delegate()
    {
       Console.WriteLine("");
    }

    Class() : this((string)null)
    {
    }

    Class(int a)
    {
    }

    Class(string a)
    {
    }
}
```

 이는 예기치 않은 것 처럼 보일 수 있지만 컴파일러에서 다른 생성자에 연결 되지 않은 모든 생성자에 대 한 고유한 메서드를 출력 하기 때문에 이러한 상황이 발생 합니다. 이 동작으로 인해 **anonymousMethod** 에서 발생 하는 모든 위반은 별도로 표시 되지 않아야 합니다. 즉, 새 생성자를 도입 하는 경우 이전에 **클래스 (int)** 와 **클래스 (문자열)** 에 대해 이전에 표시 되지 않은 경고가 새 생성자에 대해서도 표시 되지 않아야 함을 의미 합니다.

 다음 두 가지 방법 중 하나로이 문제를 해결할 수 있습니다. 모든 생성자가 연결 하는 공용 생성자에서 **anonymousMethod** 를 선언할 수 있습니다. 또는 모든 생성자가 호출 하는 초기화 메서드에서 선언할 수 있습니다.

## <a name="see-also"></a>관련 항목
 [관리 코드 품질 분석](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
