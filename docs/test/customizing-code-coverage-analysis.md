---
title: 코드 검사 분석 사용자 지정
ms.date: 08/21/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 9171afdc6fe5ca65a8ba2bcae81fe255981cdae6
ms.sourcegitcommit: 8217b2ff48028f43c05c5590a293d358897c8651
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475993"
---
# <a name="customize-code-coverage-analysis"></a>코드 검사 분석 사용자 지정

기본적으로 코드 검사는 단위 테스트 중에 로드되는 모든 솔루션 어셈블리를 분석합니다. 이 기본 동작은 대부분은 문제 없이 작동하므로 사용하는 것이 좋습니다. 자세한 내용은 [코드 검사를 사용하여 테스트할 코드 범위 결정](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)을 참조하세요.

코드 검사 결과에서 테스트 코드를 제외하고 애플리케이션 코드만 포함하려면 테스트 클래스에 <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> 특성을 추가합니다.

솔루션의 일부가 아닌 어셈블리를 포함하려면 이러한 어셈블리에 대한 *.pdb* 파일을 얻어서 어셈블리 *.dll* 파일과 동일한 폴더에 복사합니다.

## <a name="run-settings-file"></a>실행 설정 파일

[실행 설정 파일](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)은 유닛 테스트 도구에서 사용하는 구성 파일입니다. 고급 코드 검사 설정은 *.runsettings* 파일에서 지정합니다.

코드 검사를 사용자 지정하려면 다음 단계를 수행합니다.

1. 실행 설정 파일을 솔루션에 추가합니다. **솔루션 탐색기**의 솔루션 바로 가기 메뉴에서 **추가** > **새 항목**, **XML File**을 차례로 선택합니다. 파일을 *CodeCoverage.runsettings*와 같은 이름으로 저장합니다.

2. 이 문서의 끝 부분에 있는 예제 파일에서 콘텐츠를 추가한 다음, 다음 섹션에 설명된 대로 각자의 요구 사항에 맞게 사용자 지정합니다.

::: moniker range="vs-2017"

3. 실행 설정 파일을 선택하려면 **테스트** 메뉴에서 **테스트 설정** > **테스트 설정 파일 선택**을 선택합니다. 명령줄에서 테스트를 실행하기 위한 실행 설정 파일을 지정하려면 [단위 테스트 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file-from-the-command-line)을 참조하세요.

::: moniker-end

::: moniker range=">=vs-2019"

