---
title: T4 텍스트 템플릿 작성에 대 한 지침 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 04dd3fc4-10e8-488a-bdea-4d615f50f063
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d1e15a8c00a0614d020defd2df7b06665289a8b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666057"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>T4 텍스트 템플릿 작성 지침
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이러한 일반적인 지침은에서 프로그램 코드나 기타 응용 프로그램 리소스를 생성 하는 경우에 유용할 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . 고정 규칙은 아닙니다.

## <a name="guidelines-for-design-time-t4-templates"></a>디자인 타임 T4 템플릿에 대 한 지침
 디자인 타임 T4 템플릿은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 디자인 타임에 프로젝트에서 코드를 생성 하는 템플릿입니다. 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)을 참조 하세요.

 응용 프로그램의 다양 한 측면을 생성 합니다.
코드 생성은 프로젝트 중에 변경 되거나 응용 프로그램의 다른 버전 간에 변경 될 수 있는 응용 프로그램의 해당 측면에 가장 유용 합니다. 생성 해야 하는 항목을 보다 쉽게 확인할 수 있도록 이러한 변수 측면을 보다 고정 측면에서 분리 합니다. 예를 들어 응용 프로그램에서 웹 사이트를 제공 하는 경우 탐색 경로를 정의 하는 논리에서 함수를 제공 하는 표준 페이지를 한 페이지에서 다른 페이지로 분리 합니다.

 하나 이상의 원본 모델에서 변수 측면을 인코딩합니다.
모델은 생성 되는 코드의 변수 부분에 대 한 특정 값을 가져오기 위해 각 템플릿에서 읽는 파일 또는 데이터베이스입니다. 모델은 데이터베이스, 사용자 고유 디자인, 다이어그램 또는 도메인별 언어의 XML 파일 일 수 있습니다. 일반적으로 한 모델은 프로젝트에서 많은 파일을 생성 하는 데 사용 됩니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . 각 파일은 별도의 템플릿에서 생성 됩니다.

 하나 이상의 모델을 프로젝트에 사용할 수 있습니다. 예를 들어 웹 페이지 간 탐색을 위한 모델과 페이지 레이아웃에 대 한 별도의 모델을 정의할 수 있습니다.

 사용자의 요구 사항 및 어휘를 구현 하지 않고 모델에 집중 합니다.
예를 들어 웹 사이트 응용 프로그램에서 모델이 웹 페이지 및 하이퍼링크를 참조 하 게 될 것입니다.

 모델에서 나타내는 정보의 종류에 맞는 프레젠테이션 형태를 선택 하는 것이 가장 좋습니다. 예를 들어 웹 사이트를 통한 탐색 경로 모델은 상자와 화살표의 다이어그램인 것일 수 있습니다.

 생성 된 코드를 테스트 합니다.
수동 또는 자동 테스트를 사용 하 여 사용자가 요구 하는 결과 코드가 작동 하는지 확인 합니다. 코드가 생성 되는 동일한 모델에서 테스트를 생성 하지 않습니다.

 일부 경우에는 모델에서 직접 일반 테스트를 수행할 수 있습니다. 예를 들어, 웹 사이트의 모든 페이지를 탐색 하 여 해당 웹 사이트의 모든 페이지에 연결할 수 있는지 확인 하는 테스트를 작성할 수 있습니다.

 사용자 지정 코드 허용: partial 클래스를 생성 합니다.
