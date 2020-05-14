---
title: 사용자 정의 색 항목 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: feecd9e8f8178045f66999b775e2d0792f50b288
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708991"
---
# <a name="custom-colorable-items"></a>사용자 정의 색상 항목
언어 서비스의 일부로 사용자 지정 색상 항목을 구현하여 키워드 및 주석과 같은 색지정 유형 목록을 재정의할 수 있습니다.

## <a name="user-settings-of-colorable-items"></a>색상 항목의 사용자 설정
 **도구** 메뉴에서 **옵션을** 선택한 다음 **환경**아래의 글꼴 및 색상을 선택하여 **글꼴 및 색상** 대화 상자를 표시할 수 **있습니다.** **텍스트 편집기** 또는 **명령 창과**같은 디스플레이를 선택하면 **항목 목록** 상자에 해당 표시에 대한 모든 색상 항목이 표시됩니다. 각 색상 항목에 대한 글꼴, 크기, 전경 색상 및 배경 색을 보고 변경할 수 있습니다. 선택 항목은 레지스트리의 캐시에 저장되고 색상 항목 이름으로 액세스됩니다.

## <a name="presentation-of-colorable-items"></a>컬러 아이템 의 프리젠 테이션
 IDE는 **글꼴 및 색상** 대화 상자에서 색상 항목의 사용자 재정의를 처리하므로 각 사용자 지정 색상 항목만 이름으로 제공하면 됩니다. 이 이름은 **항목 표시** 목록에 표시됩니다. 색상 항목은 알파벳 순서로 표시됩니다. 언어 서비스의 사용자 지정 색상 항목을 그룹화하려면 언어 이름(예: **NewLanguage - 주석** 및 **newLanguage - 키워드)으로**각 이름을 시작할 수 있습니다.

> [!CAUTION]
> 기존 색상 항목 이름과의 충돌을 방지하려면 색상 항목 이름에 언어 이름을 포함해야 합니다. 개발 중에 색상 항목 중 하나의 이름을 변경하는 경우 색상 항목이 처음 액세스되었을 때 생성된 캐시를 다시 설정해야 합니다. 일반적으로 디렉터리에서 Visual Studio SDK와 함께 설치된 **CreateExpInstance** 도구를 사용하여 실험 캐시를 재설정할 수 있습니다.
>
> *C:\프로그램 파일 (x86)\마이크로소프트 비주얼 스튜디오 14.0\VSSDK\비주얼 스튜디오 통합\도구\빈*
>
> 캐시를 재설정하려면 **CreateExpInstance /재설정**을 입력합니다. **CreateExpInstance에**대한 자세한 내용은 [CreateExpInstance 유틸리티를](../../extensibility/internals/createexpinstance-utility.md)참조하십시오.

 색상 항목 목록의 첫 번째 항목은 참조되지 않습니다. 첫 번째 항목은 0의 색상 항목 인덱스에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 해당하며 해당 항목의 기본 텍스트 색상 및 속성을 항상 제공합니다. 이 참조되지 않은 항목을 처리하는 가장 쉬운 방법은 목록에서 자리 표시자 색 항목을 첫 번째 항목으로 제공하는 것입니다.

## <a name="implement-custom-colorable-items"></a>사용자 지정 색상 항목 구현

1. 키워드, 연산자 및 식별자와 같은 언어에 색상을 입력해야 하는 내용을 정의합니다.

2. 이러한 색상 항목의 열거를 만듭니다.

3. 파서 또는 스캐너에서 반환된 토큰 형식을 수온값과 연결합니다.

    예를 들어 토큰 형식을 나타내는 값은 사용자 지정 색상 항목 열거형의 동일한 값일 수 있습니다.

4. 개체에서 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 구현할 때 특성 목록을 사용자 지정 색상 항목 열거형의 값으로 채우면 파서 또는 스캐너에서 반환된 토큰 유형에 해당합니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>

5. 인터페이스를 구현하는 동일한 클래스에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 인터페이스와 두 가지 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>구현하고 . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

6. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 인터페이스를 구현합니다.

7. 24비트 또는 높은 색상 값을 지원하려면 인터페이스도 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 구현합니다.

8. 언어 서비스 개체에서 파서 또는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 스캐너가 식별할 수 있는 각 색 항목에 대해 개체가 포함된 목록을 만듭니다.

    사용자 지정 색상 항목 열거형의 해당 값을 사용하여 목록의 각 항목에 액세스할 수 있습니다. 열거형 값을 목록에 인덱스로 사용합니다. 목록의 첫 번째 항목은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 항상 자신을 처리하는 기본 텍스트 스타일에 해당하므로 액세스되지 않습니다. 목록의 시작 부분에 자리 표시자 색상 항목을 삽입하여 이를 보정할 수 있습니다.

9. 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 구현할 때 사용자 지정 색상 항목 목록의 항목 수를 반환합니다.

10. 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 구현할 때 목록에서 요청된 색상 항목을 반환합니다.

    및 인터페이스를 구현하는 방법에 대한 예는 을 참조하십시오. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>

## <a name="see-also"></a>참조
- [레거시 언어 서비스 모델](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [사용자 지정 편집기의 구문 색칠](../../extensibility/syntax-coloring-in-custom-editors.md)
- [레거시 언어 서비스의 구문 색칠](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [구문 색칠 구현](../../extensibility/internals/implementing-syntax-coloring.md)
- [방법: 내장 된 색 항목을 사용 하 여](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
