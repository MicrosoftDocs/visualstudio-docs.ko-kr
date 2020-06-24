---
title: shim을 사용하여 단위 테스트를 위한 애플리케이션 격리
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 0f7d2f993891a4adfa9217357fbdb1a95e10b637
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289302"
---
# <a name="use-shims-to-isolate-your-app-for-unit-testing"></a>shim을 사용하여 유닛 테스트를 위한 앱 격리

**shim 형식**은 Microsoft Fakes 프레임워크가 환경에서 테스트 대상 구성 요소를 격리할 수 있도록 하기 위해 사용하는 두 기술 중 하나입니다. shim은 특정 메서드 호출을 테스트의 일부로 작성하는 코드로 우회합니다. 대부분의 메서드는 외부 조건에 따라 다른 결과를 반환하지만 shim은 테스트에 의해 제어되며 모든 호출에서 일관된 결과를 반환할 수 있습니다. 이렇게 하면 테스트를 더 쉽게 작성할 수 있습니다.

*shim*을 사용하여 솔루션의 일부가 아닌 코드를 어셈블리에서 격리할 수 있습니다. 솔루션의 구성 요소를 서로 격리하려면 *스텁*을 사용하세요.

개요 및 “빠른 시작” 가이드를 보려면 [Microsoft Fakes를 사용하여 테스트 대상 코드 격리](../test/isolating-code-under-test-with-microsoft-fakes.md)를 참조하세요.

**요구 사항**

- Visual Studio Enterprise
- .NET Framework 프로젝트

> [!NOTE]
> .NET Standard 프로젝트는 지원되지 않습니다.

## <a name="example-the-y2k-bug"></a>예: Y2K 버그

2000년 1월 1일에 예외를 throw하는 메서드를 살펴봅니다.

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

이 메서드를 테스트하는 경우 프로그램이 환경에 종속된 비결정적인 메서드인 컴퓨터 시계에 종속된 메서드 `DateTime.Now`에 종속되기 때문에 문제가 발생합니다. 또한 `DateTime.Now`는 정적 속성이므로 여기서 스텁 형식을 사용할 수 없습니다. 이 문제는 단위 테스트의 격리 문제를 나타냅니다. 직접 데이터베이스 API를 호출하고, 웹 서비스와 통신하는 등의 프로그램은 해당 논리가 환경에 종속되기 때문에 단위 테스트를 수행하기 어렵습니다.

이런 경우 shim 형식을 사용해야 합니다. shim 형식은 .NET 메서드를 사용자 정의 대리자로 우회하는 메커니즘을 제공합니다. shim 형식은 Fakes 생성기에서 코드로 생성되며 shim 형식이라는 대리자를 사용하여 새 메서드 구현을 지정합니다.

다음 테스트에서는 shim 형식 `ShimDateTime`을 사용하여 DateTime.Now의 사용자 지정 구현을 제공하는 방법을 보여 줍니다.

```csharp
//unit test code
// create a ShimsContext cleans up shims
using (ShimsContext.Create()) {
    // hook delegate to the shim method to redirect DateTime.Now
    // to return January 1st of 2000
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);
    Y2KChecker.Check();
}
```

## <a name="how-to-use-shims"></a>shim 사용 방법

첫 번째로 Fakes 어셈블리를 추가합니다.

1. **솔루션 탐색기**에서 단위 테스트 프로젝트의 **참조** 노드를 확장합니다.

   - Visual Basic에서 작업하는 경우 **참조** 노드를 보기 위해 **솔루션 탐색기** 도구 모음에서 **모든 파일 표시**를 선택합니다.

2. shim을 만들 클래스 정의가 포함된 어셈블리를 선택합니다. 예를 들어 **날짜/시간**을 shim하려면 **System.dll**을 선택합니다.

3. 바로 가기 메뉴에서 **Fakes 어셈블리 추가**를 선택합니다.

### <a name="use-shimscontext"></a>ShimsContext 사용

단위 테스트 프레임워크에서 shim 형식을 사용하는 경우 테스트 코드를 `ShimsContext`에 래핑하여 shim의 수명을 제어합니다. 그렇게 하지 않으면 AppDomain이 종료될 때까지 shim이 지속됩니다. `ShimsContext`를 만드는 가장 쉬운 방법은 다음 코드와 같이 정적 `Create()` 메서드를 사용하는 것입니다.

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

각 shim 컨텍스트를 올바르게 삭제하는 것이 중요합니다. 경험상, `using` 문 내에서 `ShimsContext.Create`를 호출하여 등록된 shim이 제대로 지워지도록 합니다. 예를 들어 항상 2000년 1월 1일을 반환하는 대리자로 `DateTime.Now` 메서드를 대체하는 테스트 메서드에 대해 shim을 등록할 수 있습니다. 테스트 메서드에서 등록된 shim을 지우지 않으면 테스트 실행의 나머지 부분에서 항상 2000년 1월 1일을 `DateTime.Now` 값으로 반환합니다. 이 결과는 놀라움과 혼동을 줄 수 있습니다.

