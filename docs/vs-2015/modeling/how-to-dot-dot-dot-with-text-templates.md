---
title: 어떻게... 텍스트 템플릿 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c55c7a277d3f38b36367008ae6393f58c9c9a2c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671621"
---
# <a name="how-to--with-text-templates"></a>텍스트 템플릿 사용 방법
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

의 텍스트 템플릿은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 모든 종류의 텍스트를 생성 하는 유용한 방법을 제공 합니다. 텍스트 템플릿을 사용 하 여 런타임에 응용 프로그램의 일부로 텍스트를 생성 하 고 디자인 타임에 프로젝트 코드를 생성할 수 있습니다. 이 항목에서는 가장 자주 묻는 "어떻게 할까요? ...?"를 요약 합니다. 질문.

 이 항목에서는 글머리 기호가 앞에 오는 여러 답변이 대체 제안입니다.

 텍스트 템플릿에 대 한 일반적인 소개는 [코드 생성 및 T4 텍스트 템플릿](../modeling/code-generation-and-t4-text-templates.md)을 참조 하세요.

## <a name="how-to-"></a>방법...

### <a name="generate-part-of-my-application-code"></a>내 응용 프로그램 코드의 일부를 생성 합니다.
 파일이 나 데이터베이스에 구성 또는 *모델이* 있습니다. 내 코드의 한 부분이 해당 모델에 따라 달라 집니다.

- 텍스트 템플릿에서 일부 코드 파일을 생성 합니다. 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md) 및 [템플릿 작성을 시작 하는 가장 좋은 방법은 무엇 인가요?](#starting)를 참조 하세요.

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>런타임에 파일을 생성 하 여 데이터를 템플릿에 전달 합니다.
 런타임에 응용 프로그램은 표준 텍스트와 데이터가 혼합 되어 있는 보고서와 같은 텍스트 파일을 생성 합니다. 수백 개의 문을 작성 하지 않으려고 `write` 합니다.

- 프로젝트에 런타임 텍스트 템플릿을 추가 합니다. 이 템플릿은 코드에서 클래스를 만들어 텍스트를 생성 하는 데 인스턴스화하고 사용할 수 있습니다. 생성자 매개 변수에서 데이터를 전달할 수 있습니다. 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)을 참조 하세요.

- 런타임에만 사용할 수 있는 템플릿에서 생성 하려는 경우 표준 텍스트 템플릿을 사용할 수 있습니다. 확장을 작성 하는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 텍스트 템플릿 서비스를 호출할 수 있습니다. 자세한 내용은 [VS 확장에서 텍스트 변환 호출](../modeling/invoking-text-transformation-in-a-vs-extension.md)을 참조 하세요. 다른 컨텍스트에서는 텍스트 템플릿 엔진을 사용할 수 있습니다. 자세한 내용은 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>를 참조하세요.

     지시문을 사용 \<#@parameter#> 하 여 매개 변수를 이러한 템플릿에 전달 합니다. 자세한 내용은 [T4 매개 변수 지시문](../modeling/t4-parameter-directive.md)을 참조 하세요.

### <a name="read-another-project-file-from-a-template"></a>템플릿에서 다른 프로젝트 파일 읽기
 템플릿과 동일한 프로젝트에서 파일을 읽으려면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 다음을 수행 합니다.

- 먼저 `hostSpecific="true"`를 `<#@template#>` 지시문에 삽입합니다.

     코드에서를 사용 `this.Host.ResolvePath(filename)` 하 여 파일의 전체 경로를 가져옵니다.

### <a name="invoke-methods-from-a-template"></a>템플릿에서 메서드 호출
 메서드가 이미 있는 경우 (예 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] : 표준 클래스:

