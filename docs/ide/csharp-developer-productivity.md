---
title: .NET 개발을 위한 생산성 향상
description: .NET 코드를 더 신속하게 작성할 수 있는 탐색, 코드 분석, 단위 테스트 및 기타 기능의 개요입니다.
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 0aa8e19f2be78671587dd1d9bc6254306c82a78c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567504"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>C# 개발자용 Visual Studio 생산성 가이드

Visual Studio에서 개발자 생산성을 높이는 방법을 알아봅니다. 디컴파일된 어셈블리 탐색, 입력 시 변수 이름 제안, **테스트 탐색기**의 계층 구조 보기, 파일/형식/멤버/기호 선언으로 이동하는 전체로 이동(**Ctrl**+**T**), 지능형 **예외 도우미**, 코드 스타일 구성 및 적용, 많은 리팩터링 및 코드 수정 등의 성능 및 생산성 향상 기능을 활용합니다.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>다른 편집기의 바로 가기 키에 익숙함

::: moniker range="vs-2017"

**Visual Studio 2017 버전 15.8의 새로운 기능**

::: moniker-end

다른 IDE 또는 코딩 환경에서 전환하는 경우 키보드 구성표를 *Visual Studio Code* 또는 *ReSharper(Visual Studio)* 로 변경할 수 있습니다.

![Visual Studio의 키보드 구성표](../ide/media/VS2017Guide-Keyboard.png)

또한 일부 확장은 키보드 구성표를 제공합니다.

