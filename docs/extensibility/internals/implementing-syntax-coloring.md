---
title: 구문 색칠 하기 구현 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 83ce66dd6a31e3ef852feb91e2ba304e6688a723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707640"
---
# <a name="implementing-syntax-coloring"></a>구문 색 지정 구현
언어 서비스가 구문 색지정을 제공하는 경우 파서는 텍스트 줄을 색이 가능한 항목의 배열로 변환하고 이러한 색 항목에 해당하는 토큰 형식을 반환합니다. 파서는 색이 가능한 항목 목록에 속하는 토큰 형식을 반환해야 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]은 적절한 토큰 유형에 착색기 개체에 의해 할당 된 특성에 따라 코드 창에서 각 색 항목을 표시합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]파서 인터페이스를 지정하지 않으며 파서 구현은 전적으로 사용자에게 달려 있습니다. 그러나 기본 파서 구현은 Visual Studio 언어 패키지 프로젝트에 제공됩니다. 관리 코드의 경우 MPF(관리되는 패키지 프레임워크)는 텍스트 의 색지정을 완벽하게 지원합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 구문 색칠을 구현하는 새로운 방법에 대한 자세한 내용은 [연습: 텍스트 강조 표시](../../extensibility/walkthrough-highlighting-text.md)를 참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>텍스트 색상을 지정하는 편집기 다음단계

1. 편집기는 개체에서 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 호출하여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> colorizer를 가져옵니다.

2. 편집기는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> 컬러라이저가 컬러라이저 외부에서 유지 관리해야 하는 각 줄의 상태를 결정하는 메서드를 호출합니다.

3. 착색기에서 색채를 유지 하여 색채를 유지해야 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> 하는 경우 편집기는 첫 번째 줄의 상태를 얻기 위해 메서드를 호출합니다.

4. 버퍼의 각 줄에 대해 편집기는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 다음 단계를 수행하는 메서드를 호출합니다.

    1. 텍스트 줄은 텍스트를 토큰으로 변환하기 위해 스캐너에 전달됩니다. 각 토큰은 토큰 텍스트와 토큰 유형을 지정합니다.

    2. 토큰 유형은 색이 가능한 항목 목록으로 인덱스로 변환됩니다.

    3. 토큰 정보는 배열의 각 요소가 줄의 문자에 해당하도록 배열을 채우는 데 사용됩니다. 배열에 저장된 값은 색이 가능한 항목 목록에 대한 인덱스입니다.

    4. 줄 끝에 있는 상태가 각 줄에 대해 반환됩니다.

5. 컬러라이저에서 상태를 유지 관리해야 하는 경우 편집기는 해당 줄의 상태를 캐시합니다.

6. 편집기는 메서드에서 반환된 정보를 사용하여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 텍스트 줄을 렌더링합니다. 이 경우 다음 단계를 수행해야 합니다.

    1. 줄의 각 문자에 대해 색상 항목 인덱스를 가져옵니다.

    2. 기본 색상 항목을 사용하는 경우 편집기의 색상 항목 목록에 액세스합니다.

    3. 그렇지 않으면 언어 서비스의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 메서드를 호출하여 색 항목을 가져옵니다.

    4. 색 항목의 정보를 사용하여 텍스트를 디스플레이에 렌더링합니다.

## <a name="managed-package-framework-colorizer"></a>관리되는 패키지 프레임워크 컬러라이저
 MPF(관리되는 패키지 프레임워크)는 컬러라이저를 구현하는 데 필요한 모든 클래스를 제공합니다. 언어 서비스 클래스는 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스를 상속하고 필요한 메서드를 구현해야 합니다. <xref:Microsoft.VisualStudio.Package.IScanner> 인터페이스를 구현하여 스캐너와 파서를 제공하고 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 메서드(클래스에서 구현해야 하는 메서드 중 하나)에서 해당 인터페이스의 인스턴스를 <xref:Microsoft.VisualStudio.Package.LanguageService> 반환해야 합니다. 자세한 내용은 [레거시 언어 서비스의 색지정 구문을](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)참조하십시오.

## <a name="see-also"></a>참조
- [방법: 기본 제공 색 항목 사용](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [사용자 지정 색 항목](../../extensibility/internals/custom-colorable-items.md)
- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
