---
title: 텍스트 템플릿 사용 방법
description: 텍스트 템플릿을 사용하여 텍스트를 생성할 때 발생하는 일반적인 질문에 대한 답변에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0c65a7ba67c3972620b3d589188e233827a12ffd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387270"
---
# <a name="how-to--with-text-templates"></a>텍스트 템플릿 사용 방법
Visual Studio 텍스트 템플릿은 모든 종류의 텍스트를 생성하는 유용한 방법을 제공합니다. 텍스트 템플릿을 사용하여 런타임에 애플리케이션의 일부로 텍스트를 생성하고 디자인 타임에 프로젝트 코드 중 일부를 생성할 수 있습니다. 이 항목에서는 가장 자주 묻는 "어떻게 할까요?...?"를 요약합니다. 질문.

 이 항목에서 글머리 기호가 앞에 오는 여러 답변은 대체 제안입니다.

 텍스트 템플릿에 대한 일반적인 소개는 [코드 생성 및 T4 텍스트 템플릿을 참조하세요.](../modeling/code-generation-and-t4-text-templates.md)

## <a name="how-to-"></a>사용법 ...

### <a name="generate-part-of-my-application-code"></a>내 애플리케이션 코드의 일부 생성
 파일 또는 데이터베이스에 구성 또는 *모델이* 있습니다. 내 코드의 하나 이상의 부분이 해당 모델에 따라 달라집니다.