- [Visual Studio용 바로 가기 키(ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Emacs 에뮬레이션](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

다음은 많이 사용되는 Visual Studio 바로 가기입니다.

| 바로 가기(모든 프로필) | 명령 | 설명 |
|-|-|-|
| **Ctrl**+**T** | 전체로 이동 | 임의 파일, 형식, 멤버 또는 기호 선언으로 이동 |
| **F12**(또는 **Ctrl**+**클릭**) | 정의로 이동 | 기호가 정의된 위치로 이동 |
| **Ctrl**+**F12** | 구현으로 이동 | 모든 베이스 형식 또는 멤버에서 다양한 구현으로 이동 |
| **Shift**+**F12** | 모든 참조 찾기 | 모든 기호 또는 리터럴 참조 보기 |
| **Alt**+**홈** | 기본으로 이동 | 상속 체인 탐색 |
| **Ctrl**+ **.** (또는 C# 프로필에서 **Alt**+**Enter**) | 빠른 작업 및 리팩터링 | 커서 위치 또는 코드 선택에서 사용 가능한 코드 해결, 코드 생성 작업, 리팩터링, 또는 기타 빠른 작업 확인 |
| **Ctrl**+**D** | 중복된 줄 | 커서가 있는 코드 줄 복제(**Visual Studio 2017 버전 15.6** 이상에서 사용 가능) |
| **Shift**+**Alt**+ **+** / **-** | 선택 영역을 확대/축소 | 편집기(**Visual Studio 2017 버전 15.5** 이상에서 사용 가능)에서 현재 선택 영역을 확장하거나 축소 |
| **Shift** + **Alt** +  **.** | 일치하는 다음 캐럿 삽입 | 현재 선택 영역과 일치하는 다음 위치에서 선택 영역 및 캐럿 추가(**Visual Studio 2017 버전 15.8** 이상에서 사용할 수 있음) |
| **Ctrl**+**Q** | 검색 | 모든 Visual Studio 설정 검색 |
| **F5** | 디버깅 시작 | 애플리케이션 디버깅 시작 |
| **Ctrl**+**F5** | 디버깅하지 않고 실행 | 디버깅하지 않고 애플리케이션을 로컬에서 실행 |
| **Ctrl**+**K**,**D**(기본 프로필) 또는 **Ctrl**+**E**,**D**(C# 프로필) | 문서 서식 | 줄 바꿈, 간격 및 들여쓰기 설정에 따라 파일에서 서식 위반 정리 |
| **Ctrl**+ **\\** ,**Ctrl**+**E**(기본 프로필) 또는 **Ctrl**+**W**,**E**(C# 프로필) | 오류 목록 보기 | 문서, 프로젝트 또는 솔루션의 모든 오류 보기 |
| **Alt** + **PgUp/PgDn** | 다음/이전 문제로 이동 | 문서에서 이전/다음 오류, 경고, 제안으로 이동(**Visual Studio 2017 버전 15.8** 이상에서 사용할 수 있음) |
| **Ctrl**+**K**, **/** | 한 줄로 된 주석 처리/주석 처리 제거 전환 | 이 명령은 선택 영역이 이미 주석으로 처리되었는지 여부에 따라 한 줄로 된 주석을 추가하거나 제거합니다. |
| **Ctrl**+**Shift**+ **/** | 블록 주석 처리/주석 처리 제거 전환 | 이 명령은 선택 영역에 따라 블록 주석을 추가하거나 제거합니다. |

> [!NOTE]
> 기본 Visual Studio keybindings의 바인딩을 해제한 일부 확장 위의 명령을 사용하려면 **도구** > **설정 가져오기 및 내보내기** > **모든 설정 다시 설정** 또는 **도구** > **옵션** > **키보드** > **다시 설정**으로 이동하여 Visual Studio의 기본값으로 키 바인딩을 복원합니다.

바로 가기 키와 명령에 대한 자세한 내용은 [생산성 바로 가기](../ide/productivity-shortcuts.md) 및 [인기 바로 가기 키](default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)를 참조하세요.

## <a name="navigate-quickly-to-files-or-types"></a>파일 또는 형식으로 빠르게 이동

Visual Studio에는 **전체로 이동**(**Ctrl**+**T**) 기능이 있습니다. **전체로 이동**은 사용자를 모든 파일, 형식, 멤버 또는 기호 선언으로 빠르게 이동하게 할 수 있습니다.

- 이 검색 창의 위치를 변경하거나, **기어** 아이콘을 사용하여 라이브 탐색 미리 보기를 끕니다.
- `t mytype` 등의 구문을 사용하여 결과를 필터링합니다.
- 검색 범위를 현재 문서만으로 지정합니다.
- 카멜 대/소문자 일치가 지원됩니다.

![Visual Studio에서 전체로 이동](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>코드 스타일 규칙 적용

EditorConfig 파일을 사용하여 코딩 규칙을 체계화하고 소스와 규칙을 함께 유지할 수 있습니다.

![Visual Studio에서 코드 스타일 적용](../ide/media/VSGuide_CodeStyle.png)

- **추가** > **새 항목**을 선택하여 기본 또는 .NET 스타일 EditorConfig 파일을 프로젝트에 추가합니다. **새 항목 추가** 대화 상자에서 “editorconfig”를 검색합니다. **editorconfig 파일** 항목 템플릿 중 하나를 선택하고 **추가**를 선택합니다.

   ![Visual Studio의 EditorConfig 항목 템플릿](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- **도구** > **옵션** > **텍스트 편집기** > **C#** > **코드 스타일**의 코드 스타일 설정에 따라 *.editorconfig* 파일을 자동으로 만듭니다.

   ![VS 2019의 설정에서 .editorconfig 파일 생성](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- IntelliCode for Visual Studio의 [코드 유추 기능](/visualstudio/intellicode/code-style-inference)은 기존 코드에서 코드 스타일을 유추합니다. 그런 다음, 이미 정의된 코드 스타일 기본 설정을 사용하여 비어 있지 않은 EditorConfig 파일을 만듭니다.

- 편집기를 통해 코드 스타일 규칙의 심각도 수준을 직접 구성합니다. 현재 .editorconfig 파일이 없으면 해당 파일 하나가 생성됩니다. 오류, 경고 또는 제안 위에 커서를 올리고 **Ctrl**+ **.** 을 입력하여 [빠른 작업 및 리팩터링] 메뉴를 엽니다. **문제 구성 또는 표시 안 함**을 선택합니다. 그런 다음 규칙을 선택하고 해당 규칙에 대해 구성할 심각도 수준을 선택합니다. 그러면 기존 EditorConfig가 규칙의 새 심각도로 업데이트됩니다.

   ![편집기에서 코드 스타일 규칙의 심각도 수준을 직접 구성](../ide/media/configure-severity-level.png)

[.NET 코딩 규칙 옵션](editorconfig-code-style-settings-reference.md) 문서를 확인합니다. 이 문서에는 전체 EditorConfig 파일 예제도 포함되어 있습니다.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>코드 정리

Visual Studio는 **코드 정리** 기능을 통해 코드 스타일 기본 설정을 비롯한 코드 파일의 서식 지정을 요청 시 제공합니다. 코드 정리를 실행하려면 편집기의 맨 아래에 있는 빗자루 아이콘을 클릭하거나 **Ctrl**+**K** **Ctrl**+**E**를 누릅니다.

![Visual Studio 2019의 코드 정리 단추](media/execute-code-cleanup.png)

전체 프로젝트 또는 솔루션에서 코드 정리를 실행할 수도 있습니다. **솔루션 탐색기**에서 프로젝트 또는 솔루션 이름을 마우스 오른쪽 단추로 클릭하고 **분석 및 코드 정리**를 선택한 다음, **코드 정리 실행**을 선택합니다.

![전체 프로젝트 또는 솔루션에서 코드 정리 실행](media/run-code-cleanup-project-solution.png)

파일에서 공백, 들여쓰기 등의 서식을 지정하는 것 외에, **코드 정리**는 선택된 코드 스타일도 적용합니다. 각 코드 스타일의 기본 설정은 [EditorConfig 파일](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)(프로젝트에 대해 설정된 경우) 또는 **옵션** 대화 상자의 [코드 스타일 설정](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box)에서 읽어옵니다.

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>리팩터링 및 코드 수정

Visual Studio에는 많은 리팩터링, 코드 생성 작업 및 코드 수정이 있습니다. 빨간색 오류 표시선은 오류를 나타내며, 녹색 오류 표시선은 경고를 나타내고, 세 개의 회색 점은 코드 제안 사항을 나타냅니다. 전구 또는 스크루드라이버 아이콘을 클릭하거나 **Ctrl**+ **.** 또는 **Alt**+**Enter**를 눌러 코드 수정에 액세스할 수 있습니다. 각 수정 사항은 수정 작업 방식의 라이브 코드 diff를 보여주는 미리 보기 창이 함께 제공됩니다.

인기 있는 빠른 수정 및 리팩터링은 다음과 같습니다.

- 이름 바꾸기
- 메서드 추출
- 메서드 시그니처 변경
- 생성자 생성
- 메서드 생성
- 형식을 파일로 이동
- Null 검사 추가
- 매개 변수 추가
- 불필요한 using 제거
- LINQ 쿼리 또는 LINQ 메서드에 대한 Foreach 루프
- 멤버 끌어오기

자세한 내용은 [코드 생성 기능](code-generation-in-visual-studio.md)을 참조하세요.

[FxCop 분석기를 설치](../code-quality/install-fxcop-analyzers.md)하여 코드 문제에 플래그를 지정할 수 있습니다. 또는 [Roslyn 분석기](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix)를 사용하여 고유한 리팩터링 또는 코드 수정을 작성하세요.

여러 커뮤니티 회원이 다음과 같은 코드 검사를 추가하는 무료 확장을 작성했습니다.

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint for Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

![Visual Studio에서 리팩터링](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>사용량 찾기, 구현으로 이동, 디컴파일된 어셈블리 탐색

Visual Studio에는 [코드를 탐색](../ide/navigating-code.md)하고 검색하는 데 도움이 되는 여러 가지 기능이 있습니다.

| 기능 | 바로 가기 | 세부 정보/개선 사항 |
|- | - | -|
| 모든 참조 찾기 | **Shift**+**F12**| 결과에는 색이 지정되며 프로젝트, 정의, 참조 형식(예: 읽기 또는 쓰기)별로 그룹화할 수 있습니다. 결과를 “잠글” 수도 있습니다. |
| 구현으로 이동 | **Ctrl**+**F12** | `override` 키워드에서 [정의로 이동]을 사용하여 재정의된 멤버로 이동할 수 있습니다. |
| 정의로 이동 | **F12** 또는 **Ctrl**+**클릭**| 정의로 이동하려면 **Ctrl** 키를 누른 채 클릭합니다. |
| 정의 피킹(Peeking) | **Alt**+**F12** | 정의의 인라인 보기 |
| 구조체 시각화 도우미 | 괄호 사이의 회색 점선 | 코드 구조를 보려면 가리키기 |
| 디컴파일된 어셈블리 탐색 | **F12** 또는 **Ctrl**+**클릭** | 다음 기능을 활성화하여 외부 소스(ILSpy로 디컴파일됨)로 이동합니다. **도구** > **옵션** > **텍스트 편집기** > **C#**  > **고급** > **디컴파일된 소스에 탐색을 사용하도록 설정**. |

![전체로 이동 및 모든 참조 찾기](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>개선된 IntelliSense

IntelliCode for Visual Studio를 사용하여 사전순 목록 대신 [컨텍스트 인식 코드 완성](/visualstudio/intellicode/intellicode-visual-studio)을 가져옵니다. 고유한 도메인 특정 라이브러리를 기준으로 [사용자 지정 IntelliSense 모델](/visualstudio/intellicode/custom-model-faq)을 학습할 수도 있습니다.

## <a name="unit-testing"></a>단위 테스트

Visual Studio 2017부터 테스트 환경의 기능이 훨씬 개선되었습니다. MSTest v1, MSTest v2, NUnit 또는 XUnit 테스트 프레임워크를 사용하여 테스트할 수 있습니다.

- **테스트 탐색기** 테스트 검색은 속도가 빠릅니다.

- ‘계층 구조 정렬’을 사용하여 **테스트 탐색기**에서 테스트를 구성합니다. 

   ![Visual Studio에서 텍스트 탐색기의 계층 구조 뷰](../ide/media/VSGuide_Testing.png)

- [Live Unit Testing](../test/live-unit-testing.md)은 계속 코드 변경으로 영향을 받는 테스트를 실행하며 테스트 상태를 알려주는 인라인 편집기 아이콘을 업데이트합니다. 라이브 테스트 집합에서 특정 테스트 또는 테스트 프로젝트를 포함하거나 제외합니다. (Visual Studio Enterprise Edition만 해당)

## <a name="debugging"></a>디버깅

Visual Studio의 몇 가지 디버깅 기능은 다음과 같습니다.

::: moniker range=">=vs-2019"

- **조사식**, **자동** 및 **로컬** 창에서 문자열을 검색할 수 있습니다.
- ‘클릭한 줄까지 실행’을 사용하면 코드 줄 옆을 가리키고, 나타나는 녹색 ‘재생’ 아이콘을 누르고, 해당 줄에 도달할 때까지 프로그램을 실행할 수 있습니다. 
- **예외 도우미**는 어떤 변수가 `NullReferenceException`에서 `null`인지와 같은 가장 중요한 정보를 대화 상자의 최상위 수준에 배치합니다.
- [뒤로 이동 디버깅](../debugger/view-historical-application-state.md)을 사용하면 이전 중단점 또는 단계로 돌아가서 과거의 애플리케이션 상태를 볼 수 있습니다.
- [스냅샷 디버깅](/azure/application-insights/app-insights-snapshot-debugger)을 사용하면 예외가 throw되는 때에 라이브 웹 애플리케이션의 상태를 확인할 수 있습니다(Azure에 있어야 함).

::: moniker-end

::: moniker range="vs-2017"

- ‘클릭한 줄까지 실행’을 사용하면 코드 줄 옆을 가리키고, 나타나는 녹색 ‘재생’ 아이콘을 누르고, 해당 줄에 도달할 때까지 프로그램을 실행할 수 있습니다. 
- **예외 도우미**는 어떤 변수가 `NullReferenceException`에서 `null`인지와 같은 가장 중요한 정보를 대화 상자의 최상위 수준에 배치합니다.
- [뒤로 이동 디버깅](../debugger/view-historical-application-state.md)을 사용하면 이전 중단점 또는 단계로 돌아가서 과거의 애플리케이션 상태를 볼 수 있습니다.
- [스냅샷 디버깅](/azure/application-insights/app-insights-snapshot-debugger)을 사용하면 예외가 throw되는 때에 라이브 웹 애플리케이션의 상태를 확인할 수 있습니다(Azure에 있어야 함).

::: moniker-end

![Visual Studio의 예외 도우미](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>버전 제어

git 또는 TFVC를 사용하여 Visual Studio에서 코드를 저장하고 업데이트할 수 있습니다.

::: moniker range=">=vs-2019"

- [Visual Studio용 끌어오기 요청](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs)을 설치하여 Visual Studio를 나가지 않고 끌어오기 요청을 만들고, 검토, 체크 아웃, 실행합니다.

::: moniker-end

- [팀 탐색기](reference/team-explorer-reference.md)에서 로컬 변경 내용을 구성하고, 상태 표시줄을 사용하여 보류 중인 커밋과 변경 내용을 추적합니다.

- [Visual Studio용 지속적인 업데이트 도구](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) 확장을 사용하여 Visual Studio 내부에 ASP.NET 프로젝트에 대한 연속 통합 및 지속적인 업데이트를 설정합니다.

![Visual Studio에서 소스 제어](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>알아야 할 다른 기능은 무엇인가요?

코드 작성을 보다 효율적으로 하기 위한 편집기 및 생산성 기능 목록입니다. 일부 기능은 기본적으로 꺼져 있으므로 사용하도록 설정해야 할 수 있습니다(해당 기능은 머신에서 인덱싱할 수 있거나, 논란의 여지가 있거나, 현재 실험적임).

| 기능 | 설명 | 사용 방법 |
|-|-|-|
| 솔루션 탐색기에서 파일 찾기 | **솔루션 탐색기**에서 활성 파일 강조 표시 | **솔루션 탐색기의 도구** > **옵션** > **프로젝트 및 솔루션** > **활성 항목 추적** |
| 참조 어셈블리 및 NuGet 패키지의 형식에 대한 using 추가 | 참조되지 않은 형식의 NuGet 패키지를 설치하기 위한 코드 수정이 포함된 오류 전구 표시 | **도구** > **옵션** > **텍스트 편집기** > **C#**  > **고급** > **참조 어셈블리의 형식에 대한 using 제안** 및 **NuGet 패키지의 형식에 대한 using 제안** |
| 전체 솔루션 분석 사용 | **오류 목록**에서 솔루션의 모든 오류 보기 | **도구** > **옵션** > **텍스트 편집기** > **C#**  > **고급** > **전체 솔루션 분석 사용** |
| 디컴파일된 소스에 탐색을 사용하도록 설정 | 외부 소스에서 형식/멤버에 대한 정의로 이동하고, 메서드 본문을 표시하기 위해 ILSpy 디컴파일러를 사용할 수 있습니다. | **도구** > **옵션** > **텍스트 편집기** > **C#**  > **고급** > **Enable navigation to decompiled sources(디컴파일된 소스에 탐색을 사용하도록 설정)** |
| 완료/제안 모드 | IntelliSense의 완료 동작을 변경합니다. IntelliJ 경험이 있는 개발자는 여기서 기본값이 아닌 설정을 사용하기도 합니다. | **메뉴** > **편집** > **IntelliSense** > **완료 모드 설정/해제** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | 편집기에서 코드 참조 정보 및 변경 내용을 표시합니다. (소스 제어 CodeLens 표시기는 Visual Studio Community Edition에서 사용할 수 없습니다.) | **도구** > **옵션** > **텍스트 편집기** > **모든 언어** > **CodeLens** |
| [코드 조각](../ide/visual-csharp-code-snippets.md) | 일반 상용구 코드 제거 지원 | 코드 조각 이름을 입력하고 **탭** 키를 두 번 누릅니다. |
