---
title: 파일에 대한 빌드 작업
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35136ac0b7b0104f1812df7a9bf8ba81f6907374
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408809"
---
# <a name="build-actions"></a>빌드 작업

Visual Studio 프로젝트의 모든 파일에는 빌드 작업이 있습니다. 빌드 작업은 프로젝트가 컴파일될 때 파일에 발생하는 작업을 제어합니다.

> [!NOTE]
> 이 토픽은 Windows용 Visual Studio에만 적용됩니다. Mac용 Visual Studio의 경우 [Mac용 Visual Studio에서 빌드 작업](/visualstudio/mac/build-actions)을 참조하세요.

## <a name="set-a-build-action"></a>빌드 작업 설정

파일에 대한 빌드 작업을 설정하려면 **솔루션 탐색기**에서 파일을 선택하고 **Alt**+**Enter**를 눌러 **속성** 창에서 파일의 속성을 엽니다. 또는 **솔루션 탐색기**에서 파일을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. **속성** 창의 **고급** 섹션 아래에 있는 **빌드 작업** 옆의 드롭다운 목록을 사용하여 파일에 대한 빌드 작업을 설정합니다.

![Visual Studio에서 파일에 대한 작업 빌드](media/build-actions.png)

## <a name="build-action-values"></a>빌드 작업 값

C# 및 Visual Basic 프로젝트 파일에 대한 좀 더 일반적인 빌드 작업 중 일부는 다음과 같습니다.

|빌드 작업 | 프로젝트 형식 | 설명 |
|-|-|
| **AdditionalFiles** | C#, Visual Basic | 입력으로 C# 또는 Visual Basic 컴파일러에 전달되는 비소스 텍스트 파일입니다. 이 빌드 작업은 주로 코드 품질을 확인하기 위해 프로젝트에서 참조되는 [분석기](../code-quality/roslyn-analyzers-overview.md)에 입력을 제공하는 데 사용됩니다. 자세한 내용은 [추가 파일 사용](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md)을 참조하세요.|
| **ApplicationDefinition** | WPF | 애플리케이션을 정의하는 파일입니다. 프로젝트를 처음 만들 때 *App.xaml*입니다. |
| **CodeAnalysisDictionary** | .NET | 코드 분석에서 맞춤법 검사에 사용하는 사용자 지정 단어 사전입니다. [방법: 코드 분석 사전 사용자 지정](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **컴파일** | any | 파일이 컴파일러에 소스 파일로 전달됩니다.|
| **콘텐츠** | .NET | **콘텐츠**로 표시된 파일은 <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>을 호출하여 스트림으로 검색할 수 있습니다. ASP.NET 프로젝트의 경우 이러한 파일은 배포 시 사이트의 일부로 포함됩니다.|
| **DesignData** | WPF | XAML ViewModel 파일에 사용되며, 디자인 타임에 사용자 컨트롤을 더미 형식 및 샘플 데이터를 사용하여 볼 수 있도록 합니다. |
| **DesignDataWithDesignTimeCreateable** | WPF | **DesignData**와 유사하지만 실제 형식을 사용합니다.  |
| **포함 리소스** | .NET | 파일이 어셈블리에 포함될 리소스로 컴파일러에 전달됩니다. <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName>을 호출하여 어셈블리에서 파일을 읽을 수 있습니다.|
| **EntityDeploy** | .NET | EF(Entity Framework)의 경우 EF 아티팩트의 배포를 지정하는 .edmx 파일입니다. |
| **Fakes** | .NET | Microsoft Fakes 테스트 프레임워크에 사용됩니다. [Microsoft Fakes를 사용하여 테스트 대상 코드 격리](../test/isolating-code-under-test-with-microsoft-fakes.md)를 참조하세요. |
| **없음** | any | 파일은 어떤 방식으로든 빌드에 일부가 아닙니다. 이 값은 예를 들어 "ReadMe" 파일과 같은 문서 파일에 사용할 수 있습니다.|
| **페이지** | WPF | 런타임에 로드 속도를 높이려면 XAML 파일을 이진 .baml 파일로 컴파일합니다. |
| **리소스** | WPF | 해당 파일을 확장명이 *.g.resources*인 어셈블리 매니페스트 리소스 파일에 포함하도록 지정합니다. |
| **그림자** | .NET | 빌드된 어셈블리 파일 이름 목록을 줄마다 하나씩 포함하는 .accessor 파일에 사용됩니다. 목록의 각 어셈블리에 대해 원본과 유사하지만 전용 메서드 대신 공용 메서드를 포함하는 `ClassName_Accessor` 이름의 공용 클래스를 생성합니다. 단위 테스트에 사용됩니다. |
| **시작 화면** | WPF | 런타임에 앱을 시작할 때 표시되는 이미지 파일을 지정합니다. |
| **XamlAppDef** | Windows Workflow Foundation | 포함된 워크플로를 사용하여 워크플로 XAML 파일을 어셈블리로 빌드하도록 지시합니다. |

> [!NOTE]
> 추가 빌드 작업은 특정 프로젝트 형식에 대해 정의할 수 있으므로 빌드 작업 목록은 프로젝트 형식에 따라 다르며, 이 목록에 없는 값이 표시될 수 있습니다.

## <a name="see-also"></a>참조

- [C# 컴파일러 옵션](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Visual Basic 컴파일러 옵션](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [빌드 작업(Mac용 Visual Studio)](/visualstudio/mac/build-actions)
