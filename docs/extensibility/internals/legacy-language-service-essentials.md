---
title: 레거시 언어 서비스 필수 정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 501bccf755293e86e8a9dc23fce125a10c882376
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707419"
---
# <a name="legacy-language-service-essentials"></a>레거시 언어 서비스 필수 항목
프로그래밍 언어를 Visual Studio에 통합하려면 언어 서비스를 제공해야 합니다. 이 항목에서는 레거시 언어 서비스에서 사용할 수 있는 기능에 대해 설명합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 언어 서비스를 구현하는 새로운 방법에 대한 자세한 내용은 [편집기 및 언어 서비스 확장을](../../extensibility/editor-and-language-service-extensions.md)참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

 레거시 언어 서비스는 다음과 같은 기능을 제공합니다.

|기능|Description|
|-------------|-----------------|
|구문 색 지정|편집기 뷰가 언어의 다른 요소에 대해 서로 다른 색상과 글꼴 스타일을 표시하도록 합니다. 이러한 차별화를 통해 파일을 더 쉽게 읽고 편집할 수 있습니다.<br /><br /> 일반적인 내용은 [레거시 언어 서비스의 구문 색칠을](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)참조하십시오.<br /><br /> 관리되는 패키지 프레임워크(MPF)에서 이 기능에 대한 자세한 내용은 [레거시 언어 서비스의 색지정 구문을](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)참조하십시오.|
|문 완성|사용자가 입력을 시작한 명령문 또는 키워드를 완료합니다. 명령문 완성을 사용하면 입력 횟수가 줄어들고 오류가 발생하지 않는 등 어려운 문을 보다 쉽게 입력할 수 있습니다.<br /><br /> 일반 정보는 [레거시 언어 서비스의 명령문 완료를](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)참조하십시오.<br /><br /> MPF에서 이 기능에 대한 자세한 내용은 [레거시 언어 서비스의 Word 완료를](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)참조하십시오.|
|중괄호 일치|중괄호와 같은 페어링된 문자를 강조 표시됩니다. 사용자가 "}"와 같은 닫는 문자를 입력하면 중괄호 일치는 "{"와 같은 해당 오프닝 문자를 강조 표시됩니다. 여러 수준의 문자를 둘러싸는 경우 이 기능을 사용하면 둘러싸는 문자가 올바르게 페어링되어 있는지 확인할 수 있습니다.<br /><br /> MPF에서 이 기능에 대한 자세한 내용은 [레거시 언어 서비스에서 중괄호 일치를](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)참조하십시오.|
|매개 변수 정보 도구 설명|사용자가 현재 입력중인 오버로드 된 메서드에 대한 가능한 서명 목록을 표시합니다.<br /><br /> 일반 정보는 [레거시 언어 서비스의 매개 변수 정보를](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)참조하십시오.<br /><br /> MPF의 이 기능에 대한 자세한 내용은 [레거시 언어 서비스의 매개 변수 정보를](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)참조하십시오.|
|오류 마커|구문적으로 올바르지 않은 텍스트 아래에 물결 모양의 빨간색 밑줄(구불구불한 줄이라고도 함)을 표시합니다. 오류 마커는 일반적으로 맞춤법이 틀린 키워드, 닫히지 않은 괄호, 잘못된 문자 및 이와 유사한 오류를 사용자에게 알리는 데 사용됩니다.<br /><br /> MPF 클래스에서 오류 마커는 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> 클래스의 메서드에서 자동으로 처리됩니다.|

 이러한 기능 중 대부분은 소스 코드를 구문 분석하기 위해 언어 서비스가 필요합니다. 종종 컴파일러 또는 인터프리터에 대한 토큰화 및 구문 분석 코드를 다시 사용할 수 있습니다.

 다음 기능은 프로그래밍 언어 지원과 관련이 있지만 언어 서비스의 일부가 아닙니다.

| 기능 | Description |
|-----------------------| - |
| 표현식 계산기 | 중단점의 유효성을 검사하고 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Autos** 디버그 창에 표시할 식 목록을 제공하여 디버거를 지원합니다.<br /><br /> 자세한 내용은 [디버깅에 대한 언어 서비스 지원을](../../extensibility/internals/language-service-support-for-debugging.md)참조하십시오. |
| 심볼 브라우징 도구 | **개체 브라우저,** **클래스 보기,** **전화 브라우저**및 기호 **결과 찾기를**지원합니다. |
