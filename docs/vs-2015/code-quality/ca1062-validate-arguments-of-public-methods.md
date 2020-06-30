---
title: 'CA1062: public 메서드의 인수 유효성을 검사 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 377906675d70a712f8ca72b0b6e4d8a6864c1fbc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533239"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: public 메서드의 인수에 대한 유효성을 검사하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|범주|Microsoft 디자인|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 메서드는 해당 인수가 (Visual Basic) 인지 여부를 확인 하지 않고 해당 참조 인수 중 하나를 역참조 `null` `Nothing` 합니다.

## <a name="rule-description"></a>규칙 설명
 외부에서 볼 수 있는 메서드에 전달 되는 모든 참조 인수를 확인 해야 `null` 합니다. 적절 한 경우 <xref:System.ArgumentNullException> 인수가 인 경우을 throw 합니다 `null` .

 Public 또는 protected로 선언 되기 때문에 알 수 없는 어셈블리에서 메서드를 호출할 수 있는 경우 메서드의 모든 매개 변수 유효성을 검사 해야 합니다. 알려진 어셈블리만 호출 하도록 메서드를 디자인 한 경우 메서드를 internal로 설정 하 고 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 메서드를 포함 하는 어셈블리에 특성을 적용 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면에 대해 각 참조 인수의 유효성을 검사 `null` 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 역참조 된 매개 변수가 함수의 다른 메서드 호출에서 유효성을 검사 한 것으로 확인 되는 경우이 규칙에서 경고를 표시 하지 않을 수 있습니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 메서드와 규칙을 충족 하는 메서드를 보여 줍니다.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>예제
 에서 [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] 이 규칙은 유효성 검사를 수행 하는 다른 메서드에 매개 변수가 전달 되 고 있음을 감지 하지 않습니다.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>예제
 참조 개체인 필드 또는 속성을 채우는 복사 생성자도 CA1062 규칙을 위반할 수 있습니다. 복사 생성자에 전달 된 복사 된 개체가 `null` (Visual Basic) 일 수 있기 때문에 위반이 발생 합니다 `Nothing` . 위반 문제를 해결 하려면 정적 (Visual Basic에서 공유) 메서드를 사용 하 여 복사한 개체가 null이 아닌 지 확인 합니다.

 다음 `Person` 클래스 예제에서 `other` 복사 생성자에 전달 되는 개체는 `Person` 일 수 있습니다 `null` .

```

public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>예제
 다음 수정 된 `Person` 예제에서는 `other` 복사 생성자에 전달 된 개체가 먼저 메서드에서 null 인지 확인 `PassThroughNonNull` 합니다.

```
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException("person");
        return person;
    }
}
```