- 지시문을 사용 하 여 \<#@assembly#> 어셈블리를 로드 하 고 \<#@import#> 를 사용 하 여 네임 스페이스 컨텍스트를 설정 합니다. 자세한 내용은 [T4 Import 지시어](../modeling/t4-import-directive.md)를 참조 하세요.

   동일한 어셈블리 집합과 가져오기 지시문을 자주 사용 하는 경우 지시문 프로세서를 작성 하는 것이 좋습니다. 각 템플릿에서 지시문 프로세서를 호출 하 여 어셈블리와 모델 파일을 로드 하 고 네임 스페이스 컨텍스트를 설정할 수 있습니다. 자세한 내용은 [사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기](../modeling/creating-custom-t4-text-template-directive-processors.md)를 참조 하세요.

  메서드를 직접 작성 하는 경우:

- 런타임 텍스트 템플릿을 작성 하는 경우 런타임 텍스트 템플릿과 이름이 같은 partial 클래스 정의를 작성 합니다. 이 클래스에 추가 메서드를 추가 합니다.

- `<#+ ... #>`메서드, 속성 및 개인 클래스를 선언할 수 있는 클래스 기능 제어 블록을 작성 합니다. 텍스트 템플릿이 컴파일되면 클래스로 변환 됩니다. 표준 제어 블록과 `<#...#>` 텍스트는 단일 메서드로 변환 되 고 클래스 기능 블록은 별도의 멤버로 삽입 됩니다. 자세한 내용은 [텍스트 템플릿 제어 블록](../modeling/text-template-control-blocks.md)을 참조 하세요.

   클래스 기능으로 정의 된 메서드는 포함 된 텍스트 블록을 포함할 수도 있습니다.

   하나 이상의 템플릿 파일에 사용할 수 있는 별도의 파일에 클래스 기능을 배치 하는 것이 좋습니다 `<#@include#>` .

- 별도의 어셈블리 (클래스 라이브러리)에 메서드를 작성 하 고 템플릿에서 호출 합니다. 지시문을 사용 `<#@assembly#>` 하 여 어셈블리를 로드 하 고 `<#@import#>` 네임 스페이스 컨텍스트를 설정 합니다. 디버그 하는 동안 어셈블리를 다시 작성 하려면를 중지 한 후 다시 시작 해야 할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . 자세한 내용은 [T4 텍스트 템플릿 지시문](../modeling/t4-text-template-directives.md)을 참조 하세요.

### <a name="generate-many-files-from-one-model-schema"></a>한 모델 스키마에서 많은 파일 생성
 XML 또는 데이터베이스 스키마가 동일한 모델에서 파일을 생성 하는 경우가 종종 있습니다.

- 지시문 프로세서를 작성 하는 것이 좋습니다. 이렇게 하면 단일 사용자 지정 지시문을 사용 하 여 각 템플릿의 여러 어셈블리 문과 import 문을 바꿀 수 있습니다. 또한 지시문 프로세서는 모델 파일을 로드 하 고 구문 분석할 수 있습니다. 자세한 내용은 [사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기](../modeling/creating-custom-t4-text-template-directive-processors.md)를 참조 하세요.

### <a name="generate-files-from-a-complex-model"></a>복합 모델에서 파일 생성

- 모델을 나타내는 DSL (도메인별 언어)을 만드는 것이 좋습니다. 이렇게 하면 모델의 요소 이름을 반영 하는 형식과 속성을 사용 하기 때문에 템플릿을 더 쉽게 작성할 수 있습니다. 파일을 구문 분석 하거나 XML 노드를 탐색할 필요는 없습니다. 예:

     `foreach (Book book in this.Library) { ... }`

     자세한 내용은 도메인별 언어 [시작](../modeling/getting-started-with-domain-specific-languages.md) 및 [도메인별 언어에서 코드 생성](../modeling/generating-code-from-a-domain-specific-language.md)을 참조 하세요.