- 텍스트 템플릿에서 일부 코드 파일을 생성합니다. 자세한 내용은 [T4 텍스트 템플릿을 사용하여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md) 및 템플릿 [작성을 시작하는 가장 좋은 방법은 무엇인가요?를 참조하세요.](#starting)

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>런타임에 파일을 생성하여 템플릿에 데이터 전달
 런타임에 내 애플리케이션은 표준 텍스트와 데이터가 혼합된 보고서와 같은 텍스트 파일을 생성합니다. 수백 개의 문을 쓰지 않으려고 `write` 합니다.

- 런타임 텍스트 템플릿을 프로젝트에 추가합니다. 이 템플릿은 코드를 인스턴스화하고 텍스트를 생성하는 데 사용할 수 있는 클래스를 만듭니다. 생성자 매개 변수에서 데이터를 전달할 수 있습니다. 자세한 내용은 [T4 텍스트 템플릿을 사용하여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)을 참조하세요.

- 런타임에만 사용할 수 있는 템플릿에서 생성하려는 경우 표준 텍스트 템플릿을 사용할 수 있습니다. Visual Studio 확장을 작성하는 경우 텍스트 템플릿 서비스를 호출할 수 있습니다. 자세한 내용은 [VS 확장에서 텍스트 변환 호출을 참조하세요.](../modeling/invoking-text-transformation-in-a-vs-extension.md) 다른 컨텍스트에서는 텍스트 템플릿 엔진을 사용할 수 있습니다. 자세한 내용은 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>를 참조하세요.

     지시문을 사용하여 \<#@parameter#> 이러한 템플릿에 매개 변수를 전달합니다. 자세한 내용은 [T4 매개 변수 지시문 을 참조하세요.](../modeling/t4-parameter-directive.md)

### <a name="read-another-project-file-from-a-template"></a>템플릿에서 다른 프로젝트 파일 읽기
 템플릿과 동일한 Visual Studio 프로젝트에서 파일을 읽으려면 다음을 수행합니다.

- 먼저 `hostSpecific="true"`를 `<#@template#>` 지시문에 삽입합니다.

     코드에서 를 사용하여 `this.Host.ResolvePath(filename)` 파일의 전체 경로를 얻습니다.

### <a name="invoke-methods-from-a-template"></a>템플릿에서 메서드 호출

메서드가 이미 있는 경우(예: .NET 클래스에서)

- \<#@assembly#>지시문을 사용하여 어셈블리를 로드하고 를 사용하여 \<#@import#> 네임스페이스 컨텍스트를 설정합니다. 자세한 내용은 [T4 가져오기 지시문 을 참조하세요.](../modeling/t4-import-directive.md)

   동일한 어셈블리 및 가져오기 지시문 집합을 자주 사용하는 경우 지시문 프로세서를 작성하는 것이 좋습니다. 각 템플릿에서 어셈블리 및 모델 파일을 로드하고 네임스페이스 컨텍스트를 설정할 수 있는 지시문 프로세서를 호출할 수 있습니다. 자세한 내용은 [사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기를 참조하세요.](../modeling/creating-custom-t4-text-template-directive-processors.md)

메서드를 직접 작성하는 경우:

- 런타임 텍스트 템플릿을 작성하는 경우 런타임 텍스트 템플릿과 이름이 같은 partial 클래스 정의를 작성합니다. 이 클래스에 추가 메서드를 추가합니다.

- 메서드, 속성 및 전용 클래스를 선언할 수 있는 클래스 기능 제어 블록을 `<#+ ... #>` 작성합니다. 텍스트 템플릿이 컴파일되면 클래스로 변환됩니다. 표준 제어 `<#...#>` 블록과 텍스트는 단일 메서드로 변환되고 클래스 기능 블록은 별도의 멤버로 삽입됩니다. 자세한 내용은 텍스트 템플릿 컨트롤 블록 을 [참조하세요.](../modeling/text-template-control-blocks.md)

   클래스 기능으로 정의된 메서드에는 포함된 텍스트 블록도 포함될 수 있습니다.

   클래스 기능을 하나 이상의 템플릿 파일에 포함할 수 있는 별도의 파일에 배치하는 것이 `<#@include#>` 좋습니다.

- 별도의 어셈블리(클래스 라이브러리)에 메서드를 작성하고 템플릿에서 호출합니다. 지시문을 사용하여 `<#@assembly#>` 어셈블리를 로드하고 `<#@import#>` 네임스페이스 컨텍스트를 설정합니다. 디버깅하는 동안 어셈블리를 다시 빌드하려면 Visual Studio 중지했다가 다시 시작해야 할 수 있습니다. 자세한 내용은 [T4 텍스트 템플릿 지시문 을 참조하세요.](../modeling/t4-text-template-directives.md)

### <a name="generate-many-files-from-one-model-schema"></a>하나의 모델 스키마에서 많은 파일 생성
 XML 또는 데이터베이스 스키마가 동일한 모델에서 파일을 생성하는 경우가 많습니다.

- 지시문 프로세서를 작성하는 것이 좋습니다. 이렇게 하면 각 템플릿의 여러 어셈블리 문과 import 문을 단일 사용자 지정 지시문으로 바꿀 수 있습니다. 지시문 프로세서는 모델 파일을 로드하고 구문 분석할 수도 있습니다. 자세한 내용은 [사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기를 참조하세요.](../modeling/creating-custom-t4-text-template-directive-processors.md)

### <a name="generate-files-from-a-complex-model"></a>복잡한 모델에서 파일 생성

- 모델을 나타내는 DSL(도메인별 언어)을 만드는 것이 좋습니다. 이렇게 하면 모델의 요소 이름을 반영하는 형식과 속성을 사용하므로 템플릿을 훨씬 쉽게 작성할 수 있습니다. 파일을 구문 분석하거나 XML 노드를 탐색할 필요가 없습니다. 예를 들면 다음과 같습니다.

     `foreach (Book book in this.Library) { ... }`

     자세한 내용은 [Domain-Specific 언어를 시작](../modeling/getting-started-with-domain-specific-languages.md) 및 Domain-Specific [언어에서 코드 생성을 참조하세요.](../modeling/generating-code-from-a-domain-specific-language.md)

### <a name="get-data-from-visual-studio"></a>Visual Studio 데이터 얻기
 Visual Studio 제공된 서비스를 사용하려면 특성을 설정하고 `hostSpecific` `EnvDTE` 어셈블리를 로드합니다. 예를 들면 다음과 같습니다.

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

### <a name="execute-text-templates-in-the-build-process"></a>빌드 프로세스에서 텍스트 템플릿 실행

- 자세한 내용은 [빌드 프로세스의 코드 생성을 참조하세요.](../modeling/code-generation-in-a-build-process.md)

## <a name="more-general-questions"></a>보다 일반적인 질문

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> 텍스트 템플릿 작성을 시작하는 가장 좋은 방법은 무엇인가요?

1. 생성된 파일의 특정 예제를 작성합니다.

2. `<#@template #>`지시문과 입력 파일 또는 모델을 로드하는 데 필요한 지시문 및 코드를 삽입하여 텍스트 템플릿으로 변환합니다.

3. 파일의 일부를 식 및 코드 블록으로 점진적으로 대체합니다.

### <a name="what-is-a-model"></a>"모델"이란 무엇인가요?

- 템플릿에서 읽은 입력입니다. 파일 또는 데이터베이스에 있을 수 있습니다. XML, Visio 그리기, DSL(도메인별 언어) 또는 UML 모델일 수도 있고 일반 텍스트일 수도 있습니다. 여러 파일에 분산될 수 있습니다. 일반적으로 두 개 이상의 템플릿이 하나의 모델을 읽습니다.

     "모델"이라는 용어는 생성된 프로그램 코드 또는 다른 파일보다 비즈니스의 일부 측면을 더 직접적으로 나타낸다는 의미입니다. 예를 들어 생성된 소프트웨어가 감독하는 통신 네트워크의 계획을 나타낼 수 있습니다.

### <a name="what-is-the-benefit-of-using-text-templates"></a>텍스트 템플릿 사용의 이점은 무엇인가요?
 일반적으로 한 모델에서 여러 코드 또는 다른 파일을 생성합니다. 모델은 생성된 코드보다 요구 사항을 더 직접적으로 나타냅니다. 구현 세부 정보를 생략하고 코드가 아닌 요구 사항을 기준으로 작성됩니다. 일반적으로와 같이 요구 사항이 변경되면 프로그램 코드의 다른 부분보다 더 쉽고 안정적으로 모델을 업데이트할 수 있습니다.

 따라서 코드 생성은 민첩한 개발 방법의 관점에서 중요한 도구입니다.

### <a name="what-best-practices-are-there-for-text-templates"></a>텍스트 템플릿에 대한 "모범 사례"는 무엇인가요?

- 자세한 내용은 [T4 텍스트 템플릿 작성 지침을 참조하세요.](../modeling/guidelines-for-writing-t4-text-templates.md)

### <a name="what-is-t4"></a>"T4"란?

- 여기에 설명된 Visual Studio 텍스트 템플릿 기능의 또 다른 이름입니다. 게시되지 않은 이전 버전은 "텍스트 템플릿 변환"의 약어입니다.
