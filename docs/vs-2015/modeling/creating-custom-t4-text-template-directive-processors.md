---
title: 사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
ms.assetid: 422b47af-5441-4b02-b5ad-1b8b328457e3
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eef9fd14dc78ff1f377ffb94bcf76fde0c401783
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651209"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>사용자 지정 T4 텍스트 템플릿 지시문 프로세서 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 *템플릿 변환 프로세스* 는 텍스트 *템플릿* 파일을 입력으로 사용 하 고 텍스트 파일을 출력으로 생성 합니다. *텍스트 템플릿 변환 엔진* 은 프로세스를 제어 하 고, 엔진은 텍스트 템플릿 변환 호스트 및 하나 이상의 텍스트 템플릿 *지시문 프로세서* 와 상호 작용 하 여 프로세스를 완료 합니다. 자세한 내용은 [텍스트 템플릿 변환 프로세스](../modeling/the-text-template-transformation-process.md)를 참조 하세요.

 사용자 지정 지시문 프로세서를 만들려면 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 또는 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>에서 상속하는 클래스를 만듭니다.

 이러한 두 가지 간의 차이점은 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> 사용자 로부터 매개 변수를 가져오고 템플릿 출력 파일을 생성 하는 코드를 생성 하는 데 필요한 최소 인터페이스를 구현 한다는 것입니다. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> requires/제공 디자인 패턴을 구현 합니다. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 및의 두 가지 특수 매개 변수를 처리 `requires` `provides` 합니다.  예를 들어 사용자 지정 지시문 프로세서는 사용자의 파일 이름을 허용 하 고, 파일을 열고 읽고, 파일의 텍스트를 라는 변수에 저장할 수 있습니다 `fileText` . 클래스의 서브 클래스는 <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> 사용자의 파일 이름을 `requires` 매개 변수의 값으로, 텍스트를 매개 변수의 값으로 저장할 변수의 이름을 사용할 수 있습니다 `provides` . 이 프로세서는 파일을 열고 읽은 다음 지정 된 변수에 파일의 텍스트를 저장 합니다.

 의 텍스트 템플릿에서 사용자 지정 지시문 프로세서를 호출 하기 전에 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 이를 등록 해야 합니다.

 레지스트리 키를 추가 하는 방법에 대 한 자세한 내용은 [사용자 지정 지시문 프로세서 배포](../modeling/deploying-a-custom-directive-processor.md)를 참조 하세요.

## <a name="custom-directives"></a>사용자 지정 지시문
 사용자 지정 지시문은 다음과 같습니다.

 `<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" … #>`

 텍스트 템플릿에서 외부 데이터 또는 리소스에 액세스 하려는 경우 사용자 지정 지시문 프로세서를 사용할 수 있습니다.

 다른 텍스트 템플릿에서는 단일 지시문 프로세서가 제공 하는 기능을 공유할 수 있으므로 지시문 프로세서는 다시 사용할 코드를 지정 하는 방법을 제공 합니다. 기본 제공 `include` 지시문은 코드를 구분 하는 데 사용할 수 있으며 다른 텍스트 템플릿 간에 공유할 수 있기 때문에 비슷합니다. 차이점은 지시문이 제공 하는 모든 기능이 `include` 고정 되어 있고 매개 변수를 허용 하지 않는다는 것입니다. 텍스트 템플릿에 일반적인 기능을 제공 하 고 템플릿이 매개 변수를 전달할 수 있도록 하려면 사용자 지정 지시문 프로세서를 만들어야 합니다.

 사용자 지정 지시문 프로세서의 몇 가지 예는 다음과 같습니다.

- 사용자 이름 및 암호를 매개 변수로 허용 하는 데이터베이스에서 데이터를 반환 하는 지시문 프로세서

- 파일 이름을 매개 변수로 허용 하는 파일을 열고 읽는 지시문 프로세서입니다.

### <a name="principal-parts-of-a-custom-directive-processor"></a>사용자 지정 지시문 프로세서의 주요 부분
 지시문 프로세서를 개발 하려면 또는에서 상속 되는 클래스를 만들어야 합니다 <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

 `DirectiveProcessor`구현 해야 하는 가장 중요 한 메서드는 다음과 같습니다.

- `bool IsDirectiveSupported(string directiveName)` - `true` 지시문 프로세서에서 명명 된 지시문을 처리할 수 있으면를 반환 합니다.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -템플릿 엔진은 템플릿에서 지시문이 발생할 때마다이 메서드를 호출 합니다. 프로세서에서 결과를 저장 해야 합니다.

  ProcessDirective ()를 호출한 후 템플릿 엔진은 다음 메서드를 호출 합니다.

- `string[] GetReferencesForProcessingRun()` -템플릿 코드에 필요한 어셈블리의 이름을 반환 합니다.

- `string[] GetImportsForProcessingRun()` -템플릿 코드에서 사용할 수 있는 네임 스페이스를 반환 합니다.

- `string GetClassCodeForProcessingRun()` -템플릿 코드에서 사용할 수 있는 메서드, 속성 및 기타 선언의 코드를 반환 합니다. 이 작업을 수행 하는 가장 쉬운 방법은 c # 또는 Visual Basic 코드를 포함 하는 문자열을 작성 하는 것입니다. CLR 언어를 사용 하는 템플릿에서 지시문 프로세서를 호출할 수 있도록 하려면 문을 CodeDom 트리로 만든 다음 템플릿에 사용 된 언어로 트리를 serialize 한 결과를 반환할 수 있습니다.

- 자세한 내용은 [연습: 사용자 지정 지시문 프로세서 만들기](../modeling/walkthrough-creating-a-custom-directive-processor.md)를 참조 하세요.

## <a name="in-this-section"></a>섹션 내용
 [사용자 지정 지시문 프로세서 배포](../modeling/deploying-a-custom-directive-processor.md) 사용자 지정 지시문 프로세서를 등록 하는 방법을 설명 합니다.

 [연습: 사용자 지정 지시문 프로세서 만들기](../modeling/walkthrough-creating-a-custom-directive-processor.md) 사용자 지정 지시문 프로세서를 만드는 방법, 지시문 프로세서를 등록 하 고 테스트 하는 방법 및 출력 파일을 HTML로 서식 지정 하는 방법을 설명 합니다.
