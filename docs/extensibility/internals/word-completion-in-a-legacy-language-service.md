---
title: 레거시 언어 서비스에서 단어 완성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 948751cde5b6b710d911a30ca26a61e5411bba4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703171"
---
# <a name="word-completion-in-a-legacy-language-service"></a>레거시 언어 서비스의 단어 완성
단어 완성은 부분적으로 입력된 단어의 누락된 문자를 채웁니다. 완료가 하나만 있으면 완료 문자를 입력할 때 단어가 완료됩니다. 부분 단어가 두 개 이상의 가능성과 일치하면 가능한 완료 목록이 표시됩니다. 완성 문자는 식별자에 사용되지 않는 모든 문자일 수 있습니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 자세한 내용은 [편집기 및 언어 서비스 확장을](../../extensibility/extending-the-editor-and-language-services.md)참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

## <a name="implementation-steps"></a>구현 단계

1. 사용자가 **IntelliSense** 메뉴에서 **단어 완료를** 선택하면 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 명령이 언어 서비스로 전송됩니다.

2. 클래스는 <xref:Microsoft.VisualStudio.Package.ViewFilter> 명령을 catch하고 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.ParseReason>의 구문 분석 이유로 메서드를 호출합니다.

3. 그런 <xref:Microsoft.VisualStudio.Package.Source> 다음 클래스는 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 호출하여 가능한 단어 완성 목록을 가져옵니다. <xref:Microsoft.VisualStudio.Package.CompletionSet>

    일치하는 단어가 하나만 있으면 <xref:Microsoft.VisualStudio.Package.Source> 클래스에서 단어를 완료합니다.

   또는 식별자의 첫 번째 문자를 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 입력할 때 스캐너가 트리거 값을 <xref:Microsoft.VisualStudio.Package.Source> 반환하는 경우 클래스는 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 이를 감지하고 <xref:Microsoft.VisualStudio.Package.ParseReason>의 구문 분석 이유로 메서드를 호출합니다. 이 경우 파서는 멤버 선택 문자의 존재를 감지하고 멤버 목록을 제공해야 합니다.

## <a name="enabling-support-for-the-complete-word"></a>완전한 단어에 대한 지원 활성화
 단어 완성에 대한 지원을 `CodeSense` 활성화하려면 언어 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 패키지와 연결된 사용자 특성에 전달된 명명된 매개 변수를 설정합니다. 이렇게 하면 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 클래스의 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 속성이 설정됩니다.

 구문 분석기는 단어 완성이 작동하려면 구문 분석 <xref:Microsoft.VisualStudio.Package.ParseReason>이유 값에 대한 응답으로 선언 목록을 반환해야 합니다.

## <a name="implementing-complete-word-in-the-parsesource-method"></a>구문 분석 소스 메서드에서 전체 단어 구현
 단어 완성을 <xref:Microsoft.VisualStudio.Package.Source> 위해 클래스는 클래스의 메서드를 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> 호출하여 가능한 단어 일치 목록을 가져옵니다. 클래스에서 파생 된 클래스에서 <xref:Microsoft.VisualStudio.Package.Declarations> 목록을 구현 해야 합니다. 구현해야 <xref:Microsoft.VisualStudio.Package.Declarations> 하는 방법에 대한 자세한 내용은 클래스를 참조하십시오.

 목록에 단일 단어만 포함하면 클래스는 <xref:Microsoft.VisualStudio.Package.Source> 부분 단어 대신 해당 단어를 자동으로 삽입합니다. 목록에 두 개 이상의 단어가 <xref:Microsoft.VisualStudio.Package.Source> 포함된 경우 클래스에는 사용자가 적절한 선택을 선택할 수 있는 도구 설명 목록이 표시됩니다.

 또한 레거시 언어 서비스에서 <xref:Microsoft.VisualStudio.Package.Declarations> 멤버 [완료에서](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)클래스 구현의 예를 살펴보십시오.
