---
title: 레거시 언어 서비스의 구문 색칠 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring
- language services, syntax coloring
ms.assetid: f65ff67e-8c20-497a-bebf-5e2a5b5b012f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2589ec24f230287306e0ff7e802d381fb6ab18b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704753"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>레거시 언어 서비스의 구문 색 지정

Visual Studio는 색칠 서비스를 사용하여 언어의 요소를 식별하고 편집기에서 지정된 색상으로 표시합니다.

## <a name="colorizer-model"></a>컬러라이저 모델
 언어 서비스는 편집기에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 사용되는 인터페이스를 구현합니다. 이 구현은 다음 그림과 같이 언어 서비스와는 별개의 개체입니다.

 ![SVC 색 지정기 그래픽](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> 구문 색칠 서비스는 텍스트 색지정을 위한 일반 Visual Studio 메커니즘과 는 별개입니다. 색상 지정을 지원하는 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 일반 메커니즘에 대한 자세한 내용은 [글꼴 및 색상 사용을](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)참조하십시오.

 컬러라이저 외에도 언어 서비스는 사용자 지정 색상 항목을 제공한다고 광고하여 편집기에서 사용하는 사용자 지정 색상 항목을 제공할 수 있습니다. 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 구현하는 동일한 개체에 인터페이스를 구현하여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 이 작업을 수행할 수 있습니다. 편집기에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 메서드를 호출할 때 사용자 지정 색상 항목 수를 반환 하 고 편집기 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 메서드를 호출할 때 개별 사용자 지정 색상 항목을 반환 합니다.

 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 인터페이스를 구현 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 개체를 반환 합니다. 언어 서비스가 24비트 또는 높은 색상 값을 지원하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 경우 인터페이스와 동일한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 개체에서 인터페이스를 구현해야 합니다.

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VS패키지가 언어 서비스 컬러라이저를 사용하는 방법

1. VSPackage는 다음을 수행 하려면 언어 서비스 VSPackage 필요 하는 적절 한 언어 서비스를 받아야 합니다.

    1. 인터페이스를 구현하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 개체를 사용하여 텍스트를 색칠하도록 합니다.

         텍스트는 일반적으로 인터페이스를 구현하는 개체를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 사용하여 표시됩니다.

    2. 언어 서비스 GUID에 대한 VSPackage의 서비스 공급자를 쿼리하여 언어 서비스를 가져옵니다. 언어 서비스는 파일 확장자별로 레지스트리에서 식별됩니다.

    3. 언어 서비스를 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 호출하여 연결합니다.

2. 이제 VSPackage는 다음과 같이 착색기 오브젝트를 가져오고 사용할 수 있습니다.

    > [!NOTE]
    > 핵심 편집기를 사용하는 VSPackage는 언어 서비스의 colorizer 개체를 명시적으로 가져올 필요가 없습니다. 핵심 편집기의 인스턴스가 적절한 언어 서비스를 얻는 즉시 여기에 표시된 모든 색상 지정 작업을 수행합니다.

    1. 언어 서비스의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>개체에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 메서드를 호출 하여 및 인터페이스를 구현하는 언어 서비스의 colorizer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 개체를 가져옵니다.

    2. 특정 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 텍스트 범위에 대한 색채 정보를 가져오려면 메서드를 호출합니다.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>색을 칠하는 텍스트 범위의 각 문자에 대해 하나씩 값 배열을 반환합니다. 이 값은 코어 편집기에서 유지 관리하는 기본 색상 항목 목록 또는 언어 서비스 자체에서 유지 관리하는 사용자 지정 색상 항목 목록인 색이 가능한 항목 목록으로 인덱싱됩니다.

    3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 메서드에서 반환하는 색상 지정 정보를 사용하여 선택한 텍스트를 표시합니다.

> [!NOTE]
> VSPackage는 언어 서비스 컬러라이저를 사용하는 것 외에도 범용 Visual Studio 텍스트 색칠 메커니즘을 사용할 수도 있습니다. 이 메커니즘에 대한 자세한 내용은 [글꼴 및 색상 사용을](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)참조하십시오.

## <a name="in-this-section"></a>섹션 내용
- [구문 색 지정 구현](../../extensibility/internals/implementing-syntax-coloring.md)

 편집기에서 언어 서비스의 구문 색칠에 액세스하는 방법과 구문 색칠을 지원하기 위해 언어 서비스가 구현해야 하는 내용에 대해 설명합니다.

- [방법: 기본 제공 색 항목 사용](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 언어 서비스에서 기본 제공 색상 항목을 사용하는 방법을 보여 줍니다.

- [사용자 지정 색 항목](../../extensibility/internals/custom-colorable-items.md)

 사용자 지정 색상 항목을 구현하는 방법에 대해 설명합니다.
