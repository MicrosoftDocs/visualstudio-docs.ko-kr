---
title: '방법: Built-In 색 항목 사용 | Microsoft Docs'
description: 언어 서비스에 대해 Visual Studio IDE (통합 개발 환경)에서 기본 제공 색 항목을 사용 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 64738bfe67ccc53970087100cd6c37a9881e6b2a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898320"
---
# <a name="how-to-use-built-in-colorable-items"></a>방법: 기본 제공 색 항목 사용
기본 제공 색 항목을 사용 하기 전에 먼저 사용자 지정 색 항목을 제공 하지 않는 IDE (통합 개발 환경)에 신호를 보내야 합니다 .이 경우에는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 개체입니다. 언어 서비스의 레지스트리 항목을 설정 하 여이 작업을 수행 합니다.

## <a name="to-use-built-in-colorable-items"></a>기본 제공 색 항목을 사용 하려면

1. **HKEY_LOCAL_MACHINE\VisualStudio\\<X-y> \languages\language Services \\<언어 이름 \>** 입니다. 여기서 \<X.Y> 는의 버전 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 이며는 \<Language Name> 언어 이름입니다. 여기서 **RequestStockColors** 라는 DWORD 레지스트리 항목 값을 만듭니다.

2. **RequestStockColors** 레지스트리 항목 값을 *1* 로 설정 합니다.

    레지스트리 항목을 만든 후 svc의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 메서드는 열거형의 멤버를 사용 <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> 하 여 편집기에서 사용할 색 특성의 배열을 채울 수 있습니다.

   > [!NOTE]
   > 사용자 지정 색 항목을 제공 하는 경우에는이 레지스트리 항목을 설정 하지 마십시오. 자세한 내용은 [Custom 색 items 항목](../../extensibility/internals/custom-colorable-items.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [사용자 지정 편집기의 구문 색 지정](../../extensibility/syntax-coloring-in-custom-editors.md)
- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [구문 색 지정 구현](../../extensibility/internals/implementing-syntax-coloring.md)
- [사용자 지정 색 항목](../../extensibility/internals/custom-colorable-items.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service2.md)
