---
title: 코드 검사 테스트
description: Visual Studio의 코드 검사 기능을 사용하여 코딩된 테스트에서 테스트 중인 프로젝트 코드의 비율을 확인하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 07/23/2019
ms.topic: conceptual
helpviewer_keywords:
- code coverage
dev_langs:
- CSharp
- VB
- CPP
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: c74a39c81de2612bca5c3fc39286a4432916eb11
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850076"
---
# <a name="use-code-coverage-to-determine-how-much-code-is-being-tested"></a>코드 검사를 사용하여 테스트할 코드 범위 결정

프로젝트의 코드 중 유닛 테스트와 같은 코딩된 테스트를 사용하여 실제로 테스트할 부분을 결정하려면 Visual Studio의 코드 검사 기능을 사용합니다. 버그로부터 효과적으로 보호하려면 코드의 상당한 부분을 실행 또는 '검사'해야 합니다.

코드 검사 분석은 관리되는(CLI) 코드와 관리되지 않은(네이티브) 코드에 적용할 수 있습니다.

테스트 탐색기를 사용하여 테스트 메서드를 실행하는 경우 코드 검사는 선택 사항입니다. 결과 테이블에는 각 어셈블리, 클래스 및 메서드에서 실행되는 코드의 백분율이 표시됩니다. 또한 소스 편집기에는 테스트된 코드가 표시됩니다.

::: moniker range="vs-2017"

![강조 표시된 코드 검사 결과](../test/media/codecoverage1.png)

::: moniker-end

## <a name="requirements"></a>요구 사항

코드 검사 기능은 Visual Studio Enterprise Edition에서만 사용할 수 있습니다.

## <a name="analyze-code-coverage"></a>코드 검사 분석

::: moniker range="vs-2017"

1. **테스트** 메뉴에서 **코드 검사 분석** 을 선택합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. **테스트** 메뉴에서 **모든 테스트에 대한 코드 검사 분석** 을 선택합니다.

   ![VS 2019의 코드 검사 분석 메뉴](../test/media/vs-2019/analyze-code-coverage.png)

   또한 테스트 탐색기 도구 창에서 코드 검사를 실행할 수 있습니다.

::: moniker-end

2. 테스트가 실행된 후 실행된 줄을 확인하려면 **코드 검사 결과** 창에서 ![코드 검사 강조 표시 아이콘](../test/media/codecoverage-showcoloringicon.png) **코드 검사 강조 표시** 를 선택합니다. 기본적으로 테스트에 포함된 코드는 연한 파랑으로 강조됩니다.

   > [!TIP]
   > 색을 변경하거나 굵게 표시하려면 **도구** > **옵션** > **환경** > **글꼴 및 색** > **설정 표시: 텍스트 편집기** 를 선택합니다. **표시 항목** 에서 “검사” 항목(예: **검사가 수행되지 않은 영역**)에 대한 설정을 조정합니다.
   >
   > ![코드 검사 글꼴 및 색](media/vs-2019/coverage-fonts-and-colors.png)

3. 결과에 검사가 낮게 표시되는 경우, 코드에서 실행되지 않은 부분을 확인한 다음 검사할 추가 테스트를 작성합니다. 개발 팀을 일반적으로 약 80%의 코드 검사를 목표로 합니다. 경우에 따라 더 낮은 검사도 허용됩니다. 예를 들어, 일부 코드가 표준 템플릿에서 생성된 경우 낮은 검사가 허용됩니다.

> [!TIP]
> - 컴파일러 최적화 끄기
> - 관리되지 않은(네이티브) 코드를 사용하는 경우 디버그 빌드 사용
> - 각 어셈블리에 대한 .pdb(기호) 파일 생성

예상한 결과를 얻지 못한 경우 [코드 검사 문제 해결](../test/troubleshooting-code-coverage.md)을 참조하세요.

코드를 업데이트한 후 반드시 코드 검사를 다시 실행하세요. 검사 결과 및 코드 강조는 코드를 수정한 후 또는 테스트를 실행한 경우 자동으로 업데이트되지 않습니다.

## <a name="report-in-blocks-or-lines"></a>블록 또는 줄에서 보고

