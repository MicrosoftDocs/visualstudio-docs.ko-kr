---
title: 레거시 언어 서비스의 구문 색 지정 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704753"
---
# <a name="syntax-coloring-in-a-legacy-language-service"></a>레거시 언어 서비스의 구문 색 지정

Visual Studio에서는 색 지정 서비스를 사용 하 여 언어 요소를 식별 하 고 편집기에 지정 된 색으로 표시 합니다.

## <a name="colorizer-model"></a>Svc 모델
 언어 서비스는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 인터페이스를 구현 하며,이는 편집기에서 사용 됩니다. 이 구현은 다음 그림과 같이 언어 서비스와는 별개의 개체입니다.

 ![SVC 색 지정기 그래픽](../../extensibility/internals/media/figlgsvccolorizer.gif)

> [!NOTE]
> 구문 색 지정 서비스는 텍스트 색 지정을 위한 일반 Visual Studio 메커니즘과는 별개입니다. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]색상화를 지 원하는 일반 메커니즘에 대 한 자세한 내용은 [글꼴 및 색 사용](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)을 참조 하세요.

 Svc 외에도 언어 서비스는 사용자 지정 색 항목을 제공 한다는 것을 광고 하 여 편집기에서 사용 하는 사용자 지정 색 항목을 제공할 수 있습니다. 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 구현 하는 동일한 개체에 인터페이스를 구현 하 여이 작업을 수행할 수 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> . 편집기에서 메서드를 호출할 때 사용자 지정 색 항목의 수를 반환 하 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 고, 편집기에서 메서드를 호출할 때 개별 사용자 지정 색 항목을 반환 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>메서드는 인터페이스를 구현 하는 개체를 반환 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> . 언어 서비스가 24 비트 또는 높은 색 값을 지 원하는 경우 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 인터페이스와 같은 개체에 구현 해야 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> .

## <a name="how-a-vspackage-uses-a-language-service-colorizer"></a>VSPackage에서 언어 서비스 Svc를 사용 하는 방법

1. VSPackage는 다음을 수행 하기 위해 언어 서비스 VSPackage가 필요한 적절 한 언어 서비스를 가져와야 합니다.

    1. 인터페이스를 구현 하는 개체를 사용 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 하 여 색을 지정할 텍스트를 가져옵니다.

         일반적으로 텍스트는 인터페이스를 구현 하는 개체를 사용 하 여 표시 됩니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .

    2. 언어 서비스 GUID에 대 한 VSPackage의 서비스 공급자를 쿼리하여 언어 서비스를 가져옵니다. 언어 서비스는 레지스트리에서 파일 확장명으로 식별 됩니다.

    3. 메서드를 호출 하 여 언어 서비스를에 연결 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> .

2. 이제 VSPackage는 다음과 같이 svc 개체를 가져오고 사용할 수 있습니다.

    > [!NOTE]
    > 핵심 편집기를 사용 하는 Vspackage는 언어 서비스의 svc 개체를 명시적으로 가져올 필요가 없습니다. 핵심 편집기의 인스턴스가 적절 한 언어 서비스를 가져오는 즉시 여기에 표시 되는 모든 색 지정 작업을 수행 합니다.

    1. 언어 서비스의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> 개체에서 메서드를 호출 하 여, 및 인터페이스를 구현 하는 언어 서비스의 svc 개체를 가져옵니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> .

    2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>특정 텍스트 범위에 대 한 svc 정보를 가져오려면 메서드를 호출 합니다.

         <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 색이 있는 텍스트 범위의 각 문자 마다 하나씩 값의 배열을 반환 합니다. 값은 핵심 편집기에서 유지 관리 되는 기본 색 항목 목록 또는 language service 자체에서 유지 관리 되는 사용자 지정 색 항목 목록에 해당 하는 색 항목 목록으로의 인덱스입니다.

    3. 메서드에서 반환 되는 색 지정 정보를 사용 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 하 여 선택한 텍스트를 표시 합니다.

> [!NOTE]
> 언어 서비스 svc를 사용 하는 것 외에도 VSPackage는 범용 Visual Studio 텍스트 색 지정 메커니즘을 사용할 수 있습니다. 이 메커니즘에 대 한 자세한 내용은 [글꼴 및 색 사용](/visualstudio/extensibility/using-fonts-and-colors?view=vs-2015)을 참조 하세요.

## <a name="in-this-section"></a>섹션 내용
- [구문 색 지정 구현](../../extensibility/internals/implementing-syntax-coloring.md)

 편집기에서 언어 서비스의 구문 색 지정 및 구문 색 지정을 지원 하기 위해 구현 해야 하는 언어에 대해 설명 합니다.

- [방법: 기본 제공 색 항목 사용](../../extensibility/internals/how-to-use-built-in-colorable-items.md)

 언어 서비스에서 기본 제공 색 항목을 사용 하는 방법을 보여 줍니다.

- [사용자 지정 색 항목](../../extensibility/internals/custom-colorable-items.md)

 사용자 지정 색 항목을 구현 하는 방법을 설명 합니다.