### <a name="write-a-test-with-shims"></a>shim을 사용하여 테스트 작성

테스트 코드에서 모조할 메서드에 대해 *우회*를 삽입합니다. 다음은 그 예입니다.

```csharp
[TestClass]
public class TestClass1
{
        [TestMethod]
        public void TestCurrentYear()
        {
            int fixedYear = 2000;

            using (ShimsContext.Create())
            {
              // Arrange:
                // Detour DateTime.Now to return a fixed date:
                System.Fakes.ShimDateTime.NowGet =
                () =>
                { return new DateTime(fixedYear, 1, 1); };

                // Instantiate the component under test:
                var componentUnderTest = new MyComponent();

              // Act:
                int year = componentUnderTest.GetTheCurrentYear();

              // Assert:
                // This will always be true if the component is working:
                Assert.AreEqual(fixedYear, year);
            }
        }
}
```

```vb
<TestClass()> _
Public Class TestClass1
    <TestMethod()> _
    Public Sub TestCurrentYear()
        Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()
            Dim fixedYear As Integer = 2000
            ' Arrange:
            ' Detour DateTime.Now to return a fixed date:
            System.Fakes.ShimDateTime.NowGet = _
                Function() As DateTime
                    Return New DateTime(fixedYear, 1, 1)
                End Function

            ' Instantiate the component under test:
            Dim componentUnderTest = New MyComponent()
            ' Act:
            Dim year As Integer = componentUnderTest.GetTheCurrentYear
            ' Assert:
            ' This will always be true if the component is working:
            Assert.AreEqual(fixedYear, year)
        End Using
    End Sub
End Class
```

shim 클래스 이름은 원래 형식 이름에 `Fakes.Shim` 접두사를 추가하여 구성합니다.

shim은 테스트 대상 애플리케이션의 코드에 *우회*를 삽입하여 작동합니다. 원래 메서드가 호출될 때마다 Fakes 시스템은 실제 메서드를 호출하는 대신 shim 코드가 호출되도록 우회를 수행합니다.

우회는 런타임에 생성 및 삭제됩니다. 항상 `ShimsContext`의 수명 내에서 우회를 만들어야 합니다. 삭제하면 활성화된 동안 만든 shim이 모두 제거됩니다. 이 작업은 `using` 문 내에서 수행하는 것이 가장 좋습니다.

Fakes 네임스페이스가 없다는 빌드 오류가 표시될 수도 있습니다. 다른 컴파일 오류가 있을 때 이 오류가 나타나는 경우도 있습니다. 다른 오류를 수정하면 오류가 사라집니다.

## <a name="shims-for-different-kinds-of-methods"></a>다양한 메서드에 대한 shim

shim 형식을 사용하여 정적 메서드 또는 비가상 메서드를 포함하는 .NET 메서드를 사용자 고유의 대리자로 대체할 수 있습니다.

### <a name="static-methods"></a>정적 메서드

정적 메서드에 shim을 연결하는 속성은 shim 형식에 배치됩니다. 각 속성에는 대상 메서드에 대리자를 연결하는 데 사용할 수 있는 setter만 있습니다. 예를 들어 정적 메서드 `MyMethod`를 포함하는 `MyClass` 클래스가 있다고 가정합니다.

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

항상 5를 반환하는 shim을 `MyMethod`에 연결할 수 있습니다.

```csharp
// unit test code
ShimMyClass.MyMethod = () => 5;
```

### <a name="instance-methods-for-all-instances"></a>모든 인스턴스에 대한 인스턴스 메서드

정적 메서드와 마찬가지로, 모든 인스턴스에 대해 인스턴스 메서드를 shim할 수 있습니다. 이러한 shim을 연결할 속성은 혼동을 피하기 위해 AllInstances라는 중첩된 형식에 배치됩니다. 예를 들어 인스턴스 메서드 `MyMethod`를 포함하는 `MyClass` 클래스가 있다고 가정합니다.

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

인스턴스에 관계없이 항상 5를 반환하는 shim을 `MyMethod`에 연결할 수 있습니다.

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