코드 검사는 *블록* 으로 계산됩니다. 블록은 진입점 및 진출점이 정확히 하나씩인 코드입니다.  테스트 실행 중 프로그램의 제어 흐름이 블록을 통과할 경우 해당 블록은 검사된 것으로 계산됩니다. 블록이 사용된 횟수는 결과에 영향을 아무 영향을 미치지 않습니다.

또한 표 머리글에서 **열 추가/제거** 를 선택하여 결과를 줄 단위로 표시할 수 있습니다. 일부 사용자는 백분율이 소스 코드에 표시되는 조각 크기와 더 가깝기 때문에 줄 수를 더 선호합니다. 긴 계산 블록은 여러 줄을 차지하는 경우에도 단일 블록으로 계산됩니다.

> [!TIP]
> 코드 줄에는 코드 블록이 둘 이상 있을 수 있습니다. 이와 같은 경우인 데다 테스트 실행에서 줄의 코드 블록을 모두 실행할 경우에는 하나의 줄로 계산됩니다. 줄에서 코드 블록이 전체가 아닌 일부만 실행되면 이는 부분 줄로 계산됩니다.

## <a name="manage-code-coverage-results"></a>코드 검사 결과 관리

일반적으로 **코드 검사 결과** 창에는 가장 최근 실행 결과가 표시됩니다. 결과는 테스트 데이터를 변경할 경우 또는 매번 테스트의 일부만 실행할 경우 달라집니다.

코드 검사 창은 이전 결과 또는 다른 컴퓨터에서 얻은 결과를 보는 데에도 사용할 수 있습니다.

여러 실행(예: 다른 테스트 데이터를 사용하는 실행)의 결과를 병합할 수 있습니다.

- **이전 결과 집합을 보려면** 드롭다운 메뉴에서 선택합니다. 이 메뉴에는 새 솔루션을 열 때 삭제되는 임시 목록이 표시됩니다.

- **이전 세션의 결과를 보려면** **코드 검사 결과 가져오기** 를 선택하고, 솔루션에서 **TestResults** 폴더를 탐색하고, *.coverage* 파일을 가져옵니다.

   *.coverage* 파일이 생성된 이후 소스 코드가 변경된 경우 검사 강조 표시가 잘못될 수 있습니다.

- **결과를 텍스트 형식으로 읽으려면****코드 검사 결과 내보내기** 를 선택합니다. 그러면 다른 도구로 처리하거나 메일로 쉽게 전송할 수 있는 읽기 가능한 *.coveragexml* 파일이 생성됩니다.

- **결과를 다른 사람에게 전송하려면** *.coverage* 파일 또는 내보낸 *.coveragexml* 파일을 전송합니다. 그런 다음 수신자는 파일을 가져올 수 있습니다. 동일한 버전의 소스 코드가 있으면 검사 강조를 볼 수 있습니다.

## <a name="merge-results-from-different-runs"></a>다른 실행에서 결과 병합

테스트 데이터에 따라 코드에 다른 블록이 사용되는 경우가 있습니다. 따라서 여러 테스트 실행에서 결과를 결합할 수 있습니다.

예를 들어, 입력 "2"로 테스트를 실행할 경우를 가정하면 특정 함수의 50%만 검사됩니다. 입력 “-2”로 다시 테스트를 실행하면 검사 강조 보기에서 함수의 나머지 50%가 검사된 것을 확인할 수 있습니다. 이제 두 테스트 실행의 결과를 병합하면 보고서와 검사 강조 보기에 함수의 100%가 검사된 것으로 나타납니다.

![코드 검사 창의 병합 단추 아이콘](../test/media/codecoverage-mergeicon.png) **코드 검사 결과 병합** 을 사용하여 이 작업을 수행합니다. 최근의 실행 또는 가져온 결과의 조합을 선택할 수 있습니다. 내보낸 결과를 결합하려면 내보낸 결과를 가져와야 합니다.

병합 작업 결과를 저장하려면 **코드 검사 결과 내보내기** 를 사용합니다.

### <a name="limitations-in-merging"></a>병합 제한 사항

- 다른 코드 버전의 검사 데이터를 병합하는 경우 결과가 별도로 표시되지만 결합되지 않습니다. 완전히 결합된 결과를 얻으려면 동일한 빌드의 코드를 사용하고 테스트 데이터만 변경하세요.

