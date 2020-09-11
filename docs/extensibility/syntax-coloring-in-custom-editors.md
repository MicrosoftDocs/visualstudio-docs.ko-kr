---
title: 사용자 지정 편집기의 구문 색 지정 | Microsoft Docs
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
ms.openlocfilehash: e4f6214aa67040a4eb7a4b781cf1612762c87b2e
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012427"
---
# <a name="syntax-coloring-in-custom-editors"></a>사용자 지정 편집기의 구문 색 지정
핵심 편집기를 비롯 한 Visual Studio 환경 SDK 편집기는 언어 서비스를 사용 하 여 특정 구문 항목을 식별 하 고 지정 된 문서 뷰에 대해 지정 된 색으로 표시 합니다.

## <a name="colorization-requirements"></a>색 지정 요구 사항
 언어 서비스의 svc를 구현 하는 모든 편집기는 다음을 수행 해야 합니다.

1. 을 구현 하는 개체를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 색을 지정할 텍스트와 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 텍스트의 문서 보기를 제공 하기 위해를 구현 하는 개체를 관리 합니다.

2. 언어 서비스의 식별 GUID를 사용 하 여 VSPackage의 서비스 공급자를 쿼리하여 특정 언어 서비스에 대 한 인터페이스를 가져옵니다.

3. 을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 구현 하는 개체의 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 합니다. 이 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> VSPackage에서 색을 지정할 텍스트를 관리 하는 데 사용 하는 구현과 언어 서비스를 연결 합니다.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>언어 서비스 Svc의 핵심 편집기 사용
 핵심 편집기 인스턴스에서 svc를 사용 하 여 언어 서비스를 가져오는 경우 언어 서비스의 svc에의 한 텍스트 구문 분석 및 렌더링이 자동으로 발생 하며,이는 파트에 대 한 추가 개입 없이 자동으로 발생 합니다.

 IDE는 투명 하 게 수행 됩니다.

- 는의 구현에서 추가 되거나 수정 될 때 텍스트를 구문 분석 하 고 분석 하는 데 필요에 따라 svc를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 합니다.

- 구현에서 제공 하는 문서 뷰에서 제공 하는 디스플레이가 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 업데이트 되 고 svc에서 반환 된 정보를 사용 하 여 다시 그려집니다.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>언어 서비스 Svc의 비 코어 편집기 사용
 핵심 편집기 인스턴스는 언어 서비스의 구문 색 지정 서비스를 사용할 수도 있지만, 서비스의 svc을 명시적으로 검색 하 고 적용 하 고 문서 뷰 자체를 다시 그려야 합니다.

 이렇게 하려면 코어가 아닌 편집기에서 다음을 수행 해야 합니다.

1. 및를 구현 하는 언어 서비스의 svc 개체를 가져옵니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> . VSPackage는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 언어 서비스의 인터페이스에서 메서드를 호출 하 여이를 수행 합니다.

2. 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 하 여 특정 텍스트 범위에 색이 적용 되도록 요청 합니다.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>메서드는 색이 있는 텍스트 범위의 각 문자에 대 한 값의 배열을 반환 합니다. 또한 주석, 키워드, 데이터 형식 등의 특정 유형의 색 항목으로 텍스트 범위를 식별 합니다.

3. 에서 반환 되는 색 지정 정보를 사용 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 하 여 해당 텍스트를 다시 표시 하 고 표시 합니다.

> [!NOTE]
> 언어 서비스의 svc를 사용 하는 것 외에도 VSPackage는 범용 Visual Studio 환경 SDK 텍스트 색 지정 메커니즘을 사용 하도록 선택할 수 있습니다. 이 메커니즘에 대 한 자세한 내용은 [글꼴 및 색 사용](../vs-2015/extensibility/using-fonts-and-colors.md?view=vs-2015)을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [레거시 언어 서비스의 구문 색 지정](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [구문 색 지정 구현](../extensibility/internals/implementing-syntax-coloring.md)
- [방법: 기본 제공 색 항목 사용](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [사용자 지정 색 항목](../extensibility/internals/custom-colorable-items.md)