ShimMyClass의 생성된 형식 구조는 다음 코드와 같습니다.

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public static class AllInstances {
        public static Func<MyClass, int>MyMethod {
            set {
                ...
            }
        }
    }
}
```

이 경우 Fakes는 런타임 인스턴스를 대리자의 첫 번째 인수로 전달합니다.

### <a name="instance-methods-for-one-runtime-instance"></a>단일 런타임 인스턴스에 대한 인스턴스 메서드

호출 수신자에 따라 다른 대리자가 인스턴스 메서드를 shim할 수도 있습니다. 이렇게 하면 동일한 인스턴스 메서드가 형식 인스턴스별로 다른 동작을 수행할 수 있습니다. 이러한 shim을 설정하는 속성은 shim 형식 자체의 인스턴스 메서드입니다. 인스턴스화된 각 shim 형식은 shim된 형식의 원시 인스턴스에도 연결됩니다.

예를 들어 인스턴스 메서드 `MyMethod`를 포함하는 `MyClass` 클래스가 있다고 가정합니다.

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

첫 번째 shim 형식은 항상 5를 반환하고 두 번째 shim 형식은 항상 10을 반환하도록 MyMethod의 shim 형식 두 개를 설정할 수 있습니다.

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

ShimMyClass의 생성된 형식 구조는 다음 코드와 같습니다.

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public Func<int> MyMethod {
        set {
            ...
        }
    }
    public MyClass Instance {
        get {
            ...
        }
    }
}
```

shim된 실제 형식 인스턴스는 Instance 속성을 통해 액세스할 수 있습니다.

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

shim 형식에는 shim된 형식으로의 암시적 변환도 있으므로 일반적으로 shim 형식을 있는 그대로 사용할 수 있습니다.

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime instance
```

### <a name="constructors"></a>생성자

이후 개체에 shim 형식을 연결하기 위해 생성자를 shim할 수도 있습니다. 각 생성자는 shim 형식에서 정적 메서드 Constructor로 노출됩니다. 예를 들어 정수를 사용하는 생성자를 포함하는 `MyClass` 클래스가 있다고 가정합니다.

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Value getter를 호출할 때 생성자의 값에 관계없이 이후의 모든 인스턴스가 -5를 반환하도록 생성자의 shim 형식을 설정합니다.

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

각 shim 형식이 두 개의 생성자를 노출합니다. 새 인스턴스가 필요한 경우 기본 생성자를 사용해야 하고, shim된 인스턴스를 인수로 사용하는 생성자는 생성자 shim에서만 사용해야 합니다.

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

ShimMyClass의 생성된 형식 구조는 다음 코드와 유사합니다.

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass>
{
    public static Action<MyClass, int> ConstructorInt32 {
        set {
            ...
        }
    }

    public ShimMyClass() { }
    public ShimMyClass(MyClass instance) : base(instance) { }
    ...
}
```

### <a name="base-members"></a>기본 멤버

기본 형식에 대한 shim을 만들고 기본 shim 클래스의 생성자에 자식 인스턴스를 매개 변수로 전달하여 기본 멤버의 shim 속성에 액세스할 수 있습니다.

예를 들어 인스턴스 메서드 `MyMethod` 및 하위 형식 `MyChild`를 포함하는 `MyBase` 클래스가 있다고 가정합니다.

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

새로운 `ShimMyBase` shim을 만들어 `MyBase`의 shim을 설정할 수 있습니다.

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

기본 shim 생성자에 매개 변수로 전달하면 자식 shim 형식이 암시적으로 자식 인스턴스로 변환됩니다.

ShimMyChild 및 ShimMyBase의 생성된 형식 구조는 다음 코드와 유사합니다.

```csharp
// Fakes generated code
public class ShimMyChild : ShimBase<MyChild> {
    public ShimMyChild() { }
    public ShimMyChild(Child child)
        : base(child) { }
}
public class ShimMyBase : ShimBase<MyBase> {
    public ShimMyBase(Base target) { }
    public Func<int> MyMethod
    { set { ... } }
}
```

### <a name="static-constructors"></a>정적 생성자

shim 형식은 형식의 정적 생성자를 shim하는 정적 메서드 `StaticConstructor`를 노출합니다. 정적 생성자는 한 번만 실행되므로 형식의 멤버에 액세스하기 전에 shim이 구성되는지 확인해야 합니다.

### <a name="finalizers"></a>종료자

종료자는 Fakes에서 지원되지 않습니다.

### <a name="private-methods"></a>프라이빗 메서드

Fakes 코드 생성기는 서명에 표시되는 형식, 즉 표시되는 매개 변수 형식 및 반환 형식만 있는 전용 메서드에 대해 shim 속성을 만듭니다.

### <a name="binding-interfaces"></a>바인딩 인터페이스

shim된 형식이 인터페이스를 구현하는 경우 코드 생성기에서 해당 인터페이스의 모든 멤버를 한 번에 바인딩할 수 있는 메서드를 내보냅니다.

예를 들어 `IEnumerable<int>`를 구현하는 `MyClass` 클래스가 있다고 가정합니다.

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}
```

Bind 메서드를 호출하여 MyClass에서 `IEnumerable<int>`의 구현을 shim할 수 있습니다.

```csharp
// unit test code
var shimMyClass = new ShimMyClass();
shimMyClass.Bind(new List<int> { 1, 2, 3 });
```

ShimMyClass의 생성된 형식 구조는 다음 코드와 유사합니다.

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public ShimMyClass Bind(IEnumerable<int> target) {
        ...
    }
}
```

