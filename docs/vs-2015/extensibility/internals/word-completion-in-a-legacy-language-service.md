---
title: 레거시 언어 서비스의 단어 완성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], IntelliSense Complete Word
- IntelliSense, Complete Word
- Complete Word
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8b4449a30119d925b167213141c3ba577ce42609
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841686"
---
# <a name="word-completion-in-a-legacy-language-service"></a>레거시 언어 서비스의 단어 완성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

단어 완성은 부분적으로 형식화 된 단어에서 누락 된 문자를 채웁니다. 완료 문자가 하나만 있는 경우 완료 문자를 입력 하면 단어가 완료 됩니다. 부분 단어가 둘 이상의 가능성과 일치 하는 경우 가능한 완성 목록이 표시 됩니다. 완성 문자는 식별자에 사용 되지 않는 모든 문자일 수 있습니다.  
  
 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 자세히 알아보려면 [편집기 및 언어 서비스 확장](../../extensibility/extending-the-editor-and-language-services.md)을 참조 하세요.  
  
> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.  
  
## <a name="implementation-steps"></a>구현 단계  
  
1. 사용자가 **IntelliSense** 메뉴에서 **단어 자동 완성** 을 선택 하면 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 언어 서비스로 명령이 전송 됩니다.  
  
2. <xref:Microsoft.VisualStudio.Package.ViewFilter>클래스는 명령을 catch 하 고 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 구문 분석 이유를 사용 하 여 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Package.ParseReason> .  
  
3. <xref:Microsoft.VisualStudio.Package.Source>그런 다음 클래스는 메서드를 호출 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 하 여 가능한 단어 완성 목록을 가져온 다음 클래스를 사용 하 여 도구 설명 목록에 단어를 표시 합니다 <xref:Microsoft.VisualStudio.Package.CompletionSet> .  
  
    일치 하는 단어가 하나만 있는 경우 클래스는 <xref:Microsoft.VisualStudio.Package.Source> 단어를 완성 합니다.  
  
   또는 식별자의 첫 번째 문자를 입력할 때 스캐너가 트리거 값을 반환 하는 경우 <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source> 클래스는이를 검색 하 고 <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> 구문 분석 이유를 사용 하 여 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Package.ParseReason> . 이 경우 파서는 멤버 선택 문자가 있는지 검색 하 고 멤버 목록을 제공 해야 합니다.  
  
## <a name="enabling-support-for-the-complete-word"></a>단어 자동 완성 기능 사용  
 자동 완성 기능을 지원 하려면 `CodeSense` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 언어 패키지와 연결 된 user 특성에 전달 된 명명 된 매개 변수를 설정 합니다. 이 속성은 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 클래스의 속성을 설정 합니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  
  
 파서는 <xref:Microsoft.VisualStudio.Package.ParseReason> 단어 완성이 작동 하기 위해 구문 분석 이유 값에 대 한 응답으로 선언 목록을 반환 해야 합니다.  
  
## <a name="implementing-complete-word-in-the-parsesource-method"></a>ParseSource 메서드에서 Complete Word 구현  
 단어 완성의 경우 <xref:Microsoft.VisualStudio.Package.Source> 클래스는 클래스의 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> 메서드를 호출 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 하 여 가능한 단어 일치 항목의 목록을 가져옵니다. 클래스에서 파생 된 클래스에서 목록을 구현 해야 합니다 <xref:Microsoft.VisualStudio.Package.Declarations> . <xref:Microsoft.VisualStudio.Package.Declarations>구현 해야 하는 메서드에 대 한 자세한 내용은 클래스를 참조 하세요.  
  
 목록에 단어가 하나만 포함 되어 있으면 클래스에서 단어를 <xref:Microsoft.VisualStudio.Package.Source> 부분 단어 대신 자동으로 삽입 합니다. 목록에 둘 이상의 단어가 포함 된 경우 클래스는 <xref:Microsoft.VisualStudio.Package.Source> 사용자가 적절 한 선택을 선택할 수 있는 도구 설명 목록을 제공 합니다.  
  
 또한 <xref:Microsoft.VisualStudio.Package.Declarations> [레거시 언어 서비스에서 멤버 완성](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)의 클래스 구현에 대 한 예제를 살펴봅니다.
