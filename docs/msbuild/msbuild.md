---
title: MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2387526860b7d6da136a72cf83727f6714e2e52
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633072"
---
# <a name="msbuild"></a>MSBuild

Microsoft Build Engine은 애플리케이션을 빌드하기 위한 플랫폼입니다. MSBuild라고도 하는 이 엔진은 빌드 플랫폼에서 소프트웨어를 처리하고 빌드하는 방법을 제어하는 프로젝트 파일에 대한 XML 스키마를 제공합니다. Visual Studio는 MSBuild를 사용하지만 Visual Studio에 종속되지 않습니다. 프로젝트 또는 솔루션 파일에서 *msbuild.exe*를 호출하여 Visual Studio가 설치되지 않은 환경에서 제품을 조정하고 빌드할 수 있습니다.

 Visual Studio는 MSBuild를 사용하여 관리되는 프로젝트를 로드하고 빌드합니다. Visual Studio의 프로젝트 파일( *.csproj*, *.vbproj*, *.vcxproj* 등)에는 IDE를 사용하여 프로젝트를 빌드할 때 실행되는 MSBuild XML 코드가 들어 있습니다. Visual Studio 프로젝트는 필요한 모든 설정을 가져오고 일반적인 개발 작업을 수행하는 프로세스를 빌드하지만 Visual Studio 내에서 또는 XML 편집기를 사용하여 확장하거나 수정할 수 있습니다.

 C++의 MSBuild에 대한 자세한 내용은 [MSBuild(C++)](/cpp/build/msbuild-visual-cpp)를 참조하세요.

 다음 예제에서는 Visual Studio IDE 대신 명령줄에서 MSBuild를 호출하여 빌드를 실행할 수 있는 경우를 보여줍니다.

- Visual Studio가 설치되지 않은 경우. ([Visual Studio 없이 MSBuild 다운로드](https://visualstudio.microsoft.com/downloads/?q=build+tools))

- 64비트 버전의 MSBuild를 사용하려는 경우. 이 버전의 MSBuild는 일반적으로 필요하지 않지만 MSBuild에서 더 많은 메모리에 액세스할 수 있도록 합니다.

- 여러 프로세스에서 빌드를 실행하려는 경우. 그러나 C++ 및 C#으로 작성한 프로젝트에서는 IDE를 사용하여 동일한 결과를 얻을 수 있습니다.

- 빌드 시스템을 수정하려는 경우. 예를 들어 다음과 같은 작업을 사용하도록 설정할 수 있습니다.

  - 컴파일러에 도달하기 전에 파일을 전처리합니다.

  - 빌드 출력을 다른 위치로 복사합니다.

  - 빌드 출력에서 압축 파일을 만듭니다.

  - 후처리 단계를 수행합니다. 예를 들어 다른 버전으로 어셈블리에 스탬프를 지정할 수 있습니다.

Visual Studio IDE에서 코드를 작성하지만 MSBuild를 사용하여 빌드를 실행할 수 있습니다. 또는 개발 컴퓨터의 IDE에서 코드를 빌드하지만 명령줄에서 MSBuild를 실행하여 여러 개발자가 통합한 코드를 작성할 수 있습니다. MSBuild를 사용하는 [.NET Core CLI(명령줄 인터페이스)](/dotnet/core/tools/)를 사용하여 .NET Core 프로젝트를 빌드할 수도 있습니다.

> [!NOTE]
> Azure Pipelines를 사용하여 애플리케이션을 자동으로 컴파일, 테스트 및 배포할 수 있습니다. 개발자가 코드를 체크 인할 때(예: 연속 통합 전략의 일부로) 또는 일정에 따라(예: 야간 빌드 확인 테스트 빌드) 빌드 시스템에서 빌드를 자동으로 실행할 수 있습니다. Azure Pipelines는 MSBuild를 사용하여 코드를 컴파일합니다. 자세한 내용은 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)를 참조하세요.

이 문서는 MSBuild에 대한 개요를 제공합니다. 입문용 자습서는 [연습: MSBuild 사용](../msbuild/walkthrough-using-msbuild.md)을 참조하세요.

## <a name="use-msbuild-at-a-command-prompt"></a>명령 프롬프트에서 MSBuild 사용

 명령 프롬프트에서 MSBuild를 실행하려면 적절한 명령줄 옵션과 함께 프로젝트 파일을 *MSBuild.exe*에 전달합니다. 명령줄 옵션을 사용하여 속성을 설정하고 특정 대상을 실행하며 빌드 프로세스를 제어하는 다른 옵션을 설정할 수 있습니다. 예를 들어 다음 명령줄 구문을 사용하여 `Configuration` 속성을 `Debug`로 설정하여 *MyProj.proj* 파일을 빌드합니다.

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 MSBuild 명령줄 옵션에 대한 자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)에서 확인하세요.

