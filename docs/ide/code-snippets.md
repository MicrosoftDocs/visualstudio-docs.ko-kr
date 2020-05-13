---
title: 코드 조각
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: c06f9f7dc7e5a672e3fd5da3f3fc834fe223a783
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585420"
---
# <a name="code-snippets"></a>코드 조각

코드 조각은 오른쪽 클릭 메뉴(상황에 맞는 메뉴) 명령이나 바로 가기 키 조합을 사용하여 코드 파일에 삽입할 수 있는 다시 사용 가능한 작은 블록입니다. 일반적으로 `try-finally` 또는 `if-else` 블록과 같이 자주 사용되는 코드 블록을 포함하지만 전체 클래스나 메서드를 삽입하는 데 사용할 수 있습니다.

> [!NOTE]
> 이 토픽은 Windows용 Visual Studio에만 적용됩니다. Mac용 Visual Studio는 [코드 조각(Mac용 Visual Studio)](/visualstudio/mac/snippets)을 참조하세요.

코드 조각은 C#, C++, Visual Basic, XML, T-SQL 등을 비롯하여 많은 언어에 대해 사용할 수 있습니다. 언어에 대해 사용할 수 있는 모든 설치된 코드 조각을 보려면 **도구** 메뉴에서 **코드 조각 관리자**를 열거나 **Ctrl**+**K**, **Ctrl**+**B**를 누르고 맨 위에 있는 드롭다운 메뉴에서 언어를 선택합니다.

![코드 조각 관리자 대화 상자](media/code-snippets-manager.png)

코드 조각은 다음과 같은 일반적인 방법으로 액세스할 수 있습니다.

- 메뉴 모음에서 **편집** > **IntelliSense** > **조각 삽입**을 선택

- 마우스 오른쪽 단추를 클릭하거나 코드 편집기의 컨텍스트 메뉴에서 **코드 조각** > **조각 삽입**을 선택

- 키보드에서 **Ctrl**+**K**,**Ctrl**+**X**를 누름

## <a name="expansion-snippets-and-surround-with-snippets"></a>확장 조각 및 코드 감싸기 조각

Visual Studio에는 다음 두 종류의 코드 조각이 있습니다. 확장 조각은 지정된 삽입 지점에 추가되고 조각 바로 가기를 대체할 수 있으며, 코드 감싸기 조각(C# 및 C++만 해당)은 선택한 코드 블록 주위에 추가됩니다.

확장 조각의 예: C#에서 바로 가기 tryf는 try-finally 블록을 삽입하는 데 사용됩니다.

```csharp
try
{

}
finally
{

}
```

코드 창의 오른쪽 클릭 메뉴(상황에 맞는 메뉴)에서 **코드 조각 삽입**, **Visual C#** 을 차례로 클릭하여 이 코드 조각을 삽입한 다음, `tryf`를 입력하고 나서 **Tab** 키를 누릅니다. 또는 `tryf`를 입력하고 **Tab**을 두 번 누를 수 있습니다.

코드 감싸기 조각의 예: C++에서 바로 가기 `if`는 삽입 조각 또는 코드 감싸기 조각으로 사용할 수 있습니다. 코드 줄(예: `return FALSE;`)을 선택하고 **코드 감싸기** > **if**를 선택하면 해당 줄 주위에서 조각이 확장됩니다.

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>조각 대체 매개 변수

조각은 작성 중인 정확한 코드에 맞게 바꿔야 하는 자리 표시자인 대체 매개 변수를 포함할 수 있습니다. 이전 예제에서 `true`는 적절한 조건으로 바꿀 대체 매개 변수입니다. 조각에서 같은 매개 변수의 모든 인스턴스에 대해 반복해서 대체를 수행합니다.

예를 들어 Visual Basic에는 속성을 삽입하는 코드 조각이 있습니다. 조각을 삽입하려면 마우스 오른쪽 단추를 클릭하거나 Visual Basic 코드 파일의 컨텍스트 메뉴에서 **조각** > **조각 삽입**을 선택합니다. 그런 다음, **코드 패턴** > **속성, 프로시저, 이벤트** > **속성 정의**를 선택합니다.

![속성을 정의하기 위한 코드 조각 메뉴](media/code-snippets-vb-property.png)

다음 코드가 삽입됩니다.

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

`newPropertyValue`를 `m_property`로 변경하면 `newPropertyValue`의 모든 인스턴스가 변경됩니다. 속성 선언에서 `String`을 `Int`로 변경하면 set 메서드의 값도 `Int`로 변경됩니다.

## <a name="see-also"></a>참조

- [연습: 코드 조각 만들기](../ide/walkthrough-creating-a-code-snippet.md)
- [방법: 코드 조각 배포](../ide/how-to-distribute-code-snippets.md)
- [코드 조각 사용에 대한 모범 사례](../ide/best-practices-for-using-code-snippets.md)
- [코드 조각 문제 해결](../ide/troubleshooting-snippets.md)
- [C# 코드 조각](../ide/visual-csharp-code-snippets.md)
- [C++ 코드 조각](../ide/visual-cpp-code-snippets.md)
- [코드 조각 스키마 참조](../ide/code-snippets-schema-reference.md)
- [코드 조각(Mac용 Visual Studio)](/visualstudio/mac/snippets)