- 내보낸 다음 가져온 결과 파일을 병합할 경우 결과를 블록 단위가 아닌 줄 단위로만 볼 수 있습니다. 줄 데이터를 보려면 **열 추가/제거** 명령을 사용합니다.

- ASP.NET 프로젝트 테스트의 결과를 병합할 경우 별도 테스트의 결과가 표시되지만 결합되지는 않습니다. 이는 ASP.NET 아티팩트 자체에만 적용되며, 다른 어셈블리의 결과는 결합됩니다.

## <a name="exclude-elements-from-the-code-coverage-results"></a>코드 검사 결과에서 요소 제외

코드가 텍스트 템플릿에서 생성된 경우와 같이 검사 점수에서 코드의 특정 요소를 제외하려는 경우가 있습니다. <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute?displayProperty=fullName> 특성을 class, struct, method, property, property setter 또는 getter, event 코드 요소에 임의로 추가할 수 있습니다.

> [!TIP]
> 클래스를 제외해도 해당 파생 클래스는 제외되지 않습니다.

다음은 그 예입니다. 

```csharp
using System.Diagnostics.CodeAnalysis;
...
public class ExampleClass1
{
    [ExcludeFromCodeCoverage]
    void ExampleMethod() {...}

    [ExcludeFromCodeCoverage] // exclude property
    int ExampleProperty1
    { get {...} set{...}}

    int ExampleProperty2
    {
        get
        {
            ...
        }
        [ExcludeFromCodeCoverage] // exclude setter
        set
        {
            ...
        }
    }

}
[ExcludeFromCodeCoverage]
class ExampleClass2 { ... }
```

```vb
Imports System.Diagnostics.CodeAnalysis

Class ExampleClass1
    <ExcludeFromCodeCoverage()>
    Public Sub ExampleSub1()
        ...
    End Sub

    ' Exclude property
    < ExcludeFromCodeCoverage()>
    Property ExampleProperty1 As Integer
        ...
    End Property

    ' Exclude setter
    Property ExampleProperty2 As Integer
        Get
            ...
        End Get
        <ExcludeFromCodeCoverage()>
        Set(ByVal value As Integer)
            ...
        End Set
    End Property
End Class

<ExcludeFromCodeCoverage()>
Class ExampleClass2
...
End Class
```

```cpp
// A .cpp file compiled as managed (CLI) code.
using namespace System::Diagnostics::CodeAnalysis;
...
public ref class ExampleClass1
{
  public:
    [ExcludeFromCodeCoverage]
    void ExampleFunction1() { ... }

    [ExcludeFromCodeCoverage]
    property int ExampleProperty2 {...}

    property int ExampleProperty2 {
      int get() { ... }
     [ExcludeFromCodeCoverage]
      void set(int value) { ...  }
   }
}

[ExcludeFromCodeCoverage]
public ref class ExampleClass2
{ ... }
```

### <a name="exclude-elements-in-native-c-code"></a>네이티브 C++ 코드에서 요소 제외

C++ 코드에서 관리되지 않는(네이티브) 요소를 제외하려면

```cpp
#include <CodeCoverage\CodeCoverage.h>
...

// Exclusions must be compiled as unmanaged (native):
#pragma managed(push, off)

// Exclude a particular function:
ExcludeFromCodeCoverage(Exclusion1, L"MyNamespace::MyClass::MyFunction");

// Exclude all the functions in a particular class:
ExcludeFromCodeCoverage(Exclusion2, L"MyNamespace::MyClass2::*");

// Exclude all the functions generated from a particular template:
ExcludeFromCodeCoverage(Exclusion3, L"*::MyFunction<*>");

// Exclude all the code from a particular .cpp file:
ExcludeSourceFromCodeCoverage(Exclusion4, L"*\\unittest1.cpp");

// After setting exclusions, restore the previous managed/unmanaged state:
#pragma managed(pop)
```

다음과 같은 매크로를 사용합니다.

`ExcludeFromCodeCoverage(` *ExclusionName* `, L"` *FunctionName* `");`

`ExcludeSourceFromCodeCoverage(` *ExclusionName* `, L"` *SourceFilePath* `");`

- *ExclusionName* 은 임의의 고유한 이름입니다.

