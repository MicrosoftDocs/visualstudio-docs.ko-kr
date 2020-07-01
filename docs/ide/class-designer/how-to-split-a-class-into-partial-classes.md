---
title: '방법: 클래스를 부분 클래스로 분할(클래스 디자이너)'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 623ac5269b78faee9f68580f0803576ad56c1233
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770038"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>방법: 클래스 디자이너에서 클래스를 부분 클래스로 분할

`partial` 키워드(Visual Basic에서는 `Partial`)를 사용하여 여러 선언에서 클래스 또는 구조체의 선언을 나눌 수 있습니다. 원하는 만큼 Partial 선언을 사용할 수 있습니다.

선언은 하나 또는 여러 소스 파일에 있을 수 있습니다. 모든 선언이 동일한 어셈블리와 동일한 네임스페이스에 있어야 합니다.

Partial 클래스는 여러 상황에서 유용합니다. 예를 들어 대규모 프로젝트에서 클래스를 여러 파일로 구분하면 1 초과 프로그래머가 동시에 프로젝트에서 작업을 할 수 있습니다. Visual Studio에서 생성된 코드로 작업하는 경우 소스 파일을 다시 만들 필요 없이 클래스를 변경할 수 있습니다. Visual Studio에서 생성된 코드의 예로는 Windows Forms 및 웹 서비스 래퍼 코드가 있습니다. 따라서 Visual Studio에서 만든 파일을 수정하지 않고도 자동 생성된 클래스를 사용하는 코드를 만들 수 있습니다.

partial 메서드는 두 가지 종류가 있습니다. C#에서는 선언(declaring) 및 구현(implementing), Visual Basic에서는 선언(declaration) 및 구현(implementation)이라고 합니다.

**클래스 디자이너**에서는 partial 클래스 및 메서드를 지원합니다. 클래스 다이어그램의 형식 도형은 partial 클래스의 단일 선언 위치를 가리킵니다. Partial 클래스가 여러 파일에 정의된 경우 **속성** 창에서 **새 멤버 위치** 속성을 설정하여 **클래스 디자이너**가 사용할 선언 위치를 지정할 수 있습니다. 즉, 클래스 도형을 두 번 클릭하면 **클래스 디자이너**가 **새 멤버 위치** 속성으로 식별된 클래스 선언이 있는 소스 파일로 이동합니다. 클래스 도형에서 partial 메서드를 두 번 클릭하면 **클래스 디자이너**가 partial 메서드 선언으로 이동합니다. 또한, **속성** 창의 **파일 이름** 속성이 선언 위치를 가리킵니다. partial 클래스의 경우 **파일 이름**은 해당 클래스의 선언 및 구현 코드가 포함된 파일을 모두 나열합니다. 그러나 partial 메서드의 경우에는 **파일 이름**이 partial 메서드 선언이 포함된 파일만 나열합니다.

다음 예제에서는 클래스 `Employee`의 정의를 두 개의 선언으로 분할합니다(여기서 각 선언은 서로 다른 프로시저를 정의함). 이 예제에서 두 개의 partial 정의는 하나의 소스 파일에 있거나 두 개의 서로 다른 소스 파일에 있을 수 있습니다.

> [!NOTE]
> Visual Basic에서는 부분 클래스 정의를 사용하여 Visual Studio 생성 코드와 사용자 작성 코드를 구분합니다. 코드는 별도의 소스 파일로 구분됩니다. 예를 들어, **Windows Form 디자이너**에서는 `Form`과 같은 컨트롤에 대해 partial 클래스를 정의합니다. 이런 컨트롤에서 생성된 코드를 수정해서는 안 됩니다.

Visual Basic의 부분 형식(Partial Type)에 대한 자세한 내용은 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)을 참조하세요.

## <a name="example"></a>예제

클래스 정의를 분할하려면 다음 예제와 같이 `partial` 키워드(Visual Basic의 `Partial`)를 사용합니다.

```csharp
// First part of class definition.
public partial class Employee
{
    public void CalculateWorkHours()
    {
    }
}

// Second part of class definition.
public partial class Employee
{
    public void CalculateTaxes()
    {
    }
}
```

```vb
' First part of class definition.
Partial Public Class Employee
    Public Sub CalculateWorkHours()
    End Sub
End Class

' Second part of class definition.
Partial Public Class Employee
    Public Sub CalculateTaxes()
    End Sub
End Class
```

## <a name="see-also"></a>참조

- [Partial 클래스 및 메서드](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [partial(형식)(C# 참조)](/dotnet/csharp/language-reference/keywords/partial-type)
- [partial(메서드)(C# 참조)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial(Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)
