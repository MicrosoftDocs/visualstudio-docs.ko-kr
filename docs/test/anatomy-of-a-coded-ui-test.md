---
title: 코딩된 UI 테스트 분석
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7100c6bb5c1dfb4c7d336ec110cf532f1f998d4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591205"
---
# <a name="anatomy-of-a-coded-ui-test"></a>코딩된 UI 테스트 분석

코딩된 UI 테스트 프로젝트에서 코딩된 UI 테스트를 만들 때는 일부 파일이 솔루션에 추가됩니다. 이 아티클에서는 파일에 대한 정보를 제공 합니다.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="contents-of-a-coded-ui-test"></a>코딩된 UI 테스트 내용

코딩된 UI 테스트를 만드는 경우 **코딩된 UI 테스트 빌더**에서 테스트 대상 사용자 인터페이스 맵과 모든 테스트에 대한 테스트 메서드, 매개 변수 및 어설션을 만듭니다. 각 테스트에 대한 클래스 파일도 만듭니다.

|파일|콘텐츠|편집 가능 여부|
|-|-|-|
|[UIMap.Designer.cs](#UIMapDesignerFile)|[선언 섹션](#UIMapDesignerFile)<br /><br /> [UIMap 클래스](#UIMapClass)(부분, 자동 생성됨)<br /><br /> [메서드](#UIMapMethods)<br /><br /> [속성](#UIMapProperties)|예|
|[UIMap.cs](#UIMapCS)|[UIMap 클래스](#UIMapCS)(부분)|yes|
|[CodedUITest1.cs](#CodedUITestCS)|[CodedUITest1 클래스](#CodedUITestCS)<br /><br /> [메서드](#CodedUITestMethods)<br /><br /> [속성](#CodedUITestProperties)|yes|
|[UIMap.uitest](#UIMapuitest)|테스트용 UI의 XML 맵|예|

### <a name="uimapdesignercs"></a><a name="UIMapDesignerFile"></a> UIMap.Designer.cs
이 파일에는 테스트를 만들 때 **코딩된 UI 테스트 빌더**에서 자동으로 생성되는 코드가 들어 있습니다. 이 파일은 테스트가 변경될 때마다 다시 생성되므로 코드를 추가하거나 수정할 수 있는 파일이 아닙니다.

#### <a name="declarations-section"></a>선언 섹션
이 섹션에는 Windows UI에 대한 다음 선언이 포함됩니다.

```csharp
using System;
using System.CodeDom.Compiler;
using System.Collections.Generic;
using System.Drawing;
using System.Text.RegularExpressions;
using System.Windows.Input;
using Microsoft.VisualStudio.TestTools.UITest.Extension;
using Microsoft.VisualStudio.TestTools.UITesting;
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;
using MouseButtons = System.Windows.Forms.MouseButtons;
```

<xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls> 네임스페이스는 Windows UI(사용자 인터페이스)용으로 포함되었습니다. 웹 페이지 UI의 경우 네임스페이스는 <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>입니다. Windows Presentation Foundation UI의 경우 네임스페이스는 <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>입니다.

#### <a name="uimap-class"></a><a name="UIMapClass"></a> UIMap 클래스
파일의 다음 섹션은 [UIMap](/previous-versions/dd580454(v=vs.140)) 클래스입니다.

```csharp
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public partial class UIMap
```

클래스 코드는 partial 클래스로 선언된 클래스에 적용되는 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> 특성으로 시작합니다. 이 파일의 모든 클래스에도 해당 특성이 적용되는 것을 확인합니다. 이 클래스에 대한 더 많은 코드를 포함할 수 있는 다른 파일은 뒷부분에 설명하는 *UIMap.cs*입니다.

생성된 `UIMap` 클래스에는 테스트를 기록할 때 지정된 각 메서드에 대한 코드가 포함됩니다.

```csharp
public void LaunchCalculator()
public void AddItems()
public void VerifyTotal()
public void CleanUp()
```

[UIMap](/previous-versions/dd580454(v=vs.140)) 클래스의 이 부분에는 메서드에 필요한 각 속성에 대해 생성된 코드도 포함됩니다.

```csharp
public virtual LaunchCalculatorParams LaunchCalculatorParams
public virtual AddItemsParams AddItemsParams
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues
public virtual CalculateItemsParams CalculateItemsParams
public virtual VerifyMathAppTotalExpectedValues
    VerifyMathAppTotalExpectedValues
public UIStartMenuWindow UIStartMenuWindow
public UIRunWindow UIRunWindow
public UICalculatorWindow UICalculatorWindow
public UIStartWindow UIStartWindow
public UIMathApplicationWindow UIMathApplicationWindow
```

##### <a name="uimap-methods"></a><a name="UIMapMethods"></a> UIMap 메서드
각 메서드는 `AddItems()` 메서드와 유사한 구조입니다. 이 내용은 보다 명확하도록 줄 바꿈과 함께 표시되는 코드 아래에서 자세히 설명합니다.

```csharp
/// <summary>
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.
/// </summary>
public void AddItems()
{
    #region Variable Declarations
    WinControl uICalculatorDialog =
        this.UICalculatorWindow.UICalculatorDialog;
    WinEdit uIItemEdit =
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;
    #endregion

    // Type '{NumPad7}' in 'Calculator' Dialog
    Keyboard.SendKeys(uICalculatorDialog,
        this.AddItemsParams.UICalculatorDialogSendKeys,
        ModifierKeys.None);

    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box
    Keyboard.SendKeys(uIItemEdit,
        this.AddItemsParams.UIItemEditSendKeys,
        ModifierKeys.None);
}
```

각 메서드 정의에 대한 요약 설명에서는 해당 메서드의 매개 변수 값에 사용할 클래스를 지시합니다. 이 경우 `AddItemsParams`UIMap.cs*파일의 뒷부분에서 정의되고* 속성에서 반환되는 값 형식이기도 한 `AddItemsParams` 클래스입니다.

메서드 코드 맨 위에는 메서드에서 사용할 UI 개체에 대한 지역 변수를 정의하는 `Variable Declarations` 영역이 있습니다.

이 메서드에서 `UIItemWindow` 및 `UIItemEdit`는 둘 다 `UICalculatorWindow`UIMap.cs*파일의 뒷부분에서 정의되는* 클래스를 사용하여 액세스할 수 있는 속성입니다.

다음은 `AddItemsParams` 개체의 속성을 사용하여 키보드에서 계산기 애플리케이션으로 텍스트를 보내는 줄입니다.

`VerifyTotal()` 메서드는 구조가 유사하며 다음과 같은 어설션 코드를 포함합니다.

```csharp
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '
Assert.AreEqual(
    this.VerifyTotalExpectedValues.UIItemEditText,
    uIItemEdit.Text);
```

Windows 계산기 애플리케이션의 개발자가 공개적으로 사용할 수 있는 컨트롤 이름을 제공하지 않으므로 텍스트 상자 이름은 알 수 없음으로 나열됩니다. 실제 값이 예상 값과 같지 않은 경우 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> 메서드가 실패하여 테스트에 실패합니다. 또한 예상 값은 소수점 뒤에 공백을 포함합니다. 이 특정 테스트의 기능을 수정해야 하는 경우 해당 소수점과 공백을 허용해야 합니다.

##### <a name="uimap-properties"></a><a name="UIMapProperties"></a> UIMap 속성
각 속성에 대한 코드도 클래스 전체에서 표준적입니다. `AddItemsParams` 속성에 대한 다음 코드는 `AddItems()` 메서드에서 사용됩니다.

```csharp
public virtual AddItemsParams AddItemsParams
{
    get
    {
        if ((this.mAddItemsParams == null))
        {
            this.mAddItemsParams = new AddItemsParams();
        }
        return this.mAddItemsParams;
    }
}
```

속성은 값을 반환하기 전에 `mAddItemsParams`라는 전용 지역 변수를 사용하여 보유합니다. 반환하는 개체의 속성 이름과 클래스 이름은 같습니다. 클래스는 *UIMap.cs* 파일의 뒷부분에서 정의됩니다.

속성에서 반환되는 각 클래스는 구조가 유사합니다. 다음은 `AddItemsParams` 클래스입니다.

```csharp
/// <summary>
/// Parameters to be passed into 'AddItems'
/// </summary>
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public class AddItemsParams
{
    #region Fields
    /// <summary>
    /// Type '{NumPad7}' in 'Calculator' Dialog
    /// </summary>
    public string UICalculatorDialogSendKeys = "{NumPad7}";

    /// <summary>
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box
    /// </summary>
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";
    #endregion
}
```

*UIMap.cs* 파일의 모든 클래스와 마찬가지로, 이 클래스는 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>로 시작합니다. 이 작은 클래스에는 앞에서 설명한 `Fields` 메서드에서 사용되는 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> 메서드의 매개 변수로 사용할 문자열을 정의하는 `UIMap.AddItems()` 영역이 있습니다. 이러한 매개 변수가 사용되는 메서드를 호출하기 전에 해당 문자열 필드의 값을 바꾸는 코드를 작성할 수 있습니다.

### <a name="uimapcs"></a><a name="UIMapCS"></a> UIMap.cs
기본적으로 이 파일은 메서드나 속성이 없는 partial `UIMap` 클래스를 포함합니다.

#### <a name="uimap-class"></a>UIMap 클래스
여기서 사용자 지정 코드를 만들어 [UIMap](/previous-versions/dd580454(v=vs.140)) 클래스의 기능을 확장할 수 있습니다. 이 파일에서 만드는 코드는 테스트를 수정할 때마다 **코딩된 UI 테스트 빌더**에서 덮어쓰지 않습니다.

[UIMap](/previous-versions/dd580454(v=vs.140))의 모든 부분에서 [UIMap](/previous-versions/dd580454(v=vs.140)) 클래스의 다른 부분에 있는 메서드와 속성을 사용할 수 있습니다.

### <a name="codeduitest1cs"></a><a name="CodedUITestCS"></a> CodedUITest1.cs
이 파일은 **코딩된 UI 테스트 빌더**에서 생성되지만 테스트를 수정할 때마다 다시 생성되지 않으므로 이 파일의 코드를 수정할 수 있습니다. 파일 이름은 테스트를 만들 때 지정한 테스트 이름에서 생성됩니다.

#### <a name="codeduitest1-class"></a>CodedUITest1 클래스

기본적으로 이 파일은 하나의 클래스에 대한 정의만 포함합니다.

```csharp
[CodedUITest]
public class CodedUITest1
```

[CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))가 클래스에 자동으로 적용되어 테스트 프레임워크에서 해당 클래스를 테스트 확장으로 인식할 수 있게 합니다. 또한 partial 클래스가 아닙니다. 모든 클래스 코드가 이 파일에 포함됩니다.

##### <a name="codeduitest1-properties"></a><a name="CodedUITestProperties"></a> CodedUITest1 속성

클래스는 파일 맨 아래에 있는 두 개의 기본 속성을 포함합니다. 수정하지 마십시오.

```csharp
/// <summary>
/// Gets or sets the test context which provides
/// information about and functionality for the current test run.
///</summary>
public TestContext TestContext
public UIMap UIMap
```

##### <a name="codeduitest1-methods"></a><a name="CodedUITestMethods"></a> CodedUITest1 메서드
기본적으로 클래스는 하나의 메서드만 포함합니다.

```csharp
public void CodedUITestMethod1()
```

이 메서드는 테스트를 기록할 때 지정한 각 `UIMap` 메서드를 호출합니다. 해당 메서드는 [UIMap 클래스](#UIMapClass)에 대한 섹션에서 설명합니다.

주석 처리가 제거된 경우 `Additional test attributes`라는 영역은 두 개의 선택적 메서드를 포함합니다.

```csharp
// Use TestInitialize to run code before running each test
[TestInitialize()]
public void MyTestInitialize()
{
    // To generate code for this test, select "Generate Code for Coded
    // UI Test" from the shortcut menu and select one of the menu items.
    // For more information on generated code, see
    // http://go.microsoft.com/fwlink/?LinkId=179463

    // You could move this line from the CodedUITestMethod1() method
    this.UIMap.LaunchCalculator();
}

// Use TestCleanup to run code after each test has run
[TestCleanup()]
public void MyTestCleanup()
{
    // To generate code for this test, select "Generate Code for Coded
    // UI Test" from the shortcut menu and select one of the menu items.
    // For more information on generated code, see
    // http://go.microsoft.com/fwlink/?LinkId=179463

    // You could move this line from the CodedUITestMethod1() method
    this.UIMap.CloseCalculator();
}
```

`MyTestInitialize()` 메서드에는 다른 테스트 메서드보다 먼저 이 메서드를 호출하도록 테스트 프레임워크에 지시하는 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>가 적용되어 있습니다. 마찬가지로, `MyTestCleanup()` 메서드에는 다른 테스트 메서드가 모두 호출된 후 이 메서드를 호출하도록 테스트 프레임워크에 지시하는 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>가 적용되어 있습니다. 이러한 메서드 사용은 선택 사항입니다. 이 테스트를 위해 `UIMap.LaunchCalculator()`에서 `MyTestInitialize()` 메서드를 호출할 수 있고, `UIMap.CloseCalculator()` 대신 `MyTestCleanup()`에서 `CodedUITest1Method1()` 메서드를 호출할 수 있습니다.

[CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))를 사용하여 이 클래스에 더 많은 메서드를 추가하는 경우 테스트 프레임워크에서 테스트의 일부로 각 메서드를 호출합니다.

### <a name="uimapuitest"></a><a name="UIMapuitest"></a> UIMap.uitest
코딩된 UI 테스트 기록의 구조 및 모든 해당 부분을 나타내는 XML 파일입니다. 여기에는 작업 및 클래스와 해당 클래스의 메서드 및 속성도 포함됩니다. [UIMap.Designer.cs](#UIMapDesignerFile) 파일은 코딩된 UI 빌더에서 테스트 구조를 재현하기 위해 생성되고, 테스트 프레임워크에 대한 연결을 제공하는 코드를 포함합니다.

*UIMap.uitest* 파일은 직접 편집할 수 없습니다. 그러나 코딩된 UI 빌더를 사용하여 테스트를 수정할 수 있으며, *UIMap.uitest* 파일과 [*UIMap.Designer.cs*](#UIMapDesignerFile) 파일이 자동으로 수정됩니다.

## <a name="see-also"></a>참고 항목

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>
- <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>
- [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>
- [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)
- [코딩된 UI 테스트 만들기](../test/use-ui-automation-to-test-your-code.md)
- [코딩된 UI 테스트에 대한 모범 사례](../test/best-practices-for-coded-ui-tests.md)
- [여러 UI 맵이 포함된 대형 애플리케이션 테스트](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [코딩된 UI 테스트 및 작업 기록에 지원되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
