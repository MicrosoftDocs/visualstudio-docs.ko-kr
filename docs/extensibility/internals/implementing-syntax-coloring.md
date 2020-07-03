---
title: 구문 색 지정 구현 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb3f26f59d7cbc994da1d2537e0ab352ce12205e
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905210"
---
# <a name="implementing-syntax-coloring"></a>구문 색 지정 구현
언어 서비스에서 구문 색 지정을 제공 하는 경우 파서는 텍스트 줄을 색 항목 배열로 변환 하 고 이러한 색 항목에 해당 하는 토큰 형식을 반환 합니다. 파서는 색 항목 목록에 속하는 토큰 형식을 반환 해야 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]svc 개체에 의해 적절 한 토큰 형식에 할당 된 특성에 따라 코드 창의 각 색 항목을 표시 합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]는 파서 인터페이스를 지정 하지 않으며 파서 구현은 사용자에 게 완전히 있습니다. 그러나 기본 파서 구현은 Visual Studio 언어 패키지 프로젝트에서 제공 됩니다. 관리 코드의 경우 MPF (관리 패키지 프레임 워크)는 텍스트 색을 완벽 하 게 지원 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 구문 색 지정을 구현 하는 새로운 방법에 대해 자세히 알아보려면 [연습: 텍스트 강조](../../extensibility/walkthrough-highlighting-text.md)표시를 참조 하세요.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>편집기에서 텍스트 색상화를 수행 하는 단계

1. 편집기는 개체에서 메서드를 호출 하 여 svc를 가져옵니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .

2. 편집기는 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> 하 여 svc가 svc 외부에서 유지 되어야 하는 각 줄의 상태를 요구 하는지 여부를 확인 합니다.

3. Svc가 svc 외부에서 상태를 유지 해야 하는 경우 편집기는 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> 하 여 첫 번째 줄의 상태를 가져옵니다.

4. 편집기는 버퍼의 각 줄에 대해 다음 단계를 수행 하는 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> .

    1. 텍스트 줄은 텍스트를 토큰으로 변환 하기 위해 스캐너에 전달 됩니다. 각 토큰은 토큰 텍스트와 토큰 유형을 지정 합니다.

    2. 토큰 유형이 색 항목 목록에 대 한 인덱스로 변환 됩니다.

    3. 토큰 정보는 배열의 각 요소가 줄의 문자에 해당 하는 배열을 채우는 데 사용 됩니다. 배열에 저장 된 값은 색 항목 목록에 있는 인덱스입니다.

    4. 줄의 끝에 있는 상태는 각 줄에 대해 반환 됩니다.

5. Svc에 상태를 유지 해야 하는 경우 편집기는 해당 줄의 상태를 캐시 합니다.

6. 편집기는 메서드에서 반환 된 정보를 사용 하 여 텍스트 줄을 렌더링 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> . 이 경우 다음 단계를 수행해야 합니다.

    1. 줄의 각 문자에 대해 색 항목 인덱스를 가져옵니다.

    2. 기본 색 항목을 사용 하는 경우 편집기의 색 항목 목록에 액세스 합니다.

    3. 그렇지 않으면 언어 서비스의 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 하 여 색 항목을 가져옵니다.

    4. 색 항목의 정보를 사용 하 여 텍스트를 표시로 렌더링 합니다.

## <a name="managed-package-framework-colorizer"></a>관리 되는 패키지 프레임 워크 Svc
 MPF (관리 되는 패키지 프레임 워크)는 svc을 구현 하는 데 필요한 모든 클래스를 제공 합니다. 언어 서비스 클래스는 클래스를 상속 <xref:Microsoft.VisualStudio.Package.LanguageService> 하 고 필요한 메서드를 구현 해야 합니다. 인터페이스를 구현 하 여 스캐너 및 파서를 제공 하 <xref:Microsoft.VisualStudio.Package.IScanner> 고, <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 메서드 (클래스에서 구현 해야 하는 메서드 중 하나)에서 해당 인터페이스의 인스턴스를 반환 해야 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService> . 자세한 내용은 [레거시 언어 서비스의 구문 색 색상화](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)를 참조 하세요.

## <a name="see-also"></a>참조
- [방법: 기본 제공 색 항목 사용](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [사용자 지정 색 항목](../../extensibility/internals/custom-colorable-items.md)
- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
