---
title: 사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기
description: 텍스트 템플릿 변환 프로세스 및 사용자 지정 T4 텍스트 템플릿 지시문 프로세서를 만드는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59644275f17eac197074351a777959bb1826a5de
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389503"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기

*텍스트 템플릿 변환 프로세스는* 텍스트 *템플릿* 파일을 입력으로 받아서 출력으로 텍스트 파일을 생성합니다. *텍스트 템플릿 변환 엔진은* 프로세스를 제어하고 엔진은 텍스트 템플릿 변환 호스트 및 하나 이상의 텍스트 템플릿 지시문 프로세서와 상호 작용하여 프로세스를 *완료합니다.* 자세한 내용은 텍스트 템플릿 변환 프로세스 를 [참조하세요.](../modeling/the-text-template-transformation-process.md)

사용자 지정 지시문 프로세서를 만들려면 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 또는 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>에서 상속하는 클래스를 만듭니다.

이 두 가지의 차이점은 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 사용자로부터 매개 변수를 얻고 템플릿 출력 파일을 생성하는 코드를 생성하는 데 필요한 최소 인터페이스를 구현한다는 것입니다. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 는 requires/provides 디자인 패턴을 구현합니다. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 는 두 개의 특수 매개 변수 및 를 `requires` `provides` 처리합니다.  예를 들어 사용자 지정 지시문 프로세서는 사용자의 파일 이름을 수락하고, 파일을 열고 읽은 다음, 파일의 텍스트를 라는 변수에 저장할 수 `fileText` 있습니다. 클래스의 서브클래스에서는 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 사용자의 파일 이름을 매개 변수 값으로, 텍스트를 매개 변수 값으로 저장할 변수의 이름을 지정할 수 `requires` `provides` 있습니다. 이 프로세서는 파일을 열고 읽은 다음 지정된 변수에 파일 텍스트를 저장합니다.

Visual Studio 텍스트 템플릿에서 사용자 지정 지시문 프로세서를 호출하기 전에 해당 프로세서를 등록해야 합니다.

레지스트리 키를 추가하는 방법에 대한 자세한 내용은 [사용자 지정 지시문 프로세서 배포를 참조하세요.](../modeling/deploying-a-custom-directive-processor.md)

## <a name="custom-directives"></a>사용자 지정 지시문

사용자 지정 지시문은 다음과 같습니다.

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

텍스트 템플릿에서 외부 데이터 또는 리소스에 액세스하려는 경우 사용자 지정 지시문 프로세서를 사용할 수 있습니다.

다른 텍스트 템플릿은 단일 지시문 프로세서가 제공하는 기능을 공유할 수 있으므로 지시문 프로세서는 다시 사용할 코드를 팩터하는 방법을 제공합니다. 기본 제공 `include` 지시문은 코드를 팩터 아웃하고 다른 텍스트 템플릿 간에 공유하는 데 사용할 수 있으므로 유사합니다. 차이점은 `include` 지시문에서 제공하는 기능이 고정되어 매개 변수를 허용하지 않는다는 것입니다. 텍스트 템플릿에 공통 기능을 제공하고 템플릿이 매개 변수를 전달하도록 허용하려면 사용자 지정 지시문 프로세서를 만들어야 합니다.

사용자 지정 지시문 프로세서의 몇 가지 예는 다음과 같습니다.

- 사용자 이름과 암호를 매개 변수로 허용하는 데이터베이스에서 데이터를 반환하는 지시문 프로세서입니다.

- 파일 이름을 매개 변수로 허용하는 파일을 열고 읽을 지시문 프로세서입니다.

### <a name="principal-parts-of-a-custom-directive-processor"></a>사용자 지정 지시문 프로세서의 주요 부분

지시문 프로세서를 개발하려면 또는 에서 상속되는 클래스를 만들어야 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 합니다.

구현해야 하는 가장 중요한 `DirectiveProcessor` 메서드는 다음과 같습니다.

- `bool IsDirectiveSupported(string directiveName)` - `true` 지시문 프로세서가 명명된 지시문을 처리할 수 있으면 를 반환합니다.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` - 템플릿 엔진은 템플릿에서 지시문이 발생할 때마다 이 메서드를 호출합니다. 프로세서가 결과를 저장해야 합니다.

ProcessDirective()에 대한 모든 호출 후에 템플릿 엔진은 다음 메서드를 호출합니다.

- `string[] GetReferencesForProcessingRun()` - 템플릿 코드에 필요한 어셈블리의 이름을 반환합니다.

- `string[] GetImportsForProcessingRun()` - 템플릿 코드에서 사용할 수 있는 네임스페이스를 반환합니다.

- `string GetClassCodeForProcessingRun()` - 템플릿 코드에서 사용할 수 있는 메서드, 속성 및 기타 선언의 코드를 반환합니다. 이 작업을 수행하는 가장 쉬운 방법은 C# 또는 Visual Basic 코드를 포함하는 문자열을 빌드하는 것입니다. 모든 CLR 언어를 사용하는 템플릿에서 지시문 프로세서를 호출할 수 있도록 하려면 문을 CodeDom 트리로 생성한 다음 템플릿에서 사용하는 언어로 트리를 serializing한 결과를 반환할 수 있습니다.

- 자세한 내용은 [연습: 사용자 지정 지시문 프로세서 만들기를 참조하세요.](../modeling/walkthrough-creating-a-custom-directive-processor.md)

## <a name="see-also"></a>참조

- [사용자 지정 지시문 프로세서 배포에서는 사용자](../modeling/deploying-a-custom-directive-processor.md) 지정 지시문 프로세서를 등록하는 방법을 설명합니다.
- [연습: 사용자 지정 지시문 프로세서 만들기에서는 사용자 지정 지시문 프로세서를](../modeling/walkthrough-creating-a-custom-directive-processor.md) 만드는 방법, 지시문 프로세서를 등록 및 테스트하는 방법 및 출력 파일의 서식을 HTML로 지정하는 방법을 설명합니다.
