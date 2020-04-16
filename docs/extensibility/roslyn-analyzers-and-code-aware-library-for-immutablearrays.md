---
title: 로슬린 분석기 및 불변성 에 대한 코드 인식 라이브러리 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2076bc9fe3cabbfef8d3f3fb0248724835fa83f5
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444572"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>로슬린 분석기 및 불변성 어레이에 대한 코드 인식 라이브러리

[.NET 컴파일러](https://github.com/dotnet/roslyn) 플랫폼("Roslyn")을 사용하면 코드 인식 라이브러리를 빌드할 수 있습니다. 코드 인식 라이브러리는 라이브러리를 가장 좋은 방법으로 사용하거나 오류를 방지하는 데 도움이 되는 도구 및 툴링(Roslyn 분석기)을 제공합니다. 이 항목에서는 [System.Collections.ImMutable](https://www.nuget.org/packages/System.Collections.Immutable) NuGet 패키지를 사용할 때 일반적인 오류를 catch하기 위해 실제 Roslyn 분석기를 빌드하는 방법을 보여 주며 이 항목에서는 다음과 같은 방법을 보여 주실 수 있습니다. 또한 이 예제에서는 분석기에서 찾은 코드 문제에 대한 코드 수정 프로그램을 제공하는 방법을 보여 줍니다. 사용자는 Visual Studio 전구 UI에서 코드 수정 사항을 보고 코드에 대한 수정 프로그램을 자동으로 적용할 수 있습니다.

## <a name="get-started"></a>시작

이 예제를 빌드하려면 다음이 필요합니다.

* 비주얼 스튜디오 2015 (익스프레스 에디션이 아님) 또는 이후 버전. 무료 [비주얼 스튜디오 커뮤니티 에디션을](https://visualstudio.microsoft.com/vs/community/) 사용할 수 있습니다.
* [비주얼 스튜디오 SDK](../extensibility/visual-studio-sdk.md). 또한 Visual Studio를 설치할 때 **공통 도구** 에서 Visual **Studio 확장성 도구를** 확인하여 SDK를 동시에 설치할 수도 있습니다. Visual Studio를 이미 설치한 경우 기본 **메뉴파일** > **새** > **프로젝트로**이동하여 왼쪽 탐색 창에서 **C#을** 선택한 다음 **확장성을**선택하여 이 SDK를 설치할 수도 있습니다. "Visual Studio**확장성 도구 설치"** 이동 경로 프로젝트 템플릿을 선택하면 SDK를 다운로드하여 설치하라는 메시지가 표시됩니다.
* [.NET 컴파일러 플랫폼 ("로슬린") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). 또한 기본 메뉴로 이동하여 이 SDK를 설치할 수 있습니다 **파일** > **새** > **프로젝트,** 왼쪽 탐색 창에서 **C #을** 선택한 다음 **확장성을 선택합니다.** **".NET 컴파일러 플랫폼 SDK**다운로드" "이동 경로 프로젝트 템플릿을 선택하면 SDK를 다운로드하여 설치하라는 메시지가 표시됩니다. 이 SDK에는 [로슬린 구문 시각화 도우미가](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer)포함되어 있습니다. 이 유용한 도구를 사용하면 분석기에서 찾아야 할 코드 모델 유형을 파악할 수 있습니다. 분석기 인프라는 특정 코드 모델 유형에 대해 코드를 호출하므로 코드는 필요한 경우에만 실행되고 관련 코드 분석에만 집중할 수 있습니다.

## <a name="whats-the-problem"></a>문제가 뭔가요?

라이브러리에 <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>ImmutableArray(예:) 지원을 제공하면 됩니다. C# 개발자는 .NET 배열에 대한 많은 경험을 가지고 있습니다. 그러나 구현에 사용되는 ImmutableArrays 및 최적화 기술의 특성으로 인해 C# 개발자 직관으로 인해 라이브러리 사용자는 아래에 설명된 대로 깨진 코드를 작성하게 됩니다. 또한 사용자는 .NET을 사용하여 Visual Studio에서 사용하는 품질 환경이 아닌 런타임까지 오류를 볼 수 없습니다.

사용자는 다음과 같은 코드를 작성하는 데 익숙합니다.

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

후속 코드 줄로 채울 빈 배열을 만들고 컬렉션 초기화자 구문을 사용하는 것은 C# 개발자에게 익숙합니다. 그러나 변경 가능한 배열에 대해 동일한 코드를 작성하면 런타임에 충돌이 발생합니다.

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

첫 번째 오류는 기본 데이터 저장소를 래핑하기 위해 구조체를 사용하는 ImmutableArray 구현 때문입니다. `default(T)` 식이 모든 0 또는 null 멤버를 가진 구조체를 반환할 수 있도록 구조체에는 매개 변수가 없는 생성자가 있어야 합니다. 코드가 액세스하면 `b1.Length`ImmutableArray 구조체에 기본 저장소 배열이 없기 때문에 런타임 null 참조 오류가 발생합니다. 빈 변경할 수 없는 배열을 만드는 `ImmutableArray<int>.Empty`올바른 방법은 .

메서드가 호출할 때마다 새 `ImmutableArray.Add` 인스턴스를 반환하기 때문에 컬렉션 초기화자가 있는 오류가 발생합니다. 변경 되지 않습니다 때문에 변경 되지 않습니다. 새 요소를 추가할 때 다시 얻을 새 ImmutableArray 개체 (기존 ImmutableArray 성능상의 이유로 저장소를 공유할 수 있습니다). 호출하기 전에 첫 번째 [불가분 불가]를 가리키기 때문에 `b2` 기본 `b2` 불가변배열입니다. `Add()` 그것에 길이를 호출 하는 null 참조 오류와 충돌. 수동으로 Add를 호출하지 않고 ImmutableArray를 초기화하는 `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`올바른 방법은 을 사용하는 것입니다.

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>분석기를 트리거할 관련 구문 노드 유형 찾기

 분석기를 빌드하기 시작하려면 먼저 찾아야 할 SyntaxNode 유형을 파악합니다. **메뉴보기** > **다른 윈도우** > **로슬린 구문 시각화 도우미에서** **구문 시각화** 도우미를 시작합니다.

을 선언하는 줄에 편집기의 카를을 놓습니다. `b1` 구문 시각화 도우미가 구문 트리의 `LocalDeclarationStatement` 노드에 있음을 보여 줄 것입니다. 이 노드에는 `VariableDeclaration` `VariableDeclarator`에 의한 이노드가 있으며, `EqualsValueClause`이 노드에는 `ObjectCreationExpression`에 의한 이점이 있습니다. 노드의 구문 시각화 도우미 트리를 클릭하면 편집기 창의 구문이 강조 표시되어 해당 노드로 표시되는 코드가 표시됩니다. SyntaxNode 하위 형식의 이름은 C# 문법에 사용된 이름과 일치합니다.

## <a name="create-the-analyzer-project"></a>분석기 프로젝트 만들기

주 메뉴에서**새** > **프로젝트** **파일** > 을 선택합니다. 새 **프로젝트** 대화 상자에서 왼쪽 탐색 모음의 **C#** 프로젝트에서 **확장성을**선택하고 오른쪽 창에서 코드 수정 프로젝트 템플릿을 **가진 분석기를** 선택합니다. 이름을 입력하고 대화 상자를 확인합니다.

템플릿이 *DiagnosticAnalyzer.cs* 파일을 엽니다. 해당 편집기 버퍼 탭을 선택합니다. 이 파일에는 (Roslyn API 형식)에서 `DiagnosticAnalyzer` 파생 된 분석기 클래스 (프로젝트에 준 이름으로 형성)가 있습니다. 새 클래스에는 `DiagnosticAnalyzerAttribute` 컴파일러가 분석기를 검색하고 로드할 수 있도록 분석기와 관련된 분석기선언이 있습니다.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

C# 코드를 대상으로 하는 Visual Basic을 사용 하 여 분석기를 구현할 수 있습니다., 그 반대의 경우도 마찬가지입니다. 분석기에서 한 언어 또는 둘 다 대상여부를 선택하는 것이 진단 분석기 특성에서 더 중요합니다. 언어의 상세한 모델링이 필요한 보다 정교한 분석기는 단일 언어만 대상으로 지정할 수 있습니다. 예를 들어 분석기에서 형식 이름 또는 공용 멤버 이름만 검사하는 경우 Visual Basic 및 C#에서 Roslyn이 제공하는 공통 언어 모델을 사용할 수 있습니다. 예를 들어 FxCop은 클래스가 <xref:System.Runtime.Serialization.ISerializable>구현되지만 클래스에는 <xref:System.SerializableAttribute> 언어독립적이며 Visual Basic 및 C# 코드 모두에서 작동합니다.

## <a name="initialize-the-analyzer"></a>분석기 초기화

 클래스에서 `DiagnosticAnalyzer` 약간 아래로 스크롤하여 `Initialize` 메서드를 확인합니다. 컴파일러는 분석기를 활성화할 때 이 메서드를 호출합니다. 이 메서드는 `AnalysisContext` 분석기에서 컨텍스트 정보를 얻고 분석하려는 코드 종류에 대한 이벤트에 대한 콜백을 등록할 수 있는 개체를 가져옵니다.

```csharp
public override void Initialize(AnalysisContext context) {}
```

이 메서드에서 새 줄을 열고 "컨텍스트"를 입력합니다. 을 참조하면 IntelliSense 완료 목록이 표시됩니다. 완료 목록에서 다양한 종류의 이벤트를 `Register...` 처리하는 여러 가지 방법이 있음을 알 수 있습니다. 예를 들어 첫 번째 `RegisterCodeBlockAction`는 " 일반적으로 곱슬 대 괄호 사이의 코드인 블록에 대해 코드를 다시 호출합니다. 블록에 등록하면 필드의 초기화자, 특성에 지정된 값 또는 선택적 매개 변수의 값에 대한 코드도 다시 호출됩니다.

또 다른 `RegisterCompilationStartAction`예로 , 컴파일이 시작될 때 코드를 다시 호출하므로 여러 위치에서 상태를 수집해야 할 때 유용합니다. 데이터 구조를 만들어 사용되는 모든 기호를 수집할 수 있으며 분석기에서 일부 구문이나 기호를 다시 호출할 때마다 데이터 구조의 각 위치에 대한 정보를 저장할 수 있습니다. 컴파일 종료로 인해 다시 호출되는 경우 예를 들어 저장한 모든 위치를 분석하여 코드가 각 `using` 문에서 사용하는 기호를 보고할 수 있습니다.

**구문 시각화 도우미를**사용 하 여 컴파일러 개체 CreationExpression를 처리 할 때 호출 하려는 것을 배웠습니다. 이 코드를 사용하여 콜백을 설정합니다.

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

구문 노드에 등록하고 개체 만들기 구문 노드만 필터링합니다. 규칙에 따라 분석기 작성자는 작업을 등록할 때 lambda를 사용하므로 분석기를 상태 비상태로 유지하는 데 도움이 됩니다. Visual Studio 기능을 사용하여 **사용에서 생성하여** 메서드를 `AnalyzeObjectCreation` 만들 수 있습니다. 이렇게 하면 컨텍스트 매개 변수의 올바른 형식도 생성됩니다.

## <a name="set-properties-for-users-of-your-analyzer"></a>분석기 사용자에 대한 속성 설정

분석기가 Visual Studio UI에 적절하게 표시되도록 다음 코드 줄을 찾아 수정하여 분석기를 식별합니다.

```csharp
internal const string Category = "Naming";
```

`"Naming"`을 `"API Guidance"`으로 변경합니다.

다음으로 **솔루션 탐색기를**사용하여 프로젝트에서 *Resources.resx* 파일을 찾아 엽니다. 분석기, 제목 등에 대한 설명을 넣을 수 있습니다. 이 모든 값을 현재로 `"Don't use ImmutableArray<T> constructor"` 변경할 수 있습니다. {0}문자열 (, {1}등)에 문자열 서식 지정 인수를 넣을 수 `Diagnostic.Create()`있으며 나중에 호출 `params` 할 때 전달 할 인수 배열을 제공 할 수 있습니다.

## <a name="analyze-an-object-creation-expression"></a>개체 생성 식 분석

메서드는 `AnalyzeObjectCreation` 코드 분석기 프레임워크에서 제공하는 다른 유형의 컨텍스트를 사용합니다. 메서드를 `Initialize` `AnalysisContext` 사용하면 작업 콜백을 등록하여 분석기를 설정할 수 있습니다. 예를 `SyntaxNodeAnalysisContext`들어, 전달할 `CancellationToken` 수 있는 a가 있습니다. 사용자가 편집기에서 입력을 시작하면 Roslyn은 작업을 저장하고 성능을 향상시키기 위해 실행 중인 분석기를 취소합니다. 또 다른 예로, 이 컨텍스트에는 개체 생성 구문 노드를 반환하는 Node 속성이 있습니다.

구문 노드 작업을 필터링한 형식이라고 가정할 수 있는 노드를 가져옵니다.

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>분석기로 Visual Studio를 처음 실행

분석기를 구축하고 실행하여 Visual Studio를 **시작합니다(F5**를 누릅니다). **솔루션 탐색기의** 시작 프로젝트는 VSIX 프로젝트이므로 코드를 실행하면 코드와 VSIX가 빌드된 다음 VSIX가 설치된 Visual Studio를 시작합니다. 이러한 방식으로 Visual Studio를 시작하면 고유한 레지스트리 하이브로 시작되므로 분석기를 빌드하는 동안 Visual Studio의 주요 사용이 테스트 인스턴스의 영향을 받지 않습니다. 이러한 방식으로 처음 시작할 때 Visual Studio는 설치 후 Visual Studio를 처음 시작했을 때와 유사한 몇 가지 초기화를 수행합니다.

콘솔 프로젝트를 만든 다음 콘솔 응용 프로그램 Main 메서드에 배열 코드를 입력합니다.

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

변경할 수 없는 `ImmutableArray` NuGet 패키지를 얻고 코드에 `using` 문을 추가해야 하기 때문에 물결선이 있는 코드 줄에 물결선이 있습니다. **솔루션 탐색기의** 프로젝트 노드에서 오른쪽 포인터 버튼을 누르고 **NuGet 패키지 관리를 선택합니다.** NuGet 관리자에서 검색 상자에 "변경할 수 없습니다"를 입력하고 왼쪽 창에서 **System.Collections.Immutable** **항목(Microsoft.Bcl.Immutable을**선택하지 않음)을 선택하고 오른쪽 창의 **설치** 버튼을 누릅니다. 패키지를 설치하면 프로젝트 참조에 대한 참조가 추가됩니다.

당신은 여전히 `ImmutableArray`아래에 빨간색 물결선이 표시되므로 해당 식별자에서 캐럿을 배치하고 **Ctrl을**+누릅니다.**.** (기간)을 사용하여 제안된 수정 메뉴를 가져오고 적절한 `using` 문을 추가하도록 선택합니다.

**모두를 저장하고** 계속 깨끗한 상태로 넣어 지금 Visual Studio의 두 번째 인스턴스를 닫습니다.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>편집을 사용하여 분석기를 완료하고 계속

Visual Studio의 첫 번째 인스턴스에서는 첫 번째 줄의 캐릿으로 `AnalyzeObjectCreation` **F9을** 눌러 메서드의 시작 부분에 중단점을 설정합니다.

**F5를**사용 하 여 분석기를 다시 시작 하 고 Visual Studio의 두 번째 인스턴스에서 마지막으로 만든 콘솔 응용 프로그램을 다시 엽니다.

Roslyn 컴파일러가 개체 생성 식을 보고 분석기로 호출했기 때문에 중단점에서 Visual Studio의 첫 번째 인스턴스로 돌아갑니다.

**개체 생성 노드를 가져옵니다.** **F10을**눌러 `objectCreation` 변수를 설정하는 선을 단계별로 단계별로 설정하고 `"objectCreation.ToString()"`즉시 **창에서** 식을 평가합니다. 변수가 가리키는 구문 노드가 원하는 코드입니다. `"new ImmutableArray<int>()"`

**변경할 수 없는 배열\><T 유형 개체를 가져옵니다.** 생성되는 형식이 변경 불가능한 배열인지 확인해야 합니다. 먼저 이 형식을 나타내는 개체를 가져옵니다. 의미 체계 모델을 사용하여 형식을 확인하여 정확히 올바른 형식이 있는지 확인하고 에서 `ToString()`문자열을 비교하지 않습니다. 함수 끝에 다음 코드 줄을 입력합니다.

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

백틱(') 및 제네릭 매개 변수 수를 사용한 메타데이터의 제네릭 형식을 지정합니다. 당신이 볼 수없는 이유입니다 "... 메타데이터 이름에\<"변경 불가능한 배열 t">.

의미 체계 모델에는 기호, 데이터 흐름, 가변 수명 등에 대해 질문할 수 있는 유용한 사항이 많이 있습니다. Roslyn은 다양한 엔지니어링 이유(성능, 잘못된 코드 모델링 등)를 위해 구문 노드를 의미 체계 모델과 분리합니다. 컴파일 모델이 정확한 비교를 위해 참조에 포함된 정보를 조회하도록 합니다.

편집기 창의 왼쪽에 있는 노란색 실행 포인터를 끌 수 있습니다. `objectCreation` **F10을**사용하여 변수를 설정하고 새 코드 줄을 단계별로 정렬합니다. 변수 `immutableArrayOfType`위에 마우스 포인터를 마우스 포인터로 가져가면 의미 체계 모델에서 정확한 형식을 찾은 것을 볼 수 있습니다.

**개체 만들기 식의 형식을 가져옵니다.** "Type"은 이 문서에서 몇 가지 방법으로 사용되지만,이 "새로운 Foo"표현식이있는 경우 Foo 모델을 얻어야한다는 것을 의미합니다. 개체 만들기 식의 형식을 사용하여 ImmutableArray\<t> 형식인지 확인해야 합니다. 의미 체계 모델을 다시 사용하여 개체 만들기 식에서 형식 기호(ImmutableArray)에 대한 기호 정보를 가져옵니다. 함수 끝에 다음 코드 줄을 입력합니다.

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

분석기는 편집기 버퍼에서 불완전하거나 잘못된 코드를 처리해야 하므로(예: `using` 누락된 문이 있는 `symbolInfo` `null`경우) . 분석을 완료하려면 기호 정보 개체에서 명명된 형식(INamedTypeSymbol)을 얻어야 합니다.

**형식을 비교합니다.** 찾고 있는 열려 있는 T 의 제네릭 형식이 있고 코드의 형식이 구체적인 제네릭 형식이므로 형식이 생성된 형식에 대한 기호 `immutableArrayOfTType`정보를 쿼리하고 해당 결과를 .와 비교합니다. 메서드의 끝에 다음을 입력합니다.

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**진단을 보고합니다.** 진단을 보고하는 것은 매우 쉽습니다. 초기화 방법 전에 정의된 프로젝트 템플릿에서 만든 규칙을 사용합니다. 코드의 이 상황은 오류이므로 규칙을 초기화한 줄을 변경하여 `DiagnosticSeverity.Warning` (녹색 물결선)을 `DiagnosticSeverity.Error` 빨간색 물결선으로 바꿀 수 있습니다. 규칙의 나머지 부분에서 편집한 리소스에서 초기화합니다. 또한 개체 만들기 식의 형식 사양의 위치인 물결모양의 위치를 보고해야 합니다. 블록에 이 `if` 코드를 입력합니다.

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

함수는 다음과 같아야 합니다(아마도 서식이 다르게 지정됨).

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

분석기의 작동을 볼 수 있도록 중단점을 제거하고 Visual Studio의 첫 번째 인스턴스로 돌아가는 작업을 중지합니다. 실행 포인터를 메서드의 시작 부분으로 드래그하고 **F5를** 눌러 실행을 계속합니다. Visual Studio의 두 번째 인스턴스로 다시 전환하면 컴파일러가 코드를 다시 검사하기 시작하고 분석기로 호출됩니다. 아래의 `ImmutableType<int>`물결선이 보입니다.

## <a name="adding-a-code-fix-for-the-code-issue"></a>코드 문제에 대한 "코드 수정" 추가

시작하기 전에 Visual Studio의 두 번째 인스턴스를 닫고 분석기를 개발하는 Visual Studio의 첫 번째 인스턴스에서 디버깅을 중지합니다.

**새 클래스를 추가합니다.** **솔루션 탐색기에서** 프로젝트 노드의 바로 가기 메뉴(오른쪽 포인터 단추)를 사용하고 새 항목을 추가하도록 선택합니다. 을 라는 `BuildCodeFixProvider`클래스를 추가합니다. 이 클래스에서 `CodeFixProvider`파생되어야 하며 **Ctrl**+을 사용해야**합니다.** (기간)을 사용하여 올바른 `using` 문을 추가하는 코드 수정 을 호출합니다. 또한 이 클래스는 특성에 `ExportCodeFixProvider` 추가되어야 하며 `using` `LanguageNames` 열거형 문제를 해결하기 위해 문을 추가해야 합니다. 다음과 같은 코드가 있는 클래스 파일이 있어야 합니다.

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**파생 된 멤버를 스텁합니다.** 이제 편집기의 `CodeFixProvider` 캐럿을 식별자 안에 놓고 **Ctrl을**+누릅니다.**.** (기간)을 사용하여 이 추상 기본 클래스에 대한 구현을 스텁합니다. 그러면 속성과 메서드가 생성됩니다.

**속성을 구현합니다.** `FixableDiagnosticIds` 속성 본문에 `get` 다음 코드를 입력합니다.

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn은 문자열인 이러한 식별자를 일치시켜 진단 및 수정 사항을 함께 제공합니다. 프로젝트 템플릿에서 진단 ID를 생성했으며 자유롭게 변경할 수 있습니다. 속성의 코드는 분석기 클래스에서 ID를 반환합니다.

**RegisterCodeFixAsync 메서드는 컨텍스트를 사용합니다.** 코드 수정이 여러 진단에 적용되거나 코드 줄에 두 개 이상의 문제가 있을 수 있으므로 컨텍스트가 중요합니다. "컨텍스트"를 입력하는 경우. 메서드의 본문에 IntelliSense 완료 목록에 몇 가지 유용한 멤버가 표시됩니다. 취소 토큰 멤버가 있어 수정 프로그램을 취소하려는지 확인할 수 있습니다. 유용한 멤버가 많고 프로젝트 및 솔루션 모델 개체에 도착할 수 있는 문서 멤버가 있습니다. 진단을 보고할 때 지정된 코드 위치의 시작 및 끝인 Span 멤버가 있습니다.

**메서드를 비동기화로 만듭니다.** 가장 먼저 해야 할 일은 생성된 메서드 선언을 `async` 메서드로 수정하는 것입니다. 추상 클래스의 구현을 스텁하기 위한 코드 수정에는 `async` 메서드가 `Task`을 반환하더라도 키워드가 포함되지 않습니다.

**구문 트리의 루트를 가져옵니다.** 코드를 수정하려면 코드 수정이 변경된 새 구문 트리를 생성해야 합니다. 을 호출하려면 `Document` `GetSyntaxRootAsync`컨텍스트에서 이가 필요합니다. 구문 트리를 가져오는 데 사용할 수 없는 작업이 있기 때문에 이 방법은 비동기 메서드입니다. Visual Studio UI는 이 시간 동안 `async` 응답해야 하며, 이 기능을 사용하면 됩니다. 메서드의 코드 줄을 다음과 같은 코드로 바꿉니다.

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**문제가 있는 노드를 찾습니다.** 컨텍스트의 범위를 전달하지만 찾은 노드는 변경해야 하는 코드가 아닐 수 있습니다. 보고된 진단은 형식 식별자(물결선이 속한 위치)에 대한 범위만 제공했지만 시작 부분에 있는 `new` 키워드와 끝에 괄호를 포함하여 전체 개체 만들기 식을 대체해야 합니다. 메서드에 다음 코드를 추가하고 **Ctrl**+**을 사용합니다.** 을 위한 `using` 문을 `ObjectCreationExpressionSyntax`추가하려면 :

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**전구 UI에 대한 코드 수정 프로그램을 등록합니다.** 코드 수정 프로그램을 등록하면 Roslyn이 Visual Studio 전구 UI에 자동으로 연결됩니다. 최종 사용자는 **Ctrl**+을 사용할 수 있음을 볼 수**있습니다.** 분석기가 잘못된 `ImmutableArray<T>` 생성자 사용을 비시하는 경우(기간) 코드 수정 공급자는 문제가 있을 때만 실행되므로 찾고 있던 개체 만들기 식이 있다고 가정할 수 있습니다. 컨텍스트 매개 변수에서 `RegisterCodeFixAsync` 메서드 끝에 다음 코드를 추가하여 새 코드 수정 프로그램을 등록할 수 있습니다.

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

편집기의 캐럿을 `CodeAction`식별자에 배치한 다음 **Ctrl**+을 사용해야**합니다.** (기간)을 사용하여 `using` 이 형식에 대한 적절한 문을 추가합니다.

그런 다음 편집기의 `ChangeToImmutableArrayEmpty` 캐럿을 식별자안에 넣고 **Ctrl**+을**사용합니다.** 다시 생성하려면 이 메서드 스텁을 생성합니다.

추가한 이 마지막 코드 조각은 발견된 문제의 `CodeAction` 종류에 대한 진단 ID와 를 전달하여 코드 수정을 등록합니다. 이 예제에서는 이 코드에서 수정 사항을 제공하는 진단 ID가 하나뿐이므로 진단 ID 배열의 첫 번째 요소를 전달할 수 있습니다. `CodeAction`을 만들 때 전구 UI가 코드 수정에 대한 설명으로 사용해야 하는 텍스트를 전달합니다. 또한 CancelToken을 받아 새 문서를 반환하는 함수를 전달합니다. 새 문서에는 을 호출하는 `ImmutableArray.Empty`패치된 코드가 포함된 새 구문 트리가 있습니다. 이 코드 조각은 개체만들기 노드와 컨텍스트의 문서를 통해 닫을 수 있도록 람다를 사용합니다.

**새 구문 트리를 구성합니다.** 앞에서 `ChangeToImmutableArrayEmpty` 생성한 스텁 메서드에서 코드 줄을 `ImmutableArray<int>.Empty;`입력합니다. **구문 시각화 도우미** 도구 창을 다시 보면 이 구문이 SimpleMemberAccessExpression 노드임을 알 수 있습니다. 이것이 이 메서드가 새 문서에서 생성하고 반환하는 데 필요한 것입니다.

첫 번째 `ChangeToImmutableArrayEmpty` 변경 사항은 `async` `Task<Document>` 코드 생성기가 메서드가 비동기라고 가정할 수 없기 때문에 이전에 추가하는 것입니다.

메서드가 다음과 유사하도록 본문에 다음 코드를 입력합니다.

```csharp
private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

`SyntaxGenerator` 편집기의 캐럿을 식별자안에 넣고 **Ctrl**+을 사용해야**합니다.** (기간)을 사용하여 `using` 이 형식에 대한 적절한 문을 추가합니다.

이 코드는 새 코드를 생성하는 데 유용한 형식인 을 사용합니다. `SyntaxGenerator` 코드 문제가 있는 문서에 대한 생성기를 `ChangeToImmutableArrayEmpty` 얻은 `MemberAccessExpression`후 호출하여 액세스하려는 멤버가 있는 형식을 전달하고 멤버 이름을 문자열로 전달합니다.

다음으로 메서드는 문서의 루트를 가져오고 일반적인 경우에 임의의 작업을 포함할 수 있으므로 코드는 이 호출을 기다리고 취소 토큰을 전달합니다. Roslyn 코드 모델은 .NET 문자열로 작업하는 것과 같이 변경할 수 없습니다. 문자열을 업데이트하면 새 문자열 개체를 가져옵니다. 호출하면 `ReplaceNode`새 루트 노드를 다시 가져옵니다. 대부분의 구문 트리는 변경할 수 없기 때문에 공유되지만 `objectCreation` 노드는 `memberAccess` 노드뿐만 아니라 구문 트리 루트까지의 모든 상위 노드로 대체됩니다.

## <a name="try-your-code-fix"></a>코드 수정 시도

이제 **F5를** 눌러 Visual Studio의 두 번째 인스턴스에서 분석기를 실행할 수 있습니다. 이전에 사용한 콘솔 프로젝트를 엽니다. 이제 새 개체 생성 표현식의 위치에 전구가 `ImmutableArray<int>`나타납니다. **당신은 Ctrl을**+누르면 **.** (기간) 다음 코드 수정 을 볼 것 이다, 그리고 전구 UI에서 자동으로 생성 된 코드 차이 미리 보기를 볼 것 이다. 로슬린은 당신을 위해이 만듭니다.

**프로 팁:** Visual Studio의 두 번째 인스턴스를 시작하고 코드 수정을 통해 전구가 표시되지 않으면 Visual Studio 구성 요소 캐시를 지워야 할 수 있습니다. 캐시를 지리려면 Visual Studio에서 구성 요소를 다시 검사해야 하므로 Visual Studio는 최신 구성 요소를 선택해야 합니다. 먼저 Visual Studio의 두 번째 인스턴스를 종료합니다. 그런 **다음, 윈도우 탐색기에서,** *%LOCALAPPDATA %\마이크로 소프트 \VisualStudio\16.0Roslyn로\\*이동합니다. ("16.0"은 Visual Studio를 사용하여 버전에서 버전으로 변경됩니다. 하위 디렉터리 *구성 요소 모델 캐시를*삭제합니다.

## <a name="talk-video-and-finish-code-project"></a>토크 비디오 및 코드 프로젝트 완료

이 예제는 [이 말씀에서](https://channel9.msdn.com/events/Build/2015/3-725)더 발전하고 논의된 것을 볼 수 있습니다. 이 강연에서는 작업 분석기를 시연하고 이를 구축하는 데 안내합니다.

완성된 모든 코드는 여기에서 볼 수 [있습니다.](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) 하위 폴더 *DoNotUseImmutable배열수집초기화자* 및 *DoNotUseImmutableArrayCtor는* 각각 문제를 찾기 위한 C# 파일과 Visual Studio 전구 UI에 표시된 코드 수정 사항을 구현하는 C# 파일을 가지고 있습니다. 완료된 코드에는 ImmutableArray\<T> 형식 개체를 반복해서 가져오지 않도록 약간 더 추상화가 있습니다. 중첩된 등록된 작업을 사용하여 하위 작업(개체 만들기 분석 및 컬렉션 초기화 분석)이 실행될 때마다 사용할 수 있는 컨텍스트에서 형식 개체를 저장합니다.

## <a name="see-also"></a>참조

* [\\\ 빌드 2015 이야기](https://channel9.msdn.com/events/Build/2015/3-725)
* [GitHub에서 완료된 코드](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [GitHub의 몇 가지 예는 세 가지 종류의 분석기로 그룹화되었습니다.](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [GitHub OSS 사이트의 다른 문서](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [GitHub에 로슬린 분석기와 구현 FxCop 규칙](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
