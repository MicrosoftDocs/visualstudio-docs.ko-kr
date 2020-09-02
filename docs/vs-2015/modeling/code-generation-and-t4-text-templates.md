---
title: 코드 생성 및 T4 텍스트 템플릿 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: 84
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f34422dfd47efdce9bf837f923da0e139a13398
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667914"
---
# <a name="code-generation-and-t4-text-templates"></a>코드 생성 및 T4 텍스트 템플릿
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 *T4 텍스트 템플릿* 은 텍스트 파일을 생성할 수 있는 제어 논리 및 텍스트 블록이 혼합된 것입니다. 제어 논리는 [!INCLUDE[csprcs](../includes/csprcs-md.md)] 또는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]에서 프로그램 코드 조각으로 작성되었습니다. Visual Studio 2015 업데이트 2 이상에서는 T4 템플릿 지시문에 C# 버전 6.0 기능을 사용할 수 있습니다. 생성된 파일은 웹 페이지, 리소스 파일 또는 임의 언어로 작성된 프로그램 소스 코드와 같은 임의 종류의 텍스트일 수 있습니다.

 T4 텍스트 템플릿에는 다음 두 가지 종류가 있습니다.

 **런타임 T4 텍스트 템플릿** ('전처리된' 템플릿)은 애플리케이션에서 실행되어 일반적으로 해당 출력의 일부로 텍스트 문자열을 생성합니다.
예를 들어 HTML 페이지를 정의하는 템플릿을 만들 수 있습니다.

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

 템플릿은 생성된 출력과 유사합니다. 결과 출력과 템플릿이 유사하기 때문에 템플릿을 변경하려는 경우 실수를 방지할 수 있습니다.

 또한 템플릿에는 프로그램 코드 조각이 포함됩니다. 이러한 조각을 사용하여 텍스트 섹션을 반복하고, 조건부 섹션을 만들고, 애플리케이션의 데이터를 표시할 수 있습니다.

 출력을 생성하기 위해 애플리케이션은 템플릿에 의해 생성된 함수를 호출합니다. 예를 들면 다음과 같습니다.

```csharp
string webResponseText = new MyTemplate().TransformText();

```

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 가 설치되지 않은 컴퓨터에서 애플리케이션을 실행할 수 있습니다.

 런타임 템플릿을 만들려면 **전처리된 텍스트 템플릿** 파일을 프로젝트에 추가합니다. 또는 일반 텍스트 파일을 추가하고 해당 **사용자 지정 도구** 속성을 **TextTemplatingFilePreprocessor**로 설정할 수 있습니다.

 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)을 참조 하세요. 템플릿 구문에 대 한 자세한 내용은 [T4 텍스트 템플릿 작성](../modeling/writing-a-t4-text-template.md)을 참조 하세요.

 **디자인 타임 T4 텍스트 템플릿** 은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에서 실행되어 소스 코드의 일부와 애플리케이션의 다른 리소스를 정의합니다.
일반적으로 단일 입력 파일이나 데이터베이스의 데이터를 읽고 `.cs`, `.vb`또는 다른 소스 파일의 일부를 생성하는 여러 템플릿을 사용합니다. 각 템플릿이 하나의 파일을 생성합니다. 템플릿은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 또는 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]내에서 실행됩니다.

 예를 들어 입력 데이터는 구성 데이터의 XML 파일일 수 있습니다. 개발 중에 XML 파일을 편집할 때마다 텍스트 템플릿에서 애플리케이션 코드의 일부가 다시 생성됩니다. 템플릿 중 하나는 다음 예제와 유사할 수 있습니다.

