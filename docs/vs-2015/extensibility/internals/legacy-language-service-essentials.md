---
title: 레거시 언어 서비스 Essentials | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- languages, integrating into Visual Studio
- language services, integrating programming languages
- Visual Studio, integrating programming languages
- programming languages, integrating into Visual Studio
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a3926ff84f3b2e6415df1ca7333409c05d839685
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841363"
---
# <a name="legacy-language-service-essentials"></a>레거시 언어 서비스 필수 항목
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로그래밍 언어를 Visual Studio에 통합 하려면 언어 서비스를 제공 해야 합니다. 이 항목에서는 레거시 언어 서비스에서 사용할 수 있는 기능에 대해 설명 합니다.  
  
 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 언어 서비스를 구현 하는 새로운 방법에 대해 자세히 알아보려면 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)을 참조 하세요.  
  
> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.  
  
 레거시 언어 서비스는 다음과 같은 기능을 제공 합니다.  
  
|기능|Description|  
|-------------|-----------------|  
|구문 색 지정|편집기 보기에서 언어의 여러 요소에 대해 서로 다른 색과 글꼴 스타일을 표시 하도록 합니다. 이러한 구분을 통해 파일을 보다 쉽게 읽고 편집할 수 있습니다.<br /><br /> 일반 정보 [는 레거시 언어 서비스의 구문 색](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)지정을 참조 하세요.<br /><br /> MPF (managed package framework)의이 기능에 대 한 자세한 내용은 [레거시 언어 서비스의 구문 색 색상화](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)를 참조 하세요.|  
|문 완성|사용자가 입력을 시작한 문이나 키워드를 완료 합니다. 문 완성 기능을 사용 하면 입력이 줄어들고 오류가 발생할 가능성이 더 적기 때문에 어려운 문을 더 쉽게 입력할 수 있습니다.<br /><br /> 일반 정보는 [레거시 언어 서비스의 문 완성](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)을 참조 하세요.<br /><br /> MPF에서이 기능에 대 한 자세한 내용은 [레거시 언어 서비스의 단어 완성](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)을 참조 하세요.|  
|중괄호 일치|괄호와 같이 쌍을 이루는 문자를 강조 표시 합니다. 사용자가 "}"와 같은 닫는 문자를 입력 하면 중괄호 일치는 "{"와 같이 해당 하는 여는 문자를 강조 표시 합니다. 여러 수준을 포함 하는 문자를 사용 하는 경우이 기능을 통해 사용자는 바깥쪽 문자가 올바르게 쌍으로 연결 되어 있는지 확인할 수 있습니다.<br /><br /> MPF의이 기능에 대 한 자세한 내용은 [레거시 언어 서비스의 중괄호 일치](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)를 참조 하세요.|  
|매개 변수 정보 도구 설명|사용자가 현재 입력 하 고 있는 오버 로드 된 메서드의 가능한 서명 목록을 표시 합니다.<br /><br /> 일반 정보 [는 레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)를 참조 하세요.<br /><br /> MPF에서이 기능에 대 한 자세한 내용은 [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)를 참조 하세요.|  
|오류 표식|구문적으로 부정확 한 텍스트에서 물결 모양의 빨간색 밑줄을 표시 합니다. 오류 표식은 일반적으로 사용자가 철자가 잘못 된 키워드, 닫히지 않은 괄호, 잘못 된 문자 및 유사한 오류를 인식 하도록 하는 데 사용 됩니다.<br /><br /> MPF 클래스에서 오류 마커는 클래스의 메서드에서 자동으로 처리 됩니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> .|  
  
 이러한 기능 중 상당수는 소스 코드를 구문 분석 하기 위해 언어 서비스가 필요 합니다. 종종 컴파일러나 인터프리터에 대 한 토큰화 및 구문 분석 코드를 다시 사용할 수 있습니다.  
  
 다음 기능은 프로그래밍 언어에 대 한 지원과 관련이 있지만 언어 서비스의 일부가 아닙니다.  
  
|기능|Description|  
|-------------|-----------------|  
|식 계산기|는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 중단점의 유효성을 검사 하 고 **자동** 디버그 창에 표시할 식의 목록을 제공 하 여 디버거를 지원 합니다.<br /><br /> 자세한 내용은 [디버깅을 위한 언어 서비스 지원](../../extensibility/internals/language-service-support-for-debugging.md)을 참조 하세요.|  
|기호 검색 도구|**개체 브라우저**, **클래스 뷰**, **호출 브라우저**를 지원 하 고 **기호 결과를 찾습니다**.|