생성 된 코드와 함께 직접 작성 하는 코드를 허용 합니다. 일반적으로 코드 생성 체계에서 발생할 수 있는 모든 변형에 대해 처리할 수 있는 것은 아닙니다. 따라서 생성 된 코드의 일부를 추가 하거나 재정의 해야 합니다. 생성 된 자료가 또는와 같은 .NET 언어에 있는 경우 [!INCLUDE[csprcs](../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 두 가지 전략이 특히 유용 합니다.

- 생성 된 클래스는 부분 이어야 합니다. 이렇게 하면 생성 된 코드에 내용을 추가할 수 있습니다.

- 클래스는 다른 클래스에서 상속 하는 쌍으로 생성 되어야 합니다. 기본 클래스는 생성 된 모든 메서드와 속성을 포함 해야 하며, 파생 클래스는 생성자만 포함 해야 합니다. 이를 통해 직접 작성 된 코드는 생성 된 메서드를 재정의할 수 있습니다.

  XML과 같은 다른 생성 된 언어에서 지시문을 사용 `<#@include#>` 하 여 손으로 작성 되 고 생성 된 콘텐츠의 간단한 조합을 만듭니다. 더 복잡 한 경우에는 생성 된 파일을 직접 작성 한 파일과 결합 하는 후 처리 단계를 작성 해야 할 수 있습니다.

  공통 자료를 포함 파일 또는 런타임 템플릿으로 이동 하 여 여러 템플릿에서 유사한 텍스트와 코드 블록을 반복 하지 않도록 하려면 지시문을 사용 `<#@ include #>` 합니다. 자세한 내용은 [T4 Include 지시문](../modeling/t4-include-directive.md)을 참조 하세요.

  별도의 프로젝트에서 런타임 텍스트 템플릿을 작성 한 다음 디자인 타임 템플릿에서 호출할 수도 있습니다. 이렇게 하려면 지시문을 사용 `<#@ assembly #>` 하 여 별도의 프로젝트에 액세스 합니다.

  코드의 많은 블록을 별도 어셈블리로 이동 하는 것이 좋습니다.
  코드 블록 및 클래스 기능 블록이 클 경우이 코드 중 일부를 별도 프로젝트에서 컴파일하는 메서드로 이동 하는 것이 유용할 수 있습니다. 지시문을 사용 `<#@ assembly #>` 하 여 템플릿의 코드에 액세스할 수 있습니다. 자세한 내용은 [T4 Assembly 지시문](../modeling/t4-assembly-directive.md)을 참조 하세요.

  템플릿이 상속할 수 있는 추상 클래스에 메서드를 넣을 수 있습니다. 추상 클래스는에서 상속 해야 합니다 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> . 자세한 내용은 [T4 템플릿 지시문](../modeling/t4-template-directive.md)을 참조 하세요.

  구성 파일이 아닌 코드를 생성 합니다. 변수 응용 프로그램을 작성 하는 한 가지 방법은 구성 파일을 허용 하는 일반 프로그램 코드를 작성 하는 것입니다. 이러한 방식으로 작성 된 응용 프로그램은 매우 유연 하며, 응용 프로그램을 다시 빌드하지 않고도 비즈니스 요구 사항이 변경 되 면 다시 구성할 수 있습니다. 그러나이 방법의 단점은 응용 프로그램이 보다 구체적인 응용 프로그램 보다 더 잘 수행 되지 않는 것입니다. 또한 대부분의 제네릭 형식을 처리 하기 때문에 일부 프로그램 코드는 읽기 및 유지 관리가 더 어려워집니다.

  이와 대조적으로 컴파일 전에 변수 부분을 생성 하는 응용 프로그램은 강력한 형식의 응용 프로그램입니다. 이를 통해 직접 작성 한 코드를 작성 하 고 소프트웨어의 생성 된 부분과 통합 하는 것이 훨씬 더 쉽고 안정적입니다.

  코드 생성의 모든 이점을 얻으려면 구성 파일 대신 프로그램 코드를 생성 해 보세요.

  생성 된 코드 폴더를 사용 하 여 템플릿과 생성 된 파일을 **생성 된 코드**라는 프로젝트 폴더에 저장 하 여 직접 편집 해야 하는 파일이 아니라는 것을 명확 하 게 합니다. 재정의 하거나 생성 된 클래스에 추가할 사용자 지정 코드를 만드는 경우 이러한 클래스를 **사용자 지정 코드**라는 폴더에 저장 합니다. 일반적인 프로젝트의 구조는 다음과 같습니다.

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs

```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>실행 시간 (전처리) T4 템플릿에 대 한 지침
 공용 자료를 상속 된 템플릿으로 이동-상속을 사용 하 여 T4 텍스트 템플릿 간에 메서드 및 텍스트 블록을 공유할 수 있습니다. 자세한 내용은 [T4 템플릿 지시문](../modeling/t4-template-directive.md)을 참조 하세요.

 런타임 템플릿이 있는 포함 파일을 사용할 수도 있습니다.

 코드의 많은 본문을 partial 클래스로 이동 합니다.
각 런타임 템플릿은 템플릿과 이름이 같은 partial 클래스 정의를 생성 합니다. 동일한 클래스의 다른 부분 정의가 포함 된 코드 파일을 작성할 수 있습니다. 이러한 방식으로 클래스에 메서드, 필드 및 생성자를 추가할 수 있습니다. 이러한 멤버는 템플릿의 코드 블록에서 호출할 수 있습니다.

 IntelliSense를 사용할 수 있기 때문에 코드를 더 쉽게 작성할 수 있다는 이점이 있습니다. 또한 프레젠테이션과 기본 논리를 더 잘 구분할 수 있습니다.

 예를 들어 **MyReportText.tt**에서 다음을 수행 합니다.

 `The total is: <#= ComputeTotal() #>`

 **MyReportText-Methods.cs**:

 `private string ComputeTotal() { ... }`

 사용자 지정 코드 허용: 확장 점수 제공에서 가상 메서드 생성을 고려 \<#+ class feature blocks #> 합니다. 이렇게 하면 단일 템플릿을 수정 하지 않고 많은 컨텍스트에서 사용할 수 있습니다. 템플릿을 수정 하는 대신 최소 추가 논리를 제공 하는 파생 클래스를 생성할 수 있습니다. 파생 클래스는 일반 코드 이거나 런타임 템플릿이 될 수 있습니다.

 예를 들어 MyStandardRunTimeTemplate.tt에서 다음을 수행 합니다.

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

 응용 프로그램 코드에서 다음을 수행 합니다.

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();

```

## <a name="guidelines-for-all-t4-templates"></a>모든 T4 템플릿에 대 한 지침
 텍스트를 분리 하 여 데이터를 수집 합니다. 계산 및 텍스트 블록을 혼합 해 서 사용 하지 마십시오. 각 텍스트 템플릿에서 첫 번째를 사용 \<# code block #> 하 여 변수를 설정 하 고 복잡 한 계산을 수행 합니다. 첫 번째 텍스트 블록에서 템플릿 끝까지 또는 첫 번째 텍스트 블록부터 \<#+ class feature block #> 긴 식을 사용 하지 말고 텍스트 블록이 포함 되지 않은 경우 루프와 조건을 방지 합니다. 이 방법을 사용 하면 템플릿을 더 쉽게 읽고 유지 관리할 수 있습니다.

 포함 파일에를 사용 하지 마세요 `.tt` . 포함 파일의 경우와 같이 다른 파일 이름 확장명을 사용 `.ttinclude` 합니다. `.tt`런타임 또는 디자인 타임 텍스트 템플릿으로 처리 하려는 파일에만를 사용 합니다. 경우에 따라에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 파일을 인식 `.tt` 하 고 해당 속성을 자동으로 설정 하 여 처리 합니다.

 각 템플릿을 고정 프로토타입으로 시작 합니다.
생성 하려는 코드 또는 텍스트의 예제를 작성 하 고 올바른지 확인 합니다. 그런 다음 확장을 .tt로 변경 하 고 모델을 읽어 내용을 수정 하는 코드를 증분 삽입 합니다.

 형식화 된 모델을 사용 하는 것이 좋습니다.
모델에 대해 XML 또는 데이터베이스 스키마를 만들 수 있지만 DSL (도메인 특정 언어)을 만드는 것이 유용할 수 있습니다. DSL은 스키마의 각 노드를 나타내는 클래스와 특성을 나타내는 속성을 생성 한다는 이점이 있습니다. 즉, 비즈니스 모델을 기준으로 프로그래밍할 수 있습니다. 예를 들면 다음과 같습니다.

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 모델에 다이어그램을 사용 하는 것이 좋습니다.
대부분의 모델은 특히 매우 큰 경우 텍스트 테이블로 가장 효과적으로 표시 되 고 관리 됩니다.

 그러나 일부 종류의 비즈니스 요구 사항에 대해서는 복잡 한 관계 및 워크플로 집합을 명확 하 게 파악 하는 것이 중요 하며 다이어그램은 가장 적합 한 매체입니다. 다이어그램의 장점은 사용자 및 기타 관련자와 논의 하기가 쉽기 때문입니다. 비즈니스 요구 사항의 수준에서 모델의 코드를 생성 하면 요구 사항이 변경 될 때 코드를 보다 유연 하 게 만들 수 있습니다.

 UML 클래스 및 동작 다이어그램은 이러한 용도로 적용 되는 경우가 많습니다. 사용자 고유의 다이어그램 유형을 DSL (도메인별 언어)로 디자인할 수도 있습니다. UML 및 Dsl 모두에서 코드를 생성할 수 있습니다. 자세한 내용은 [아키텍처 분석 및 모델링](../modeling/analyze-and-model-your-architecture.md) 및 [아키텍처 분석 및 모델링](../modeling/analyze-and-model-your-architecture.md)을 참조 하세요.

## <a name="see-also"></a>관련 항목
 T4 텍스트 [템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md) [t4 텍스트 템플릿을 사용 하 여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)