```
<#@ output extension=".txt" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}

```

 XML 파일의 값에 따라 생성된 `.cs` 파일은 다음과 유사합니다.

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

 또 다른 예로 비즈니스 활동의 워크플로 다이어그램을 입력으로 사용할 수 있습니다. 사용자가 비즈니스 워크플로를 변경하거나 다른 워크플로를 가진 새 사용자로 작업을 시작할 때 새 모델에 맞게 코드를 쉽게 다시 생성할 수 있습니다.

 디자인 타임 템플릿을 사용하면 요구 사항이 변경될 때 더 빠르고 안정적으로 구성을 변경할 수 있습니다. 일반적으로 입력은 워크플로 예제와 같이 비즈니스 요구 사항 측면에서 정의됩니다. 이렇게 하면 보다 쉽게 변경 내용을 사용자에게 설명할 수 있습니다. 따라서 디자인 타임 템플릿은 민첩한 개발 프로세스에 유용한 도구입니다.

 디자인 타임 템플릿을 만들려면 **텍스트 템플릿** 파일을 프로젝트에 추가합니다. 또는 일반 텍스트 파일을 추가하고 해당 **사용자 지정 도구** 속성을 **TextTemplatingFileGenerator**로 설정할 수 있습니다.

 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)을 참조 하세요. 템플릿 구문에 대 한 자세한 내용은 [T4 텍스트 템플릿 작성](../modeling/writing-a-t4-text-template.md)을 참조 하세요.

> [!NOTE]
> *모델* 이란 용어는 때때로 하나 이상의 템플릿에서 읽은 데이터를 설명하는 데 사용됩니다. 모델은 모든 형식과 종류의 파일 또는 데이터베이스일 수 있으며 UML 모델이나 도메인 특정 언어 모델이 아니어도 됩니다. '모델'은 단지 데이터가 코드와 달리 비즈니스 개념 측면에서 정의될 수 있음을 나타냅니다.

 텍스트 템플릿 변환 기능을 *T4*라고 합니다.

## <a name="in-this-section"></a>섹션 내용
 [T4 텍스트 템플릿을 사용 하 여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md) 텍스트 파일을 생성 하는 응용 프로그램에서 미리 컴파일된 텍스트 템플릿을 통해 쉽게 텍스트를 정의할 수 있습니다. 그러나 런타임에 변경되는 텍스트 템플릿에는 이 방법을 사용할 수 없습니다.

 [T4 텍스트 템플릿을 사용 하 여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md) 모델에서 코드 및 기타 리소스를 생성 하면 모델을 업데이트 하 여 응용 프로그램을 업데이트할 수 있습니다.

 [빌드 프로세스의 코드 생성](../modeling/code-generation-in-a-build-process.md) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 시각화 및 모델링 SDK를 설치한 경우 생성 된 소프트웨어가 모델의 변경 내용으로 최신 상태를 유지 하도록 할 수 있습니다.

 [T4 텍스트 템플릿 작성](../modeling/writing-a-t4-text-template.md) 텍스트 템플릿 파일의 구문입니다.

 [연습: 텍스트 템플릿을 사용 하 여 코드 생성](../modeling/walkthrough-generating-code-by-using-text-templates.md) 코드 생성을 사용 하는 한 가지 방법을 보여 줍니다.

 [T4 텍스트 템플릿 디버그](../modeling/debugging-a-t4-text-template.md) 텍스트 템플릿을 디버그 하는 방법 및 몇 가지 일반적인 텍스트 템플릿 오류입니다.

 [TextTransform 유틸리티를 사용 하 여 파일 생성](../modeling/generating-files-with-the-texttransform-utility.md) 텍스트 템플릿 변환을 실행 하는 데 사용할 수 있는 명령줄 도구입니다.

 [T4 텍스트 변환 사용자 지정](../modeling/customizing-t4-text-transformation.md) 고유한 데이터 원본에 대 한 지시문 프로세서 및 사용자 지정 템플릿 호스트를 작성 하는 방법입니다.

## <a name="see-also"></a>관련 항목
 [도메인 특정 언어에서 코드를 생성 하](../modeling/generating-code-from-a-domain-specific-language.md) [는 UML 모델에서 파일 생성](../modeling/generate-files-from-a-uml-model.md)
