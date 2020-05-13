---
title: 레거시 언어 서비스의 빠른 정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d070c607313b406f036a5b6f071eaa371070408
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705938"
---
# <a name="quick-info-in-a-legacy-language-service"></a>레거시 언어 서비스의 빠른 정보
IntelliSense 빠른 정보는 사용자가 식별자에서 캐러를 배치하고 **IntelliSense** 메뉴에서 **빠른 정보를** 선택하거나 식별자 위에 마우스 커서를 보유할 때 소스의 식별자에 대한 정보를 표시합니다. 이렇게 하면 도구 설명이 식별자에 대한 정보와 함께 표시됩니다. 이 정보는 일반적으로 식별자 유형으로 구성됩니다. 디버그 엔진이 활성 상태일 때 이 정보에는 현재 값이 포함될 수 있습니다. 디버그 엔진은 표현식 값을 제공하지만 언어 서비스는 식별자만 처리합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 자세한 내용은 [연습: QuickInfo 도구 설명 표시를](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

 MPF(관리되는 패키지 프레임워크) 언어 서비스 클래스는 IntelliSense 빠른 정보 도구 팁을 표시하기 위한 완전한 지원을 제공합니다. 표시할 텍스트를 제공하고 빠른 정보 기능을 활성화하기만 하면 됩니다.

 표시할 텍스트는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.ParseReason>의 구문 분석 값으로 메서드 파서를 호출하여 가져옵니다. 이러한 이유로 파서는 개체에 지정된 위치에서 식별자에 대한 형식 정보(또는 빠른 정보 도구 설명에 표시하기에 적합한 정보)를 가져오도록 <xref:Microsoft.VisualStudio.Package.ParseRequest> 지시합니다. 개체는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 메서드에 전달된 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 개체입니다.

 파서는 모든 식별자의 유형을 결정하기 위해 <xref:Microsoft.VisualStudio.Package.ParseRequest> 개체의 위치까지 모든 것을 구문 분석해야 합니다. 그런 다음 파서는 구문 분석 요청 위치에서 식별자를 얻어야 합니다. 마지막으로, 파서는 개체가 메서드에서 텍스트를 반환할 수 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 있도록 해당 식별자와 연결된 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> 도구 설명 데이터를 개체에 전달해야 합니다.

## <a name="enabling-the-quick-info-feature"></a>빠른 정보 기능 활성화
 빠른 정보 기능을 사용하려면 `CodeSense` `QuickInfo` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>의 매개 변수및 명명된 매개변수를 설정해야 합니다. 이러한 특성은 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 및 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> 속성을 설정합니다.

## <a name="implementing-the-quick-info-feature"></a>빠른 정보 기능 구현
 클래스는 <xref:Microsoft.VisualStudio.Package.ViewFilter> IntelliSense 빠른 정보 작업을 처리합니다. 클래스가 <xref:Microsoft.VisualStudio.Package.ViewFilter> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 명령을 수신하면 클래스는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 명령을 보낼 때의 <xref:Microsoft.VisualStudio.Package.ParseReason> 구문 분석 이유와 카포트의 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 위치를 사용하여 메서드를 호출합니다. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 그런 다음 메서드 파서는 소스를 지정된 위치까지 구문 분석한 다음 지정된 위치에서 식별자를 구문 분석하여 빠른 정보 도구 설명에 표시할 내용을 결정해야 합니다.

 대부분의 구문 분석자는 전체 소스 파일의 초기 구문 분석 작업을 수행하여 결과를 구문 분석 트리에 저장합니다. 전체 구문 분석 메서드에 <xref:Microsoft.VisualStudio.Package.ParseReason> 전달 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 될 때 수행 됩니다. 그런 다음 구문 분석의 다른 종류는 구문 분석 트리를 사용하여 원하는 정보를 얻을 수 있습니다.

 예를 들어 구문 분석 이유 <xref:Microsoft.VisualStudio.Package.ParseReason> 값은 소스 위치에서 식별자를 찾아 구문 분석 트리에서 찾아 형식 정보를 가져올 수 있습니다. 그런 다음 이 형식 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 정보가 클래스에 전달되고 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> 메서드에 의해 반환됩니다.
