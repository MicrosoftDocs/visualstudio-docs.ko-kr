---
title: 사용자 지정 편집기의 구문 색칠 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6296c8451684a121ac42dbde6619c0ebbb421908
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699332"
---
# <a name="syntax-coloring-in-custom-editors"></a>사용자 지정 편집기의 구문 색 지정
핵심 편집기를 포함한 Visual Studio 환경 SDK 편집자는 언어 서비스를 사용하여 특정 구문 항목을 식별하고 지정된 문서 보기에 지정된 색상으로 표시합니다.

## <a name="colorization-requirements"></a>색지정 요구 사항
 언어 서비스의 컬러라이저를 구현하는 모든 편집자는 다음을 수행해야 합니다.

1. 구현하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 개체를 사용하여 색을 칠할 텍스트를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 관리하고 텍스트의 문서 보기를 제공하기 위해 구현하는 개체를 사용합니다.

2. 언어 서비스의 식별 GUID를 사용하여 VSPackage의 서비스 공급자를 쿼리하여 특정 언어 서비스에 대한 인터페이스를 가져옵니다.

3. 을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 구현하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>개체의 메서드를 호출합니다. 이 메서드는 언어 서비스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> VSPackage에서 색을 칠할 텍스트를 관리하는 데 사용하는 구현과 연결합니다.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>언어 서비스의 컬러라이저의 핵심 편집자 사용
 코어 편집기의 인스턴스에서 컬러라이저가 있는 언어 서비스를 가져오는 경우 언어 서비스의 컬러라이저에 의한 텍스트 구문 분석 및 렌더링은 추가 개입 없이 자동으로 수행됩니다.

 IDE는 투명하게 다음을 수행합니다.

- 에 구현시 텍스트를 추가하거나 수정할 때 텍스트를 구문 분석하고 분석하기 위해 필요에 따라 colorizer를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>호출합니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 구현에서 제공하는 문서 뷰에서 제공하는 디스플레이가 컬러라이저에서 반환된 정보를 사용하여 업데이트되고 다시 그려지는지 확인합니다.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>언어 서비스의 컬러라이저의 비핵심 편집기 사용
 비핵심 편집기 인스턴스는 언어 서비스의 구문 색지정 서비스를 사용할 수도 있지만 서비스의 색채를 명시적으로 검색하고 적용하고 문서 뷰를 다시 그려야 합니다.

 이렇게 하려면 코어가 아닌 편집기는 다음을 수행해야 합니다.

1. 언어 서비스의 컬러라이저 개체(구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 및)를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>가져옵니다. VSPackage언어 서비스의 인터페이스에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 메서드를 호출 하 여이 작업을 수행 합니다.

2. 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 호출하여 특정 텍스트 범위의 색상을 달라고 요청합니다.

     메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 색이 칠되는 텍스트 범위의 각 문자에 대해 하나씩 값 배열을 반환합니다. 또한 텍스트 범위를 주석, 키워드 또는 데이터 유형과 같은 특정 유형의 색 항목으로 식별합니다.

3. 반환된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 색상 정보를 사용하여 텍스트를 다시 칠하고 표시합니다.

> [!NOTE]
> VSPackage는 언어 서비스의 컬러라이저를 사용하는 것 외에도 범용 Visual Studio 환경 SDK 텍스트 색칠 메커니즘을 사용하도록 선택할 수 있습니다. 이 메커니즘에 대한 자세한 내용은 [글꼴 및 색상 사용을](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)참조하십시오.

## <a name="see-also"></a>참조

- [레거시 언어 서비스의 구문 색 지정](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [구문 색 지정 구현](../extensibility/internals/implementing-syntax-coloring.md)
- [방법: 기본 제공 색 항목 사용](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [사용자 지정 색 항목](../extensibility/internals/custom-colorable-items.md)
