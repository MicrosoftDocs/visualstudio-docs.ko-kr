---
title: T4 텍스트 템플릿 지시문
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7ceb5139ff133a0005efafd5dc96f20e22b73cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75591829"
---
# <a name="t4-text-template-directives"></a>T4 텍스트 템플릿 지시문

지시문은 텍스트 템플릿 변환 엔진에 명령을 제공합니다.

지시문의 구문은 다음과 같습니다.

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

모든 특성 값을 큰따옴표로 묶어야 합니다. 값 자체에 따옴표가 포함된 경우 \ 문자를 사용하여 이스케이프해야 합니다.

일반적으로 지시문은 템플릿 파일이나 포함된 파일의 첫 번째 요소입니다. 지시문을 코드 블록 `<#...#>` 내에 두거나 클래스 기능 블록 `<#+...#>` 뒤에 두면 안 됩니다.

[T4 템플릿 지시문](../modeling/t4-template-directive.md)

```
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>
```

[T4 매개 변수 지시문](../modeling/t4-parameter-directive.md)

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

[T4 Output 지시문](../modeling/t4-output-directive.md)

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

[T4 Assembly 지시문](../modeling/t4-assembly-directive.md)

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

[T4 Import 지시문](../modeling/t4-import-directive.md)

```
<#@ import namespace="namespace" #>
```

[T4 Include 지시문](../modeling/t4-include-directive.md)

```
<#@ include file="filePath" #>
```

[T4 CleanUpBehavior 지시문](../modeling/t4-cleanupbehavior-directive.md)

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

또한 고유한 지시문을 만들 수 있습니다. 자세한 내용은 [사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기](../modeling/creating-custom-t4-text-template-directive-processors.md)를 참조 하세요. Visualization and Modeling SDK를 사용하여 DSL(Domain-Specific Language)을 만드는 경우 지시문 프로세서가 DSL의 일부로 생성됩니다.
