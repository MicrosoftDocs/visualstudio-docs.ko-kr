---
title: 레거시 언어 서비스의 요약 정보 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705938"
---
# <a name="quick-info-in-a-legacy-language-service"></a>레거시 언어 서비스의 빠른 정보
IntelliSense 빠른 정보는 사용자가 식별자에 캐럿을 배치 하 고 **intellisense** 메뉴에서 **요약 정보** 를 선택 하거나 식별자 위에 마우스 커서를 둘 때 원본에서 식별자에 대 한 정보를 표시 합니다. 이렇게 하면 식별자에 대 한 정보와 함께 도구 설명이 표시 됩니다. 이 정보는 일반적으로 식별자 형식으로 구성 됩니다. 디버그 엔진이 활성화 된 경우이 정보에는 현재 값이 포함 될 수 있습니다. 디버그 엔진은 식 값을 제공 하는 반면 언어 서비스는 식별자만 처리 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 자세히 알아보려면 [연습: QuickInfo 도구 설명 표시](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)를 참조 하세요.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

 MPF (관리 패키지 프레임 워크) 언어 서비스 클래스는 IntelliSense 요약 정보 도구 설명을 표시 하기 위한 완전 한 지원을 제공 합니다. 표시 되는 텍스트를 제공 하 고 요약 정보 기능을 사용 하도록 설정 하면 됩니다.

 표시 될 텍스트는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 구문 분석 이유 값을 사용 하 여 메서드 파서를 호출 하 여 가져옵니다 <xref:Microsoft.VisualStudio.Package.ParseReason> . 이러한 이유는 개체에 지정 된 위치에서 식별자에 대 한 형식 정보 (또는 빠른 정보 도구 설명에 표시 되는 적절 한 항목)를 가져오도록 파서에 지시 합니다 <xref:Microsoft.VisualStudio.Package.ParseRequest> . <xref:Microsoft.VisualStudio.Package.ParseRequest>개체는 메서드에 전달 된 개체입니다 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> .

 파서는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 모든 식별자의 형식을 확인 하기 위해 개체의 모든 위치를 구문 분석 해야 합니다. 그러면 파서가 구문 분석 요청 위치에서 식별자를 가져와야 합니다. 마지막으로, 파서가 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 메서드에서 텍스트를 반환할 수 있도록 해당 식별자와 연결 된 도구 설명 데이터를 개체에 전달 해야 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> .

## <a name="enabling-the-quick-info-feature"></a>요약 정보 기능 사용
 요약 정보 기능을 사용 하도록 설정 하려면 `CodeSense` 의 및 명명 된 `QuickInfo` 매개 변수를 설정 해야 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . 이러한 특성은 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 및 속성을 설정 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> 합니다.

## <a name="implementing-the-quick-info-feature"></a>요약 정보 기능 구현
 <xref:Microsoft.VisualStudio.Package.ViewFilter>클래스는 IntelliSense 요약 정보 작업을 처리 합니다. <xref:Microsoft.VisualStudio.Package.ViewFilter>클래스가 명령을 받는 경우 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 클래스는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 구문 분석 이유를 사용 하 여 메서드를 호출 <xref:Microsoft.VisualStudio.Package.ParseReason> 하 고 명령이 전송 될 때 캐럿의 위치를 호출 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 합니다. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>그러면 메서드 파서가 지정 된 위치까지 소스를 구문 분석 한 다음 지정 된 위치에 있는 식별자를 구문 분석 하 여 요약 정보 도구 설명에 표시할 항목을 결정 해야 합니다.

 대부분의 파서는 전체 소스 파일에 대 한 초기 구문 분석을 수행 하 고 결과를 구문 분석 트리에 저장 합니다. 이 메서드에 전달 될 때 전체 구문 분석이 수행 됩니다 <xref:Microsoft.VisualStudio.Package.ParseReason> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . 그런 다음 구문 분석 트리를 사용 하 여 원하는 정보를 가져올 수 있습니다.

 예를 들어 구문 분석 이유 값의는 <xref:Microsoft.VisualStudio.Package.ParseReason> 소스 위치에서 식별자를 찾고 구문 분석 트리에서 검색 하 여 형식 정보를 가져올 수 있습니다. 이 형식 정보는 클래스로 전달 되며 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 메서드에서 반환 됩니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> .
