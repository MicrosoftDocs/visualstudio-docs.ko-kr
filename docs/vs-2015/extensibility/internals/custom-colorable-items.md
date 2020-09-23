---
title: 사용자 지정 색 항목 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 24a4db907ec859c6075c06956f86939047379897
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "91102537"
---
# <a name="custom-colorable-items"></a>사용자 지정 색 항목
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

언어 서비스의 일부로 사용자 지정 색 항목을 구현 하 여 키워드 및 주석과 같은 색 지정을 위한 형식 목록을 재정의할 수 있습니다.  
  
## <a name="user-settings-of-colorable-items"></a>색 Items의 사용자 설정  
 **도구** 메뉴에서 **옵션** 을 선택 하 고 **환경**아래에서 **글꼴 및 색** 을 선택 하 여 **글꼴 및 색** 대화 상자를 표시할 수 있습니다. **텍스트 편집기나** **명령 창과**같은 디스플레이를 선택 하면 표시 **항목** 목록 상자에 해당 디스플레이에 대 한 모든 색 항목이 표시 됩니다. 각 색 항목에 대 한 글꼴, 크기, 전경색 및 배경색을 보고 변경할 수 있습니다. 선택 항목은 레지스트리의 캐시에 저장 되 고 색 항목 이름으로 액세스 됩니다.  
  
## <a name="presentation-of-colorable-items"></a>색 항목 프레젠테이션  
 IDE는 **글꼴 및 색** 대화 상자에서 색 항목의 사용자 재정의를 처리 하기 때문에 각 사용자 지정 색 항목만 이름을 지정 해야 합니다. 이 이름은 **표시 항목** 목록에 표시 됩니다. 색 항목은 사전순으로 표시 됩니다. 언어 서비스의 사용자 지정 색 항목을 그룹화 하기 위해 각 이름을 언어 이름으로 시작할 수 있습니다 (예: **Newlanguage-Comment** 및 **Newlanguage-키워드)**.  
  
> [!CAUTION]
> 기존 색 항목 이름과의 충돌을 방지 하려면 색 항목 이름에 언어 이름을 포함 해야 합니다. 개발 하는 동안 색 항목 중 하나의 이름을 변경 하는 경우 색 항목에 처음 액세스할 때 생성 된 캐시를 다시 설정 해야 합니다. 일반적으로 디렉터리에 Visual Studio SDK와 함께 설치 되는 CreateExpInstance 도구를 사용 하 여 실험적 캐시를 다시 설정할 수 있습니다.  
>   
> **C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ VSSDK\VisualStudioIntegration\Tools\Bin**  
>   
> 캐시를 다시 설정 하려면를 호출 `CreateExpInstance /Reset` 합니다. CreateExpInstance에 대 한 자세한 내용은 [Createexpinstance 유틸리티](../../extensibility/internals/createexpinstance-utility.md)를 참조 하세요.  
  
 색 항목 목록의 첫 번째 항목은 참조 되지 않습니다. 첫 번째 항목은 색 항목 인덱스 0에 해당 하며 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 항상 해당 항목에 대 한 기본 텍스트 색과 특성을 제공 합니다. 참조 되지 않은이 항목을 처리 하는 가장 쉬운 방법은 목록에서 자리 표시자 색 항목을 첫 번째 항목으로 제공 하는 것입니다.  
  
## <a name="implementing-custom-colorable-items"></a>사용자 지정 색 항목 구현  
  
1. 키워드, 연산자 및 식별자와 같은 언어로 색을 지정 해야 하는 항목을 정의 합니다.  
  
2. 이러한 색 항목의 열거형을 만듭니다.  
  
3. 파서 또는 스캐너에서 반환 된 토큰 형식을 열거 된 값과 연결 합니다.  
  
    예를 들어, 토큰 형식을 나타내는 값은 custom 색 items 열거의 동일한 값이 될 수 있습니다.  
  
4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>개체의 메서드 구현에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 특성 목록을 파서 또는 스캐너에서 반환 된 토큰 형식에 해당 하는 사용자 지정 색 items 열거형의 값으로 채웁니다.  
  
5. 인터페이스를 구현 하는 동일한 클래스에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 인터페이스와 두 메서드 (및)를 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> .  
  
6. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 인터페이스를 구현합니다.  
  
7. 24 비트 또는 높은 색의 값을 지원 하려면 인터페이스도 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 합니다.  
  
8. 언어 서비스 개체에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 파서가 나 스캐너가 식별할 수 있는 각 색 항목에 대 한 개체를 포함 하는 목록을 만듭니다.  
  
    사용자 지정 색 items 열거의 해당 값을 사용 하 여 목록의 각 항목에 액세스할 수 있습니다. 열거 값을 목록에 인덱스로 사용 합니다. 목록의 첫 번째 항목은 항상 자체적으로 처리 하는 기본 텍스트 스타일에 해당 하므로 액세스 되지 않습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 목록의 시작 부분에 자리 표시자 색 항목을 삽입 하 여이를 보정할 수 있습니다.  
  
9. 메서드 구현에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 사용자 지정 색 항목 목록의 항목 수를 반환 합니다.  
  
10. 메서드의 구현에서 요청 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 색 항목을 목록에서 반환 합니다.  
  
    및 인터페이스를 구현 하는 방법에 대 한 예제는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 를 참조 하십시오 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> .  
  
## <a name="see-also"></a>참고 항목  
 [레거시 언어 서비스의 모델](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [사용자 지정 편집기의 구문 색 지정](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [구문 색 지정 구현](../../extensibility/internals/implementing-syntax-coloring.md)   
 [방법: 기본 제공 색 항목 사용](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
