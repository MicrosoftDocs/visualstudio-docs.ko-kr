---
title: '방법: 내장 컬러 아이템 사용 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34e07894c3306f544396e53001990f7b9a2df5a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707782"
---
# <a name="how-to-use-built-in-colorable-items"></a>방법: 내장 된 색 항목을 사용 하 여
기본 제공 색상 항목을 사용하기 전에 먼저 통합 개발 환경(IDE)에 사용자 지정 색상 항목을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 제공하지 않는다는 신호를 보내야 합니다. 언어 서비스에 대한 레지스트리 항목을 설정하여 이 작업을 수행합니다.

## <a name="to-use-built-in-colorable-items"></a>내장 컬러 아이템을 사용하려면

1. **\\ HKEY_LOCAL_MACHINE\VisualStudio<X.Y>\Languages\Language 서비스\><언어 이름,\\ ** \<여기서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] X.Y> 버전이고 \<언어 이름> 언어 이름은 **RequestStockColors**라는 DWORD 레지스트리 항목 값을 만듭니다.

2. **RequestStockColors** 레지스트리 입력 값을 *1로*설정합니다.

    레지스트리 항목을 만든 후 colorizer의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 메서드는 열거형의 <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> 멤버를 사용하여 편집기에서 사용할 색상 특성 배열을 채울 수 있습니다.

   > [!NOTE]
   > 사용자 지정 색상 항목을 제공하는 경우 이 레지스트리 항목을 설정하지 마십시오. 자세한 내용은 [사용자 지정 색상 항목을](../../extensibility/internals/custom-colorable-items.md)참조하십시오.

## <a name="see-also"></a>참조
- [사용자 지정 편집기의 구문 색칠](../../extensibility/syntax-coloring-in-custom-editors.md)
- [레거시 언어 서비스의 구문 색칠](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [구문 색칠 구현](../../extensibility/internals/implementing-syntax-coloring.md)
- [사용자 정의 색상 항목](../../extensibility/internals/custom-colorable-items.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service2.md)