- UML 모델에서 코드를 생성 하는 것이 좋습니다. 코드는 UML을 직접 반영 하지 않아도 됩니다. 예를 들어 UML 모델의 각 클래스에 대해 클래스를 생성할 필요가 없습니다. 대신 UML 클래스 다이어그램을 사용 하 여 웹 사이트를 표시 하 고 각 UML 클래스에서 웹 페이지를 생성할 수 있습니다. 요구 사항에 가장 가까운 다이어그램 유형을 선택 합니다. 예를 들어 작업 다이어그램을 선택 하 여 모든 유형의 워크플로를 나타냅니다. 스테레오 타입을 정의 하 여 각 요소 형식에 응용 프로그램에 적절 한 정보를 추가할 수 있습니다.

     UML 모델에서 생성 하면 DSL을 사용 하는 것 처럼 모델을 다이어그램 폼으로 그리거나 편집할 수 있습니다.

     자세한 내용은 [앱에 대 한 모델 만들기](../modeling/create-models-for-your-app.md) 및 [UML 모델에서 파일 생성](../modeling/generate-files-from-a-uml-model.md)을 참조 하세요.

### <a name="get-data-from-vsprvs"></a>데이터 가져오기 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]
 에서 제공 하는 서비스를 사용 하려면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 특성을 설정 하 `hostSpecific` 고 `EnvDTE` 어셈블리를 로드 합니다. 예:

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

- 자세한 내용은 [빌드 프로세스에서 코드 생성](../modeling/code-generation-in-a-build-process.md)을 참조 하세요.

## <a name="more-general-questions"></a>더 일반적인 질문

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> 텍스트 템플릿 작성을 시작 하는 가장 좋은 방법은 무엇입니까?

1. 생성 된 파일의 특정 예제를 작성 합니다.

2. `<#@template #>`지시문을 삽입 하 고 입력 파일이 나 모델을 로드 하는 데 필요한 지시문과 코드를 삽입 하 여 텍스트 템플릿으로 변환 합니다.

3. 파일의 일부를 식 및 코드 블록으로 점차적으로 바꿉니다.

### <a name="what-is-a-model"></a>"모델"이란 무엇인가요?

- 템플릿에서 읽은 입력입니다. 파일이 나 데이터베이스에 있을 수 있습니다. XML, Visio drawing 또는 DSL (도메인별 언어) 또는 UML 모델 일 수도 있고 일반 텍스트일 수도 있습니다. 여러 파일에 걸쳐 분산 될 수 있습니다. 일반적으로 두 개 이상의 템플릿이 하나의 모델을 읽습니다.

     "모델" 이라는 용어는 생성 된 프로그램 코드 또는 다른 파일 보다 비즈니스의 일부 측면을 나타내는 의미입니다. 예를 들어 생성 된 소프트웨어가 감독 하는 통신 네트워크 계획을 나타낼 수 있습니다.

### <a name="what-is-the-benefit-of-using-text-templates"></a>텍스트 템플릿을 사용 하는 경우의 혜택은 무엇 인가요?
 일반적으로 모델 하나에서 여러 코드 또는 다른 파일을 생성 합니다. 모델은 생성 된 코드 보다 더 직접적으로 요구 사항을 나타냅니다. 구현 세부 정보를 생략 하 고 코드가 아닌 요구 사항 측면에서 작성 됩니다. 일반적으로 요구 사항이 변경 되 면 프로그램 코드의 여러 부분 보다 쉽고 안정적으로 모델을 업데이트할 수 있습니다.

 따라서 코드 생성은 agile 개발 방법의 관점에서 중요 한 도구입니다.

### <a name="what-best-practices-are-there-for-text-templates"></a>텍스트 템플릿에 대 한 "모범 사례"는 무엇 인가요?

- 자세한 내용은 [T4 텍스트 템플릿 작성에 대 한 지침](../modeling/guidelines-for-writing-t4-text-templates.md)을 참조 하세요.

### <a name="what-is-t4"></a>"T4" 란?

- 여기에 설명 된 텍스트 템플릿 기능에 대 한 다른 이름 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 입니다. 게시 되지 않은 이전 버전은 "텍스트 템플릿 변환"의 약어 였습니다.