- *FunctionName* 은 정규화된 함수 이름입니다. 와일드 카드를 포함할 수 있습니다. 예를 들어, 클래스의 모든 함수를 제외하려면 `MyNamespace::MyClass::*`를 씁니다.

- *SourceFilePath* 는 .cpp 파일의 로컬 또는 UNC 경로입니다. 와일드 카드를 포함할 수 있습니다. 다음 예제는 특정 디렉터리에서 모든 파일을 제외합니다. `\\MyComputer\Source\UnitTests\*.cpp`

- `#include <CodeCoverage\CodeCoverage.h>`

- 임의의 네임스페이스 또는 클래스 안이 아닌 전역 네임스페이스에 제외 매크로에 대한 호출을 추가합니다.

- 단위 테스트 코드 파일 또는 애플리케이션 코드 파일에 제외를 추가할 수 있습니다.

- 제외는 컴파일러 옵션을 설정하거나 `#pragma managed(off)`를 사용하여 관리되지 않는(네이티브) 코드로 컴파일해야 합니다.

> [!NOTE]
> C++/CLI 코드에서 함수를 제외하려면 함수에 `[System::Diagnostics::CodeAnalysis::ExcludeFromCodeCoverage]` 특성을 적용합니다. C#의 경우에도 동일합니다.

### <a name="include-or-exclude-additional-elements"></a>추가 요소 포함 또는 제외

로드되어 있고 *.pdb* 파일을 *.dll* 또는 *.exe* 파일과 같은 디렉터리에서 사용할 수 있는 어셈블리에서만 코드 검사 분석을 수행할 수 있습니다. 따라서 경우에 따라 적절한 *.pdb* 파일의 사본을 가져와서 포함된 어셈블리 집합을 확장할 수 있습니다.

*.runsettings* 파일을 작성하면 코드 검사 분석에 대해 선택되는 어셈블리와 요소를 더 자세히 제어할 수 있습니다. 예를 들어, 클래스에 특성을 추가하지 않고도 특정 종류의 어셈블리를 제외할 수 있습니다. 자세한 내용은 [코드 검사 분석 사용자 지정](../test/customizing-code-coverage-analysis.md)을 참조하세요.

## <a name="analyze-code-coverage-in-azure-pipelines"></a>Azure Pipelines에서 코드 검사 분석

코드를 체크 인하면 테스트가 다른 팀원의 테스트와 함께 빌드 서버에서 실행됩니다. Azure Pipelines에서 코드 검사를 분석하여 전체 프로젝트에 대한 최신 검사 정보를 전체적으로 파악하는 데 유용합니다. 또한 일반적으로 개발 머신에서 실행하지 않는 자동화된 시스템 테스트와 기타 코딩된 테스트도 포함됩니다. 자세한 내용은 [빌드를 사용하여 단위 테스트 실행](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)을 참조하세요.

## <a name="analyze-code-coverage-from-the-command-line"></a>명령줄에서 코드 검사 분석

명령줄에서 테스트를 실행하려면 *vstest.console.exe* 를 사용합니다. 코드 검사는 *vstest.console.exe* 유틸리티의 옵션입니다.

1. Visual Studio용 개발자 명령 프롬프트를 시작합니다.

   ::: moniker range="vs-2017"

   Windows **시작** 메뉴에서 **Visual Studio 2017** > **VS 2017용 개발자 명령 프롬프트** 를 선택합니다.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   Windows **시작** 메뉴에서 **Visual Studio 2019** > **VS 2019용 개발자 명령 프롬프트** 를 선택합니다.

   ::: moniker-end

2. 명령 프롬프트에서 다음 명령을 실행합니다.

   ```shell
   vstest.console.exe MyTestAssembly.dll /EnableCodeCoverage
   ```

자세한 내용은 [MSTest.exe 명령줄 옵션](vstest-console-options.md)을 참조하세요.

## <a name="troubleshoot"></a>문제 해결

코드 검사 결과가 표시되지 않으면 [코드 검사 문제 해결](../test/troubleshooting-code-coverage.md) 문서가 도움이 될 수 있습니다.

## <a name="see-also"></a>참고 항목

- [코드 검사 분석 사용자 지정](../test/customizing-code-coverage-analysis.md)
- [코드 검사 문제 해결](../test/troubleshooting-code-coverage.md)
- [코드 단위 테스트](../test/unit-test-your-code.md)