## <a name="change-the-default-behavior"></a>기본 동작 변경

생성된 각 shim 형식에는 `IShimBehavior` 인터페이스의 인스턴스가 `ShimBase<T>.InstanceBehavior` 속성을 통해 포함됩니다. 클라이언트가 명시적으로 shim되지 않은 인스턴스 멤버를 호출할 때마다 동작이 사용됩니다.

동작이 명시적으로 설정되지 않은 경우 정적 `ShimsBehaviors.Current` 속성에서 반환한 인스턴스를 사용합니다. 기본적으로 이 속성은 `NotImplementedException` 예외를 throw하는 동작을 반환합니다.

이 동작은 shim 인스턴스의 `InstanceBehavior` 속성을 설정하여 언제든지 변경할 수 있습니다. 예를 들어 다음 코드 조각은 아무 작업을 하지 않거나 반환 형식의 기본값, 즉 `default(T)`를 반환하는 동작으로 shim을 변경합니다.

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;
```

정적 `ShimsBehaviors.Current` 속성을 설정하여 `InstanceBehavior` 속성이 명시적으로 설정되지 않은 shim된 모든 인스턴스에 대해 전역적으로 동작을 변경할 수도 있습니다.

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimsBehaviors.Current = ShimsBehaviors.DefaultValue;
```

## <a name="detect-environment-accesses"></a>환경 액세스 검색

해당 shim 형식의 정적 속성 `Behavior`에 `ShimsBehaviors.NotImplemented` 동작을 할당하면 정적 메서드를 포함하여 특정 형식의 모든 메서드에 동작을 연결할 수 있습니다.

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

## <a name="concurrency"></a>동시성

shim 형식은 AppDomain의 모든 스레드에 적용되며 스레드 선호도가 없습니다. 동시 실행을 지원하는 테스트 실행을 사용하려는 경우 중요한 사실입니다. shim 형식과 관련된 테스트는 동시에 실행할 수 없습니다. 이 속성은 Fakes 런타임에 의해 적용되지 않습니다.

## <a name="call-the-original-method-from-the-shim-method"></a>shim 메서드에서 원래 메서드 호출

메서드에 전달된 파일 이름의 유효성을 검사한 후 파일 시스템에 텍스트를 작성하려 한다고 가정합니다. 이 경우 shim 메서드 중에 원래 메서드를 호출합니다.

이 문제를 해결하는 첫 번째 방법은 다음 코드와 같이 대리자 및 `ShimsContext.ExecuteWithoutShims()`를 사용하여 원래 메서드 호출을 래핑하는 것입니다.

```csharp
// unit test code
ShimFile.WriteAllTextStringString = (fileName, content) => {
  ShimsContext.ExecuteWithoutShims(() => {

      Console.WriteLine("enter");
      File.WriteAllText(fileName, content);
      Console.WriteLine("leave");
  });
};
```

또 다른 방법은 shim을 null로 설정하고 원래 메서드를 호출한 다음 shim을 복원하는 것입니다.

```csharp
// unit test code
ShimsDelegates.Action<string, string> shim = null;
shim = (fileName, content) => {
  try {
    Console.WriteLine("enter");
    // remove shim in order to call original method
    ShimFile.WriteAllTextStringString = null;
    File.WriteAllText(fileName, content);
  }
  finally
  {
    // restore shim
    ShimFile.WriteAllTextStringString = shim;
    Console.WriteLine("leave");
  }
};
// initialize the shim
ShimFile.WriteAllTextStringString = shim;
```

## <a name="systemenvironment"></a>System.Environment

<xref:System.Environment?displayProperty=fullName>를 shim하려면 **Assembly** 요소 뒤에 있는 mscorlib.fakes 파일에 다음 콘텐츠를 추가합니다.

```xml
<ShimGeneration>
    <Add FullName="System.Environment"/>
</ShimGeneration>
```

솔루션을 다시 빌드한 후 <xref:System.Environment?displayProperty=fullName> 클래스의 메서드 및 속성의 shim이 가능한데, 예를 들면 다음과 같습니다.

```csharp
System.Fakes.ShimEnvironment.GetCommandLineArgsGet = ...
```

## <a name="limitations"></a>제한 사항

.NET 기본 클래스 라이브러리 **mscorlib** 및 **System**의 일부 형식에서는 shim을 사용할 수 없습니다.

## <a name="see-also"></a>참고 항목

- [Microsoft Fakes를 사용하여 테스트 대상 코드 격리](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Peter Provost의 블로그: Visual Studio 2012 Shim](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [비디오(1h16): Visual Studio 2012에서 Fakes를 사용하여 테스트되지 않은 코드 테스트](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