3. 실행 설정 파일을 선택하려면 **테스트** 메뉴에서 **설정 파일 선택**을 선택합니다. 명령줄에서 테스트를 실행하기 위한 실행 설정 파일을 지정하려면 [단위 테스트 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md#specify-a-run-settings-file-from-the-command-line)을 참조하세요.

::: moniker-end

   **코드 검사 분석**을 선택하면 실행 설정 파일에서 구성 정보를 읽습니다.

   > [!TIP]
   > 테스트를 실행하거나 코드를 업데이트하면 이전 코드 검사 결과 및 코드 강조가 자동으로 숨겨지지 않습니다.

::: moniker range="vs-2017"

사용자 지정 설정을 해제하거나 설정하려면 **테스트** > **테스트 설정** 메뉴에서 파일을 선택 취소 또는 선택합니다.

![Visual Studio 2017에서 사용자 지정 설정 파일이 있는 테스트 설정 메뉴](../test/media/codecoverage-settingsfile.png)

::: moniker-end

::: moniker range=">=vs-2019"

사용자 지정 설정을 켜고 끄려면 **테스트** 메뉴에서 파일을 선택 취소 또는 선택합니다.

::: moniker-end

## <a name="symbol-search-paths"></a>기호 검색 경로

코드 검사에는 어셈블리에 대한 기호 파일( *.pdb* 파일)이 필요합니다. 솔루션에서 빌드한 어셈블리의 경우 기호 파일은 대개 이진 파일과 함께 있으며 코드 검사는 자동으로 실행됩니다. 코드 검사 분석에 참조된 어셈블리를 포함하려는 경우가 있습니다. 이런 경우에 *.pdb* 파일이 이진 파일과 가깝지 않을 수 있지만 *.runsettings* 파일에서 기호 검색 경로를 지정할 수 있습니다.

```xml
<SymbolSearchPaths>
      <Path>\\mybuildshare\builds\ProjectX</Path>
      <!--More paths if required-->
</SymbolSearchPaths>
```

> [!NOTE]
> 기호 확인은 어셈블리가 많은 원격 파일 위치를 사용할 경우 특히 오래 걸릴 수 있습니다. 따라서 *.pdb* 파일을 이진( *.dll* 및.*exe*) 파일과 같은 로컬 위치에 복사하는 것이 좋습니다.

## <a name="include-or-exclude-assemblies-and-members"></a>어셈블리와 멤버 포함 또는 제외

어셈블리 또는 특정 형식과 멤버를 코드 검사 분석에 포함하거나 제외할 수 있습니다. **포함** 섹션이 비어 있거나 생략된 경우, 관련 PDB 파일이 있는 로드된 어셈블리가 모두 포함됩니다. **제외** 섹션의 절과 일치하는 어셈블리나 멤버는 코드 검사에서 제외됩니다. **제외** 섹션이 **포함** 섹션보다 우선 적용되므로, **포함** 및 **제외**에 모두 나열된 어셈블리는 코드 검사에 포함되지 않습니다.

예를 들어 다음 XML은 이름을 지정하여 단일 어셈블리를 제외합니다.

```xml
<ModulePaths>
  <Exclude>
   <ModulePath>.*Fabrikam.Math.UnitTest.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Exclude>
</ModulePaths>
```

다음 예제에서는 단일 어셈블리만 코드 검사에 포함되도록 지정합니다.

```xml
<ModulePaths>
  <Include>
   <ModulePath>.*Fabrikam.Math.dll</ModulePath>
   <!-- Add more ModulePath nodes here. -->
  </Include>
</ModulePaths>
```

다음 표에서는 코드 검사에 포함하거나 제외할 어셈블리와 멤버를 찾는 다양한 방법을 보여 줍니다.

| XML 요소 | 일치 항목 |
| - | - |
| ModulePath | 어셈블리 이름 또는 파일 경로로 지정된 어셈블리를 찾습니다. |
| CompanyName | **회사** 특성으로 어셈블리를 찾습니다. |
| PublicKeyToken | 퍼블릭 키 토큰으로 서명된 어셈블리를 찾습니다. |
| 원본 | 요소가 정의된 소스 파일의 경로 이름으로 요소를 찾습니다. |
| attribute | 지정된 특성이 있는 요소를 찾습니다. 특성의 전체 이름을 지정합니다(예: `<Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>`).<br/><br/><xref:System.Runtime.CompilerServices.CompilerGeneratedAttribute> 특성을 제외하면 `async`, `await`, `yield return` 및 자동 구현 속성과 같은 언어 기능을 사용하는 코드가 코드 검사 분석에서 제외됩니다. 실제로 생성된 코드를 제외하려면 <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> 특성만 제외합니다. |
| 함수 | 매개 변수 목록을 포함하여 정규화된 이름으로 프로시저, 함수 또는 메서드를 찾습니다. [정규식](#regular-expressions)을 사용하여 이름의 일부를 찾을 수도 있습니다.<br/><br/>예제:<br/><br/>`Fabrikam.Math.LocalMath.SquareRoot(double);` (C#)<br/><br/>`Fabrikam::Math::LocalMath::SquareRoot(double)`(C++) |

### <a name="regular-expressions"></a>정규식

Include 및 Exclude 노드는 와일드카드와 동일하지 않은 정규식을 사용합니다. 모든 일치 항목은 대소문자를 구분하지 않습니다. 예는 다음과 같습니다.

- **.\*** 은(는) 모든 문자의 문자열과 일치합니다.

- **\\.** 점 “.”과 일치합니다.

- **\\(   \\)** 는 괄호 “(  )”와 일치합니다.

- **\\\\** 파일 경로 구분 기호 “\\”와 일치합니다.

- **^** 는 문자열의 시작과 일치합니다.

- **$** 는 문자열의 끝과 일치합니다.

다음 XML은 정규식을 사용하여 특정 어셈블리를 포함하고 제외하는 방법을 보여 줍니다.

```xml
<ModulePaths>
  <Include>
    <!-- Include all loaded .dll assemblies (but not .exe assemblies): -->
    <ModulePath>.*\.dll$</ModulePath>
  </Include>
  <Exclude>
    <!-- But exclude some assemblies: -->
    <ModulePath>.*\\Fabrikam\.MyTests1\.dll$</ModulePath>
    <!-- Exclude all file paths that contain "Temp": -->
    <ModulePath>.*Temp.*</ModulePath>
  </Exclude>
</ModulePaths>
```

다음 XML은 정규식을 사용하여 특정 함수를 포함하고 제외하는 방법을 보여 줍니다.

```xml
<Functions>
  <Include>
    <!-- Include methods in the Fabrikam namespace: -->
    <Function>^Fabrikam\..*</Function>
    <!-- Include all methods named EqualTo: -->
    <Function>.*\.EqualTo\(.*</Function>
  </Include>
  <Exclude>
    <!-- Exclude methods in a class or namespace named UnitTest: -->
    <Function>.*\.UnitTest\..*</Function>
  </Exclude>
</Functions>
```

> [!WARNING]
> 이스케이프되지 않은 괄호 또는 일치하지 않는 괄호와 같이 정규식에 오류가 있는 경우 코드 검사 분석이 실행되지 않습니다.

정규식에 대한 자세한 내용은 [Visual Studio에서 정규식 사용](../ide/using-regular-expressions-in-visual-studio.md)을 참조하세요.

## <a name="sample-runsettings-file"></a>샘플 .runsettings 파일

이 코드를 복사하고 필요에 따라 편집합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- File name extension must be .runsettings -->
<RunSettings>
  <DataCollectionRunSettings>
    <DataCollectors>
      <DataCollector friendlyName="Code Coverage" uri="datacollector://Microsoft/CodeCoverage/2.0" assemblyQualifiedName="Microsoft.VisualStudio.Coverage.DynamicCoverageDataCollector, Microsoft.VisualStudio.TraceCollector, Version=11.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a">
        <Configuration>
          <CodeCoverage>
<!--
Additional paths to search for .pdb (symbol) files. Symbols must be found for modules to be instrumented.
If .pdb files are in the same folder as the .dll or .exe files, they are automatically found. Otherwise, specify them here.
Note that searching for symbols increases code coverage runtime. So keep this small and local.
-->
<!--
            <SymbolSearchPaths>
                   <Path>C:\Users\User\Documents\Visual Studio 2012\Projects\ProjectX\bin\Debug</Path>
                   <Path>\\mybuildshare\builds\ProjectX</Path>
            </SymbolSearchPaths>
-->

<!--
About include/exclude lists:
Empty "Include" clauses imply all; empty "Exclude" clauses imply none.
Each element in the list is a regular expression (ECMAScript syntax). See /visualstudio/ide/using-regular-expressions-in-visual-studio.
An item must first match at least one entry in the include list to be included.
Included items must then not match any entries in the exclude list to remain included.
-->

            <!-- Match assembly file paths: -->
            <ModulePaths>
              <Include>
                <ModulePath>.*\.dll$</ModulePath>
                <ModulePath>.*\.exe$</ModulePath>
              </Include>
              <Exclude>
                <ModulePath>.*CPPUnitTestFramework.*</ModulePath>
              </Exclude>
            </ModulePaths>

            <!-- Match fully qualified names of functions: -->
            <!-- (Use "\." to delimit namespaces in C# or Visual Basic, "::" in C++.)  -->
            <Functions>
              <Exclude>
                <Function>^Fabrikam\.UnitTest\..*</Function>
                <Function>^std::.*</Function>
                <Function>^ATL::.*</Function>
                <Function>.*::__GetTestMethodInfo.*</Function>
                <Function>^Microsoft::VisualStudio::CppCodeCoverageFramework::.*</Function>
                <Function>^Microsoft::VisualStudio::CppUnitTestFramework::.*</Function>
              </Exclude>
            </Functions>

            <!-- Match attributes on any code element: -->
            <Attributes>
              <Exclude>
                <!-- Don't forget "Attribute" at the end of the name -->
                <Attribute>^System\.Diagnostics\.DebuggerHiddenAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.DebuggerNonUserCodeAttribute$</Attribute>
                <Attribute>^System\.CodeDom\.Compiler\.GeneratedCodeAttribute$</Attribute>
                <Attribute>^System\.Diagnostics\.CodeAnalysis\.ExcludeFromCodeCoverageAttribute$</Attribute>
              </Exclude>
            </Attributes>

            <!-- Match the path of the source files in which each method is defined: -->
            <Sources>
              <Exclude>
                <Source>.*\\atlmfc\\.*</Source>
                <Source>.*\\vctools\\.*</Source>
                <Source>.*\\public\\sdk\\.*</Source>
                <Source>.*\\microsoft sdks\\.*</Source>
                <Source>.*\\vc\\include\\.*</Source>
              </Exclude>
            </Sources>

            <!-- Match the company name property in the assembly: -->
            <CompanyNames>
              <Exclude>
                <CompanyName>.*microsoft.*</CompanyName>
              </Exclude>
            </CompanyNames>

            <!-- Match the public key token of a signed assembly: -->
            <PublicKeyTokens>
              <!-- Exclude Visual Studio extensions: -->
              <Exclude>
                <PublicKeyToken>^B77A5C561934E089$</PublicKeyToken>
                <PublicKeyToken>^B03F5F7F11D50A3A$</PublicKeyToken>
                <PublicKeyToken>^31BF3856AD364E35$</PublicKeyToken>
                <PublicKeyToken>^89845DCD8080CC91$</PublicKeyToken>
                <PublicKeyToken>^71E9BCE111E9429C$</PublicKeyToken>
                <PublicKeyToken>^8F50407C4E9E73B6$</PublicKeyToken>
                <PublicKeyToken>^E361AF139669C375$</PublicKeyToken>
              </Exclude>
            </PublicKeyTokens>

            <!-- We recommend you do not change the following values: -->

            <!-- Set this to True to collect coverage information for functions marked with the "SecuritySafeCritical" attribute. Instead of writing directly into a memory location from such functions, code coverage inserts a probe that redirects to another function, which in turns writes into memory. -->
            <UseVerifiableInstrumentation>True</UseVerifiableInstrumentation>
            <!-- When set to True, collects coverage information from child processes that are launched with low-level ACLs, for example, UWP apps. -->
            <AllowLowIntegrityProcesses>True</AllowLowIntegrityProcesses>
            <!-- When set to True, collects coverage information from child processes that are launched by test or production code. -->
            <CollectFromChildProcesses>True</CollectFromChildProcesses>
            <!-- When set to True, restarts the IIS process and collects coverage information from it. -->
            <CollectAspDotNet>False</CollectAspDotNet>

          </CodeCoverage>
        </Configuration>
      </DataCollector>
    </DataCollectors>
  </DataCollectionRunSettings>
</RunSettings>
```

## <a name="see-also"></a>참고 항목

- [실행 설정 파일을 사용하여 단위 테스트 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [코드 검사를 사용하여 테스트할 코드 범위 결정](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
- [코드 단위 테스트](../test/unit-test-your-code.md)
