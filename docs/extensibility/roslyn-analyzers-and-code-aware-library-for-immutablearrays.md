---
title: ImmutableArrays에 대 한 Roslyn 분석기 및 코드 인식 라이브러리
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6fc40d229b911500cb6c196dba34546ed9ede206
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741659"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>ImmutableArrays에 대 한 Roslyn 분석기 및 코드 인식 라이브러리

[.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn")를 사용 하면 코드 인식 라이브러리를 빌드할 수 있습니다. 코드 인식 라이브러리는 및 도구 (Roslyn 분석기)를 사용 하 여 라이브러리를 가장 적절 한 방법으로 사용 하거나 오류를 방지 하는 데 사용할 수 있는 기능을 제공 합니다. 이 항목에서는 [Roslyn NuGet 패키지](https://www.nuget.org/packages/System.Collections.Immutable) 를 사용 하는 경우 일반적인 오류를 catch 하기 위해 실제 세계 analyzer를 빌드하는 방법을 보여 줍니다. 이 예제에서는 분석기에서 발견 한 코드 문제에 대 한 코드 픽스를 제공 하는 방법도 보여 줍니다. 사용자는 Visual Studio 전구 UI에서 코드 수정 사항을 확인 하 고 코드에 대 한 수정 사항을 자동으로 적용할 수 있습니다.

## <a name="get-started"></a>시작하기

이 예제를 빌드하려면 다음이 필요 합니다.

* Visual Studio 2015 (Express Edition 아님) 이상 버전. 무료 [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/) 을 사용할 수 있습니다.
* [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md). Visual Studio를 설치할 때 **일반적인 도구** 에서 **Visual Studio 확장성 도구** 를 확인 하 여 SDK를 동시에 설치할 수도 있습니다. Visual Studio를 이미 설치한 경우에는 기본 메뉴 **파일**  >  **새**  >  **프로젝트로**이동 하 고, 왼쪽 탐색 창에서 **c #** 을 선택한 다음, **확장성**을 선택 하 여이 SDK를 설치할 수도 있습니다. "**Visual Studio 확장성 도구 설치**" 이동 경로 프로젝트 템플릿을 선택 하면 SDK를 다운로드 하 여 설치 하 라는 메시지가 표시 됩니다.
* [SDK ("Roslyn")를 .NET Compiler Platform](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK)합니다. 주 메뉴 **파일**  >  **새로 만들기**  >  **프로젝트**로 이동 하 고, 왼쪽 탐색 창에서 **c #** 을 선택한 다음, **확장성**을 선택 하 여이 SDK를 설치할 수도 있습니다. "**.NET COMPILER PLATFORM Sdk 다운로드**" 프로젝트 템플릿을 선택 하면 sdk를 다운로드 하 여 설치 하 라는 메시지가 표시 됩니다. 이 SDK는 [Roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Syntax-Visualizer.md)를 포함 합니다. 이 유용한 도구를 사용 하면 분석기에서 확인 해야 하는 코드 모델 유형을 파악할 수 있습니다. 분석기 인프라는 특정 코드 모델 형식에 대 한 코드를 호출 하므로 필요한 경우에만 코드가 실행 되 고 관련 코드 분석에만 집중할 수 있습니다.

## <a name="whats-the-problem"></a>문제가 뭔가요?

ImmutableArray (예:) 지원에 라이브러리를 제공 한다고 가정 <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName> 합니다. C # 개발자는 .NET 배열에 대해 많은 경험을 제공 합니다. 그러나 구현에 사용 되는 ImmutableArrays 및 최적화 기술 덕분에 c # Developer intuitions는 아래에 설명 된 대로 라이브러리 사용자가 손상 된 코드를 작성 하도록 합니다. 또한 사용자는 런타임 전까지 오류가 표시 되지 않습니다 .이는 .NET을 사용 하 여 Visual Studio에서 사용 되는 품질 환경이 아닙니다.

사용자는 다음과 같은 코드를 작성 하는 데 익숙할 것입니다.

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

다음 코드 줄로 채울 빈 배열을 만들고 컬렉션 이니셜라이저 구문을 사용 하는 것은 c # 개발자에 게 친숙 합니다. 그러나 런타임에 ImmutableArray 충돌에 대해 동일한 코드를 작성 합니다.

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

첫 번째 오류는 기본 데이터 저장소를 래핑하는 구조체를 사용 하 여 ImmutableArray 구현 때문입니다. 구조체에는 매개 변수가 없는 생성자가 있어야 합니다 `default(T)` . 식에서 모든 0 또는 null 멤버가 포함 된 구조체를 반환할 수 있습니다. 코드에 액세스할 때 `b1.Length` ImmutableArray 구조체에 기본 저장소 배열이 없으므로 런타임 null 역참조 오류가 발생 합니다. 빈 ImmutableArray을 만드는 올바른 방법은 `ImmutableArray<int>.Empty` 입니다.

컬렉션 이니셜라이저의 오류는 메서드를 호출할 때마다 새 인스턴스를 반환 하기 때문에 발생 합니다 `ImmutableArray.Add` . ImmutableArrays는 변경 되지 않기 때문에 새 요소를 추가할 때 새 ImmutableArray 개체 (이전에 기존 ImmutableArray를 사용 하 여 성능상의 이유로 저장소를 공유할 수 있음)를 다시 가져옵니다. `b2`는를 5 번 호출 하기 전에 첫 번째 ImmutableArray를 가리키기 때문에 `Add()` `b2` 는 기본 ImmutableArray입니다. 또한이에 대 한 호출 길이는 null 역참조 오류로 인해 충돌 합니다. 수동으로 Add를 호출 하지 않고 ImmutableArray를 초기화 하는 올바른 방법은를 사용 하는 것입니다 `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})` .

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>분석기를 트리거할 관련 구문 노드 유형을 찾습니다.

 분석기 빌드를 시작 하려면 먼저 찾아야 하는 SyntaxNode 유형을 파악 해야 합니다. 메뉴 **Syntax Visualizer** **뷰**  >  **다른 Windows**  >  **Roslyn Syntax Visualizer**에서 Syntax Visualizer를 시작 합니다.

을 선언 하는 줄에 편집기의 캐럿을 추가 `b1` 합니다. Syntax Visualizer 구문 트리의 노드에 표시 되는 것을 볼 수 있습니다 `LocalDeclarationStatement` . 이 노드에는가 있으며,이 경우에는가 있고, 마지막에는가 있습니다 `VariableDeclaration` `VariableDeclarator` `EqualsValueClause` `ObjectCreationExpression` . 노드의 Syntax Visualizer 트리를 클릭 하면 편집기 창의 구문이 강조 표시 되어 해당 노드가 나타내는 코드를 표시 합니다. SyntaxNode 하위 형식의 이름은 c # 문법에 사용 된 이름과 일치 합니다.

## <a name="create-the-analyzer-project"></a>Analyzer 프로젝트 만들기

주 메뉴에서 **파일**  >  **새로 만들기**  >  **프로젝트**를 선택 합니다. **새 프로젝트** 대화 상자의 왼쪽 탐색 모음에 있는 **c #** 프로젝트에서 **확장성**을 선택 하 고 오른쪽 창에서 코드 수정 프로젝트 템플릿이 **있는 Analyzer** 를 선택 합니다. 이름을 입력 하 고 대화 상자를 확인 합니다.

템플릿은 *DiagnosticAnalyzer.cs* 파일을 엽니다. 해당 편집기 버퍼 탭을 선택 합니다. 이 파일에는 `DiagnosticAnalyzer` (ROSLYN API 형식)에서 파생 되는 분석기 클래스 (프로젝트에 지정한 이름에서 구성 됨)가 있습니다. 새 클래스에는 `DiagnosticAnalyzerAttribute` 컴파일러가 분석기를 검색 하 고 로드할 수 있도록 분석기를 선언 하는 것이 c # 언어와 관련이 있습니다.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

C # 코드를 대상으로 하는 Visual Basic를 사용 하 여 분석기를 구현할 수 있으며 그 반대의 경우도 마찬가지입니다. DiagnosticAnalyzerAttribute에서 분석기가 한 언어를 대상으로 하는지 아니면 둘 다를 대상으로 하는지 선택 하는 것이 더 중요 합니다. 언어의 상세 모델링을 필요로 하는 더 복잡 한 분석기는 단일 언어만 대상으로 할 수 있습니다. 예를 들어 분석기에서 형식 이름 또는 공용 멤버 이름만 확인 하는 경우 Visual Basic 및 c #에서 공용 언어 모델 Roslyn 제품을 사용할 수 있습니다. 예를 들어 FxCop는 클래스가 구현 하는 것으로 경고 <xref:System.Runtime.Serialization.ISerializable> 하지만 클래스는 언어에 <xref:System.SerializableAttribute> 독립적이 고 Visual Basic 및 c # 코드 모두에 대해 작동 합니다.

## <a name="initialize-the-analyzer"></a>분석기 초기화

 적은 수의 클래스를 아래로 스크롤하여 `DiagnosticAnalyzer` 메서드를 확인 `Initialize` 합니다. 컴파일러는 분석기를 활성화할 때이 메서드를 호출 합니다. 메서드는 분석기가 `AnalysisContext` 컨텍스트 정보를 가져오고 분석할 코드 종류에 대 한 이벤트에 대 한 콜백을 등록 하는 데 사용할 수 있는 개체를 사용 합니다.

```csharp
public override void Initialize(AnalysisContext context) {}
```

이 메서드에서 새 줄을 열고 "context"를 입력 합니다. IntelliSense 완성 목록을 표시 합니다. `Register...`다양 한 종류의 이벤트를 처리 하는 다양 한 메서드가 완성 목록에서 볼 수 있습니다. 예를 들어 첫 번째는 `RegisterCodeBlockAction` 블록에 대 한 코드를 다시 호출 하는 것입니다 .이는 일반적으로 중괄호 사이에 있는 코드입니다. 블록에 등록 하면 필드 이니셜라이저, 특성에 지정 된 값 또는 선택적 매개 변수의 값에 대 한 코드를 다시 호출 합니다.

또 다른 예로는 `RegisterCompilationStartAction` 컴파일 시작 시 코드를 다시 호출 합니다 .이는 여러 위치에서 상태를 수집 해야 하는 경우에 유용 합니다. 데이터 구조를 만들어 사용 하는 모든 기호를 수집 하 고, 일부 구문 또는 기호에 대해 분석기가 다시 호출 될 때마다 데이터 구조의 각 위치에 대 한 정보를 저장할 수 있습니다. 컴파일 종료로 인해 다시 호출 하는 경우, 예를 들어 저장 한 모든 위치를 분석 하 여 코드에서 각 문에 사용 하는 기호를 보고할 수 있습니다 `using` .

**Syntax Visualizer**를 사용 하 여 컴파일러에서 ObjectCreationExpression를 처리할 때 호출 하려는 것을 배웠습니다. 이 코드를 사용 하 여 콜백을 설정 합니다.

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

구문 노드에 등록 하 고 개체 생성 구문 노드만 필터링 합니다. 규칙에 따라 분석기 작성자는 동작을 등록할 때 람다를 사용 하 여 분석기 상태를 유지 하는 데 도움이 됩니다. Visual Studio **의 관례에서 생성** 기능을 사용 하 여 메서드를 만들 수 있습니다 `AnalyzeObjectCreation` . 그러면 올바른 형식의 컨텍스트 매개 변수만 생성 됩니다.

## <a name="set-properties-for-users-of-your-analyzer"></a>분석기 사용자의 속성 설정

분석기를 Visual Studio UI에서 적절 하 게 표시 하려면 다음 코드 줄을 찾아 수정 하 여 분석기를 식별 합니다.

```csharp
internal const string Category = "Naming";
```

`"Naming"`을 `"API Guidance"`으로 변경합니다.

그런 다음 **솔루션 탐색기**를 사용 하 여 프로젝트에서 *리소스 .resx* 파일을 찾아 엽니다. 분석기, 제목 등에 대 한 설명을 입력할 수 있습니다. 지금은이 모든의 값을로 변경할 수 있습니다 `"Don't use ImmutableArray<T> constructor"` . 문자열 (, 등)에 문자열 형식 인수를 추가 하 {0} {1} 고 나중에를 호출할 때 `Diagnostic.Create()` `params` 전달할 인수 배열을 제공할 수 있습니다.

## <a name="analyze-an-object-creation-expression"></a>개체 생성 식 분석

`AnalyzeObjectCreation`메서드는 코드 분석기 프레임 워크에서 제공 하는 다른 형식의 컨텍스트를 사용 합니다. `Initialize`메서드를 사용 하면 분석기를 `AnalysisContext` 설정 하는 작업 콜백을 등록할 수 있습니다. 예를 들어,에는를 `SyntaxNodeAnalysisContext` `CancellationToken` 전달할 수 있는가 있습니다. 사용자가 편집기에서 입력을 시작 하면 Roslyn에서 분석기 실행을 취소 하 여 작업을 저장 하 고 성능을 향상 시킵니다. 또 다른 예로,이 컨텍스트에는 개체 생성 구문 노드를 반환 하는 노드 속성이 있습니다.

노드 가져오기: 구문 노드 작업을 필터링 한 형식으로 간주할 수 있습니다.

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>처음으로 분석기를 사용 하 여 Visual Studio 시작

분석기를 빌드하고 실행 하 여 Visual Studio를 시작 합니다 ( **F5**키 누르기). **솔루션 탐색기** 의 시작 프로젝트가 vsix 프로젝트 이므로 코드를 실행 하면 코드와 vsix가 빌드되고 해당 vsix가 설치 된 Visual Studio가 시작 됩니다. 이러한 방식으로 Visual Studio를 시작 하면 분석기를 빌드하는 동안 Visual Studio의 기본 사용이 테스트 인스턴스의 영향을 받지 않도록 고유한 레지스트리 hive로 시작 됩니다. 이러한 방식으로 처음 시작 하는 경우 Visual Studio는 Visual Studio를 설치한 후 처음 시작 하는 경우와 비슷한 여러 초기화를 수행 합니다.

콘솔 프로젝트를 만든 다음 배열 코드를 콘솔 응용 프로그램 Main 메서드에 입력 합니다.

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

`ImmutableArray`변경할 수 없는 NuGet 패키지를 가져오고 `using` 코드에 문을 추가 해야 하기 때문에를 사용 하는 코드 줄은 물결선. **솔루션 탐색기** 의 프로젝트 노드에서 오른쪽 포인터 단추를 누르고 **NuGet 패키지 관리**를 선택 합니다. NuGet 관리자에서 검색 상자에 "변경할 수 없음"을 입력 하 고 왼쪽 창에서 **system.object** **(변경할 수 없음) 항목**을 선택 하 고 오른쪽 창에서 **설치** 단추를 누릅니다. 패키지를 설치 하면 프로젝트 참조에 대 한 참조가 추가 됩니다.

에서 빨간색 물결선 표시 `ImmutableArray` 되 면 해당 식별자에 캐럿을 추가 하 고 **ctrl**키를 누릅니다 + **.** (마침표)를 클릭 하 여 제안 된 수정 메뉴를 표시 하 고 적절 한 문을 추가 하도록 선택 `using` 합니다.

계속 하려면 **모두 저장 하 고** Visual Studio의 두 번째 인스턴스를 닫아야 합니다.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>편집 하며 계속 하기를 사용 하 여 분석기 완료

Visual Studio의 첫 번째 인스턴스에서 `AnalyzeObjectCreation` 첫 번째 줄에 캐럿을 사용 하 여 **F9** 키를 눌러 메서드의 시작 부분에 중단점을 설정 합니다.

**F5 키**를 눌러 analyzer를 다시 시작 하 고 Visual Studio의 두 번째 인스턴스에서 마지막으로 만든 콘솔 응용 프로그램을 다시 엽니다.

Roslyn 컴파일러는 개체 생성 식을 확인 하 고 분석기에 호출 되기 때문에 중단점에서 Visual Studio의 첫 번째 인스턴스로 돌아갑니다.

**개체 생성 노드를 가져옵니다.** F10 키를 눌러 변수를 설정 하는 줄을 프로시저 `objectCreation` 단위로 실행 하 고 **F10** **직접 실행 창** 에서 식을 계산 `"objectCreation.ToString()"` 합니다. 변수가 가리키는 구문 노드는 코드 이며, 사용자가 원하는 것입니다 `"new ImmutableArray<int>()"` .

**ImmutableArray<T \> 형식 개체를 가져옵니다.** 만들려는 형식이 ImmutableArray 인지 확인 해야 합니다. 먼저이 형식을 나타내는 개체를 가져옵니다. 의미 체계 모델을 사용 하 여 형식을 검사 하 여 정확히 올바른 형식이 있는지 확인 하 고에서 문자열을 비교 하지 않습니다 `ToString()` . 함수 끝에 다음 코드 줄을 입력 합니다.

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

백 틱 (') 및 제네릭 매개 변수 수를 사용 하 여 메타 데이터의 제네릭 형식을 지정 합니다. 이러한 이유 때문에 "... ImmutableArray \<T> "를 메타 데이터 이름에 있습니다.

의미 체계 모델에는 기호, 데이터 흐름, 변수 수명 등에 대해 질문할 수 있는 많은 유용한 항목이 있습니다. Roslyn는 다양 한 엔지니어링 이유 (성능, 잘못 된 코드 모델링 등)를 위해 의미 체계 모델에서 구문 노드를 분리 합니다. 컴파일 모델에서 정확한 비교를 위해 참조에 포함 된 정보를 조회 하려고 합니다.

편집기 창의 왼쪽에서 노란색 실행 포인터를 끌 수 있습니다. 변수를 설정 하는 줄까지 끌고 F10 키를 `objectCreation` 사용 하 여 새 코드 줄을 프로시저 **F10**단위로 실행 합니다. 변수 위로 마우스 포인터를 가져가면 `immutableArrayOfType` 의미 체계 모델에 정확한 유형이 발견 된 것을 알 수 있습니다.

**개체 생성 식의 유형을 가져옵니다.** 이 문서에서 "Type"은 몇 가지 방법으로 사용 되지만이는 "new Foo" 식이 있는 경우 Foo의 모델을 가져와야 함을 의미 합니다. 개체 생성 식의 형식을 가져와서 ImmutableArray 형식 인지 확인 해야 \<T> 합니다. 의미 체계 모델을 다시 사용 하 여 개체 생성 식의 형식 기호 (ImmutableArray)에 대 한 기호 정보를 가져옵니다. 함수 끝에 다음 코드 줄을 입력 합니다.

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

분석기가 편집기 버퍼에서 불완전 하거나 잘못 된 코드를 처리 해야 하기 때문에 (예: 누락 된 `using` 문)이 있는지 확인 해야 `symbolInfo` `null` 합니다. 분석을 완료 하려면 기호 정보 개체에서 명명 된 형식 (INamedTypeSymbol)을 가져와야 합니다.

**형식을 비교 합니다.** 찾고자 하는 개방형 제네릭 형식이 있고 코드의 형식이 구체적인 제네릭 형식이 기 때문에 형식이 생성 된 항목 (개방형 제네릭 형식)에 대 한 기호 정보를 쿼리하고 해당 결과를와 비교 `immutableArrayOfTType` 합니다. 메서드 끝에 다음을 입력 합니다.

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**진단을 보고 합니다.** 진단 보고는 매우 쉽습니다. Initialize 메서드 이전에 정의 된 프로젝트 템플릿에서 생성 된 규칙을 사용 합니다. 코드에서 이러한 상황이 발생 하기 때문에 `DiagnosticSeverity.Warning` (녹색 물결선)을 `DiagnosticSeverity.Error` (빨간색 물결선)로 대체 하도록 초기화 된 규칙의 줄을 변경할 수 있습니다. 규칙의 나머지 부분은 연습의 시작 부분에서 편집한 리소스에서 초기화 됩니다. 또한 개체 생성 식의 형식 사양의 위치인 물결선의 위치를 보고 해야 합니다. 블록에 다음 코드를 입력 합니다 `if` .

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

함수는 다음과 같이 표시 됩니다 (형식이 다르게 지정 될 수도 있음).

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

분석기가 작동 하는 것을 볼 수 있도록 중단점을 제거 하 고 Visual Studio의 첫 번째 인스턴스로 반환 하는 것을 중지 합니다. 실행 포인터를 메서드의 시작 부분으로 끌고 **F5** 키를 눌러 실행을 계속 합니다. Visual Studio의 두 번째 인스턴스로 다시 전환 하면 컴파일러가 코드를 다시 검사 하기 시작 하 고 분석기를 호출 합니다. 에서 물결 표시를 볼 수 있습니다 `ImmutableType<int>` .

## <a name="adding-a-code-fix-for-the-code-issue"></a>코드 문제에 대 한 "코드 수정" 추가

시작 하기 전에 Visual Studio의 두 번째 인스턴스를 닫고 Visual Studio의 첫 번째 인스턴스 (분석기를 개발 하는)에서 디버깅을 중지 합니다.

**새 클래스를 추가합니다.** **솔루션 탐색기** 의 프로젝트 노드에서 바로 가기 메뉴 (오른쪽 포인터 단추)를 사용 하 여 새 항목을 추가 하도록 선택 합니다. 이라는 클래스를 추가 `BuildCodeFixProvider` 합니다. 이 클래스는에서 파생 되어야 `CodeFixProvider` 하며 **Ctrl 키**를 사용 해야 + **합니다.** (마침표)를 호출 하 여 올바른 문을 추가 하는 코드 수정을 호출 합니다 `using` . 또한이 클래스는 특성을 사용 하 여 주석을 지정 해야 `ExportCodeFixProvider` 하며 열거형을 확인 하는 문을 추가 해야 합니다 `using` `LanguageNames` . 다음 코드를 포함 하는 클래스 파일이 있어야 합니다.

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**파생 멤버를 스텁 아웃 합니다.** 이제 식별자에 편집기의 캐럿을 추가 `CodeFixProvider` 하 고 **ctrl**키를 누릅니다 + **.** (마침표)를 통해이 추상 기본 클래스에 대 한 구현을 스텁 합니다. 그러면 속성 및 메서드가 생성 됩니다.

**속성을 구현 합니다.** `FixableDiagnosticIds` `get` 다음 코드를 사용 하 여 속성의 본문을 입력 합니다.

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn는 이러한 식별자 (문자열만)를 일치 시켜 진단 및 픽스를 함께 제공 합니다. 프로젝트 템플릿에서 진단 ID를 생성 했으며 사용자는이를 자유롭게 변경할 수 있습니다. 속성의 코드는 분석기 클래스에서 ID를 반환 합니다.

**RegisterCodeFixAsync 메서드는 컨텍스트를 사용 합니다.** 코드 수정이 여러 진단에 적용 될 수 있거나 코드 줄에 둘 이상의 문제가 있을 수 있으므로 컨텍스트가 중요 합니다. "Context"를 입력 하는 경우 메서드의 본문에서 IntelliSense 완성 목록에 몇 가지 유용한 멤버가 표시 됩니다. 수정 사항을 취소 하려는 항목이 있는지 확인할 수 있는 CancellationToken 멤버가 있습니다. 많은 유용한 멤버를 포함 하는 문서 멤버가 있으며이를 사용 하 여 프로젝트 및 솔루션 모델 개체에 액세스할 수 있습니다. 진단을 보고할 때 지정 된 코드 위치의 시작과 끝에 해당 하는 범위 멤버가 있습니다.

**메서드를 비동기로 설정 합니다.** 가장 먼저 해야 할 일은 생성 된 메서드 선언을 메서드로 수정 하는 것입니다 `async` . 추상 클래스의 구현에 대 한 코드 픽스는 `async` 메서드가를 반환 하는 경우에도 키워드를 포함 하지 않습니다 `Task` .

**구문 트리의 루트를 가져옵니다.** 코드를 수정 하려면 코드 수정에서 수행 하는 변경 내용을 사용 하 여 새 구문 트리를 생성 해야 합니다. 를 `Document` 호출 하려면 컨텍스트에서가 필요 합니다 `GetSyntaxRootAsync` . 이 메서드는 구문 트리를 가져오는 알 수 없는 작업 (디스크에서 파일 가져오기, 구문 분석 및 Roslyn 코드 모델 빌드 포함)이 있으므로 비동기 메서드입니다. 을 사용 하 여이 시간 동안 Visual Studio UI에 응답 해야 합니다 `async` . 메서드의 코드 줄을 다음으로 바꿉니다.

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**문제가 있는 노드를 찾습니다.** 컨텍스트 범위를 전달 하지만 찾은 노드가 변경 해야 할 코드가 아닐 수도 있습니다. 보고 된 진단은 형식 식별자에 대 한 범위 (해당 하는 경우, 해당 하는 경우)만 제공 하지만 전체 개체 생성 식을 대체 해야 합니다. 여기에는 시작 부분에 있는 `new` 키워드와 끝에 괄호가 포함 됩니다. 메서드에 다음 코드를 추가 하 고 **Ctrl 키**를 사용 + **합니다.** `using`에 대 한 문을 추가 하려면 `ObjectCreationExpressionSyntax` :

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**전구 UI에 대 한 코드 수정 프로그램을 등록 합니다.** 코드 픽스를 등록 하면 Roslyn가 Visual Studio 전구 UI에 자동으로 연결 됩니다. 최종 사용자에 게 **Ctrl 키**를 사용할 수 있는 것을 볼 수 있습니다 + **.** (기간) 분석기에서 물결선 잘못 된 생성자를 사용 하는 경우 `ImmutableArray<T>` . 코드 수정 공급자는 문제가 있는 경우에만 실행 되므로 원하는 개체 생성 식이 있다고 가정할 수 있습니다. 컨텍스트 매개 변수에서 메서드의 끝에 다음 코드를 추가 하 여 새 코드 수정을 등록할 수 있습니다 `RegisterCodeFixAsync` .

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

편집기의 캐럿을 식별자에 배치한 `CodeAction` 다음 **Ctrl 키**를 사용 해야 합니다 + **.** (마침표)를 입력 하 여 해당 `using` 형식에 대 한 적절 한 문을 추가 합니다.

그런 다음 식별자에 편집기의 캐럿을 추가 `ChangeToImmutableArrayEmpty` 하 고 **Ctrl 키**를 사용 + **합니다.** 다시 한 번이 메서드 스텁을 생성 합니다.

추가한이 마지막 코드 조각은 `CodeAction` 발견 된 문제 종류에 대 한 및 진단 ID를 전달 하 여 코드 수정을 등록 합니다. 이 예제에서는이 코드에서 픽스를 제공 하는 진단 ID가 하나만 있으므로 진단 Id 배열의 첫 번째 요소만 전달 하면 됩니다. 를 만들 때 전구 `CodeAction` UI가 코드 수정에 대 한 설명으로 사용 해야 하는 텍스트를 전달 합니다. 또한 CancellationToken를 사용 하 고 새 문서를 반환 하는 함수를 전달 합니다. 새 문서에는를 호출 하는 패치 된 코드를 포함 하는 새 구문 트리가 있습니다 `ImmutableArray.Empty` . 이 코드 조각에서는 개체를 사용 하 여 개체를 만들 수 있도록 람다를 사용 합니다.

**새 구문 트리를 생성 합니다.** 이전에 `ChangeToImmutableArrayEmpty` 생성 한 스텁이 있는 메서드에서 코드 줄을 입력 `ImmutableArray<int>.Empty;` 합니다. **Syntax Visualizer** 도구 창을 다시 보면이 구문이 SimpleMemberAccessExpression 노드가 될 수 있습니다. 이 메서드는 새 문서를 생성 하 고 반환 하는 데 필요 합니다.

`ChangeToImmutableArrayEmpty` `async` `Task<Document>` 코드 생성기에서 메서드를 async로 간주할 수 없기 때문에에 대 한 첫 번째 변경 내용이 앞에 추가 됩니다.

다음 코드를 사용 하 여 본문을 입력 하면 메서드가 다음과 같이 표시 됩니다.

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

편집기의 캐럿을 식별자에 넣고 `SyntaxGenerator` **Ctrl 키**를 사용 해야 합니다 + **.** (마침표)를 입력 하 여 해당 `using` 형식에 대 한 적절 한 문을 추가 합니다.

이 코드는 `SyntaxGenerator` 새 코드를 생성 하는 데 유용한 형식인를 사용 합니다. 코드 문제가 있는 문서에 대 한 생성기를 가져온 후에는를 호출 하 여 `ChangeToImmutableArrayEmpty` 액세스 하려는 `MemberAccessExpression` 멤버가 있는 형식을 전달 하 고 멤버의 이름을 문자열로 전달 합니다.

그런 다음 메서드는 문서의 루트를 인출 하며,이는 일반적인 경우 임의의 작업을 포함할 수 있기 때문에 코드에서이 호출을 기다립니다 취소 토큰을 전달 합니다. .NET 문자열 작업 처럼 Roslyn 코드 모델은 변경할 수 없습니다. 문자열을 업데이트 하는 경우 새 문자열 개체를 반환 합니다. 를 호출 하면 `ReplaceNode` 새 루트 노드가 반환 됩니다. 대부분의 구문 트리는 변경할 수 없기 때문에 공유 되지만 노드는 노드 및 `objectCreation` `memberAccess` 모든 부모 노드 (구문 트리 루트까지)로 대체 됩니다.

## <a name="try-your-code-fix"></a>코드 수정 시도

이제 **F5** 키를 눌러 Visual Studio의 두 번째 인스턴스에서 분석기를 실행할 수 있습니다. 이전에 사용한 콘솔 프로젝트를 엽니다. 이제 새 개체 생성 식이에 대해 표시 되는 전구를 확인 해야 합니다 `ImmutableArray<int>` . **Ctrl**키를 누릅니다 + **.** (마침표) 코드 수정 프로그램이 표시 되 고 전구 UI에 자동으로 생성 된 코드 차이 미리 보기가 표시 됩니다. Roslyn 사용자에 게이를 만듭니다.

**Pro 팁:** Visual Studio의 두 번째 인스턴스를 시작 하 고 코드 수정이 포함 된 전구가 표시 되지 않으면 Visual Studio 구성 요소 캐시를 지워야 할 수 있습니다. 캐시를 지우면 Visual studio에서 구성 요소를 다시 검사 하므로 Visual Studio에서 최신 구성 요소를 선택 해야 합니다. 먼저 Visual Studio의 두 번째 인스턴스를 종료 합니다. 그런 다음 **Windows 탐색기**에서 *%LOCALAPPDATA%\Microsoft\VisualStudio\16.0Roslyn \\ *로 이동 합니다. ("16.0"은 Visual Studio를 사용 하 여 버전에서 버전으로 변경 됩니다.) 하위 디렉터리 *Componentmodelcache*를 삭제 합니다.

## <a name="talk-video-and-finish-code-project"></a>비디오 및 종료 코드 프로젝트

이 예에서는이 방법에 대해 설명 하 고 [이에 대해](https://channel9.msdn.com/events/Build/2015/3-725)자세히 설명 합니다. 이 대화에서는 작동 하는 분석기를 설명 하 고이를 빌드하는 과정을 안내 합니다.

[여기](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)에서 완성 된 코드를 모두 볼 수 있습니다. 하위 폴더 *DoNotUseImmutableArrayCollectionInitializer* 및 *DoNotUseImmutableArrayCtor* 에는 각각 문제를 찾기 위한 c # 파일과 Visual Studio 전구 UI에 표시 되는 코드 수정 프로그램을 구현 하는 c # 파일이 있습니다. 완성 된 코드에는 ImmutableArray type 개체를 가져오는 것을 방지 하기 위한 약간의 추상화가 있습니다 \<T> . 등록 된 중첩 된 작업을 사용 하 여 하위 작업 (개체 만들기 및 컬렉션 초기화 분석)이 실행 될 때마다 사용할 수 있는 컨텍스트에 형식 개체를 저장 합니다.

## <a name="see-also"></a>참고 항목

* [\\\Build 2015 통신](https://channel9.msdn.com/events/Build/2015/3-725)
* [GitHub에서 완성 된 코드](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [GitHub에 대 한 몇 가지 예제는 세 가지 분석기로 그룹화 되어 있습니다.](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [GitHub OSS 사이트의 기타 문서](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [GitHub에서 Roslyn 분석기를 사용 하 여 구현 된 FxCop 규칙](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