> [!IMPORTANT]
> 프로젝트를 다운로드하기 전에 코드를 신뢰할 수 있는지 확인하십시오.

## <a name="project-file"></a>프로젝트 파일

 MSBuild는 간단하고 확장 가능한 XML 기반 프로젝트 파일 형식을 사용합니다. MSBuild 프로젝트 파일 형식을 통해 개발자는 빌드할 항목뿐만 아니라 항목을 다른 운영 체제 및 구성에 대해 빌드하는 방법을 설명합니다. 또한 프로젝트 파일 형식을 통해 개발자는 개별 파일로 분해될 수 있는 다시 사용 가능한 빌드 규칙을 작성하여 해당 제품 내의 여러 프로젝트에서 일관성 있는 빌드를 수행할 수 있습니다.

 다음 단원에서는 MSBuild 프로젝트 파일 형식의 몇 가지 기본 요소에 대해 설명합니다. 기본 프로젝트 파일을 만드는 방법에 대한 자습서는 [연습: 처음부터 MSBuild 프로젝트 파일 만들기](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)를 진행해 보세요.

### <a name="BKMK_Properties"></a> 속성

 속성은 빌드를 구성하는 데 사용될 수 있는 키/값 쌍을 나타냅니다. 속성 이름을 포함하는 요소를 [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) 요소의 자식으로 만들어 속성을 선언합니다. 예를 들어 다음 코드는 값이 `BuildDir`인 `Build`이라는 속성을 만듭니다.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 요소에 `Condition` 특성을 포함하여 속성을 조건부로 정의할 수 있습니다. 조건이 `true`로 확인되지 않으면 조건부 요소의 내용이 무시됩니다. 다음 예제에서는 `Configuration` 요소가 아직 정의되지 않은 경우 해당 요소를 정의합니다.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 프로젝트 파일 전체에서 $(\<PropertyName>) 구문을 사용하여 속성을 참조할 수 있습니다. 예를 들어 `$(BuildDir)` 및 `$(Configuration)`을 사용하여 이전 예제의 속성을 참조할 수 있습니다.

 속성에 대한 자세한 내용은 [MSBuild 속성](../msbuild/msbuild-properties.md)을 참조하세요.

### <a name="BKMK_Items"></a> 항목

 항목은 빌드 시스템에 대한 입력이며, 일반적으로 파일을 나타냅니다. 항목은 사용자 정의된 항목 이름에 따라 항목 형식으로 그룹화됩니다. 이러한 항목 형식은 작업의 매개 변수로 사용될 수 있으며, 이 작업은 개별 항목을 사용하여 빌드 프로세스의 단계를 수행합니다.

 항목 형식의 이름을 포함하는 요소를 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 요소의 자식으로 만들어 프로젝트 파일에서 항목을 선언합니다. 예를 들어, 다음 코드는 두 개의 파일을 포함하는 `Compile`이라는 항목 형식을 만듭니다.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 프로젝트 파일 전체에서 @(\<ItemType>) 구문을 사용하여 항목 형식을 참조할 수 있습니다. 예를 들어, 예제의 항목 형식은 `@(Compile)`을 사용하여 참조됩니다.

 MSBuild에서 요소 및 특성 이름은 대/소문자를 구분합니다. 그러나 속성, 항목 및 메타데이터 이름은 대/소문자를 구분하지 않습니다. 다음 예제에서는 항목 형식 `Compile`, `comPile` 또는 기타 대/소문자 변형을 만든 후 항목 형식에 값 "one.cs;two.cs"를 지정합니다.

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <comPile Include="two.cs" />
</ItemGroup>
```

 항목은 와일드카드 문자를 사용하여 선언될 수 있으며 고급 빌드 시나리오에 대한 추가 메타데이터를 포함할 수 있습니다. 항목에 대한 자세한 내용은 [항목](../msbuild/msbuild-items.md)을 참조하세요.

### <a name="BKMK_Tasks"></a> 작업

 작업은 MSBuild 프로젝트에서 빌드 작업을 수행하는 데 사용하는 실행 코드 단위입니다. 예를 들어, 작업은 입력 파일을 컴파일하거나 외부 도구를 실행할 수 있습니다. 작업은 다시 사용할 수 있으며 다른 개발자가 다른 프로젝트에서 작업을 공유할 수 있습니다.

 작업의 실행 논리는 관리 코드로 작성되며 [UsingTask](../msbuild/usingtask-element-msbuild.md) 요소를 사용하여 MSBuild에 매핑됩니다. <xref:Microsoft.Build.Framework.ITask> 인터페이스를 구현하는 관리되는 형식을 만들어 자체의 작업을 작성할 수 있습니다. 작업을 작성하는 방법에 대한 자세한 내용은 [작업 작성](../msbuild/task-writing.md)을 참조하세요.

 MSBuild에는 요구 사항에 맞게 수정할 수 있는 일반 작업이 포함되어 있습니다. 예를 들어 파일을 복사하는 [Copy](../msbuild/copy-task.md), 디렉터리를 만드는 [MakeDir](../msbuild/makedir-task.md), Visual C# 소스 코드 파일을 컴파일하는 [Csc](../msbuild/csc-task.md) 등이 있습니다. 사용할 수 있는 작업 및 사용법 정보에 대한 전체 목록은 [작업 참조](../msbuild/msbuild-task-reference.md)를 참조하세요.

 작업 이름을 포함하는 요소를 [Target](../msbuild/target-element-msbuild.md) 요소의 자식으로 만들어 MSBuild 프로젝트 파일에서 작업을 실행합니다. 작업은 일반적으로 요소 특성으로 전달되는 매개 변수를 받아들입니다. MSBuild 속성과 항목은 모두 매개 변수로 사용할 수 있습니다. 예를 들어 다음 코드에서는 [MakeDir](../msbuild/makedir-task.md) 작업을 호출하고 앞의 예제에서 선언한 `BuildDir` 속성값을 해당 작업으로 전달합니다.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 작업에 대한 자세한 내용은 [작업](../msbuild/msbuild-tasks.md)을 참조하세요.

### <a name="BKMK_Targets"></a> 대상

 대상은 작업을 특정 순서로 그룹화하고 프로젝트 파일의 섹션을 빌드 프로세스의 진입점으로 노출합니다. 대상은 확장할 수 있고 좀더 쉽게 이해할 수 있도록 종종 논리적 섹션으로 그룹화됩니다. 빌드 단계를 대상으로 나누면 해당 코드 섹션을 각 대상으로 복사하지 않아도 다른 대상에서 빌드 프로세스의 한 부분을 호출할 수 있습니다. 예를 들어 빌드 프로세스에 대한 몇 개의 진입점에 빌드할 참조가 필요한 경우, 참조를 빌드하는 대상을 만든 다음 필요한 모든 진입점에서 이 대상을 실행할 수 있습니다.

 [Target](../msbuild/target-element-msbuild.md) 요소를 사용하여 프로젝트 파일에 대상을 선언합니다. 예를 들어 다음 코드에서는 `Compile`이라는 대상을 만듭니다. 이 대상은 앞의 예제에서 선언한 항목 목록을 포함하는 [Csc](../msbuild/csc-task.md) 작업을 호출합니다.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 고급 시나리오에서는 대상을 사용하여 서로의 관계를 설명하고 종속성 분석을 수행할 수 있습니다. 종속성 분석을 통해 대상이 최신 상태이면 빌드 프로세스의 전체 섹션을 건너뛸 수 있습니다. 대상에 대한 자세한 내용은 [대상](../msbuild/msbuild-targets.md)을 참조하세요.

## <a name="build-logs"></a>빌드 로그

 빌드 오류, 경고 및 메시지를 콘솔이나 다른 출력 디바이스에 기록할 수 있습니다. 자세한 내용은 [빌드 로그 가져오기](../msbuild/obtaining-build-logs-with-msbuild.md) 및 [MSBuild 로그인](../msbuild/logging-in-msbuild.md)을 참조하세요.

## <a name="use-msbuild-in-visual-studio"></a>Visual Studio에서 MSBuild 사용

 Visual Studio는 MSBuild 프로젝트 파일 형식을 사용하여 관리되는 프로젝트의 빌드 정보를 저장합니다. Visual Studio 인터페이스를 사용하여 추가되거나 변경된 프로젝트 설정은 모든 프로젝트에 대해 생성되는 *.\*proj* 파일에 반영됩니다. Visual Studio에서는 관리되는 프로젝트를 로드 및 빌드하기 위해 호스팅된 MSBuild 인스턴스를 사용합니다. 즉, 관리되는 프로젝트는 Visual Studio 또는 명령 프롬프트(Visual Studio가 설치되지 않은 경우)에서 빌드할 수 있으며 그 결과는 동일합니다.

 Visual Studio에서 MSBuild를 사용하는 방법에 대한 자습서는 [연습: MSBuild 사용](../msbuild/walkthrough-using-msbuild.md)을 참조하세요.

## <a name="BKMK_Multitargeting"></a> 멀티 타기팅

 Visual Studio를 사용하면 .NET Framework의 여러 버전 중 하나에서 실행되는 애플리케이션을 컴파일할 수 있습니다. 예를 들어 32비트 플랫폼의 .NET Framework 2.0에서 실행되도록 애플리케이션을 컴파일하고 동일한 애플리케이션을 64비트 플랫폼의 .NET Framework 4.5에서 실행되도록 컴파일할 수 있습니다. 둘 이상의 프레임워크에서 실행 가능하도록 컴파일하는 기능을 다중 대상 지정이라고 합니다.

 다중 대상 지정에는 다음과 같은 이점이 있습니다.

- .NET Framework의 이전 버전(예: 버전 2.0, 3.0 및 3.5)을 대상으로 하는 애플리케이션을 개발할 수 있습니다.

- .NET Framework 외에 Silverlight 등의 다른 프레임워크를 대상으로 지정할 수 있습니다.

- 대상 프레임워크의 미리 정의된 하위 집합인 *프레임워크 프로필*을 대상으로 지정할 수 있습니다.

- 현재 버전의 .NET Framework용 서비스 팩이 릴리스될 경우 해당 서비스 팩을 대상으로 지정할 수 있습니다.

- 다중 대상 지정은 대상 프레임워크 및 플랫폼에서 사용 가능한 기능만 애플리케이션에서 사용되도록 합니다.

자세한 내용은 [멀티 타기팅](../msbuild/msbuild-multitargeting-overview.md)을 참조하세요.

## <a name="see-also"></a>참조

| 제목 | 설명 |
| - | - |
| [연습: 처음부터 MSBuild 프로젝트 파일 만들기](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | 텍스트 편집기만을 사용해서 기본 프로젝트 파일을 증분 방식으로 만드는 방법을 보여 줍니다. |
| [연습: MSBuild 사용](../msbuild/walkthrough-using-msbuild.md) | MSBuild의 구성 요소를 소개하고 Visual Studio IDE를 닫지 않고 MSBuild 프로젝트를 작성, 조작 및 디버깅하는 방법을 보여 줍니다. |
| [MSBuild 개념](../msbuild/msbuild-concepts.md) | MSBuild의 네 가지 빌딩 블록인 속성, 항목, 대상 및 작업에 대해 설명합니다. |
| [항목](../msbuild/msbuild-items.md) | MSBuild 파일 형식의 일반 개념과 그러한 모든 개념이 서로 어떻게 연결되는지를 설명합니다. |
| [MSBuild 속성](../msbuild/msbuild-properties.md) | 속성 및 속성 컬렉션을 소개합니다. 속성은 빌드를 구성하는 데 사용될 수 있는 키/값 쌍입니다. |
| [대상](../msbuild/msbuild-targets.md) | 작업을 특정 순서로 그룹화하며 빌드 프로세스의 섹션이 명령줄에서 호출되도록 하는 방법에 대해 설명합니다. |
| [작업](../msbuild/msbuild-tasks.md) | MSBuild에서 사용할 수 있는 실행 코드 단위를 만들어 원자성 빌드 작업을 수행하는 방법을 보여 줍니다. |
| [조건](../msbuild/msbuild-conditions.md) | MSBuild 요소에서 `Condition` 특성을 사용하는 방법에 대해 설명합니다. |
| [고급 개념](../msbuild/msbuild-advanced-concepts.md) | 일괄 처리, 변환 수행, 다중 대상 지정 및 기타 고급 기술을 제공합니다. |
| [MSBuild의 로그인](../msbuild/logging-in-msbuild.md) | 빌드 이벤트, 메시지 및 오류를 기록하는 방법에 대해 설명합니다. |
| [추가 리소스](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | MSBuild에 대한 자세한 정보를 볼 수 있는 커뮤니티 및 지원 리소스를 나열합니다. |

## <a name="reference"></a>참고

- [MSBuild 참조](../msbuild/msbuild-reference.md)\
 참조 정보를 포함하는 항목에 대한 링크입니다.

- [용어집](msbuild-glossary.md)\
 일반적인 MSBuild 용어를 정의합니다.
