---
title: 레거시 언어 서비스 개요 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be485a0e7406d49c4dcce77958c720e0b62504b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706805"
---
# <a name="outlining-in-a-legacy-language-service"></a>레거시 언어 서비스의 개요 표시
개요를 사용하면 복잡한 프로그램을 개요 또는 개요로 축소할 수 있습니다. 예를 들어 C#에서 모든 메서드는 메서드 시그니처만 표시하면서 한 줄로 축소할 수 있습니다. 또한 구조체와 클래스의 이름만 표시하도록 축소할 수 있습니다. 단일 메서드 내에서 복잡한 논리를 축소하여 `foreach`". `if`및. `while`

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 자세한 내용은 [연습: 개요](../../extensibility/walkthrough-outlining.md)를 참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

## <a name="enabling-support-for-outlining"></a>개요에 대한 지원 활성화
 `AutoOutlining` 레지스트리 항목은 자동 개요를 활성화하기 위해 1로 설정됩니다. 자동 개요는 숨겨진 영역을 식별하고 개요 글리프를 표시하기 위해 파일을 로드하거나 변경할 때 전체 소스의 구문 분석구를 설정합니다. 개요는 사용자가 수동으로 제어할 수도 있습니다.

 `AutoOutlining` 레지스트리 항목의 값은 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 클래스의 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> 속성을 통해 얻을 수 있습니다. `AutoOutlining` 레지스트리 항목은 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 특성에 대한 명명된 매개 변수로 초기화할 수 있습니다(자세한 내용은 레거시 언어 서비스 [등록](../../extensibility/internals/registering-a-legacy-language-service1.md) 참조).

## <a name="the-hidden-region"></a>숨겨진 지역
 개요를 제공하려면 언어 서비스가 숨겨진 영역을 지원해야 합니다. 확장하거나 축소할 수 있는 텍스트 범위입니다. 숨겨진 영역은 곱슬 대괄호와 같은 표준 언어 기호 또는 사용자 지정 기호로 구분할 수 있습니다. 예를 들어 C#에는 `#region` / `#endregion` 숨겨진 영역을 구분하는 쌍이 있습니다.

 숨겨진 영역은 인터페이스로 노출되는 숨겨진 지역 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 관리자에 의해 관리됩니다.

 개요는 인터페이스의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> 숨겨진 영역을 사용하고 숨겨진 영역의 범위, 현재 표시되는 상태 및 범위가 축소될 때 표시할 배너를 포함합니다.

 언어 서비스 파서는 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 메서드를 사용하여 숨겨진 영역에 대한 기본 동작이 있는 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 새 숨겨진 영역을 추가하는 반면 메서드를 사용하면 윤곽선의 모양과 동작을 사용자 지정할 수 있습니다. 숨겨진 영역이 숨겨진 영역 세션에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 지정되면 언어 서비스의 숨겨진 영역을 관리합니다.

 숨겨진 영역 세션이 소멸되는 시기를 결정해야 하는 경우 숨겨진 영역이 변경되거나 특정 숨겨진 영역이 표시되는지 확인해야 합니다. 클래스에서 클래스를 파생 하 고 적절 한 <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>메서드를 <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>재정의 해야 합니다. <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source>

### <a name="example"></a>예제
 다음은 모든 중괄호 쌍에 대해 숨겨진 영역을 만드는 간단한 예입니다. 언어가 중괄호 일치를 제공하고 일치할 중괄호에는 적어도 중괄호({및 })가 포함된다는 가정이 있습니다. 이 방법은 설명용입니다. 전체 구현에서는 에서 서비스 케이스를 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>완벽하게 처리할 수 있습니다. 이 예제에서는 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> 기본 설정을 `true` 일시적으로 설정하는 방법도 보여 주어 도 있습니다. 다른 방법은 언어 `AutoOutlining` 패키지의 특성에 명명된 매개 변수를 `ProvideLanguageServiceAttribute` 지정하는 것입니다.

 이 예제에서는 주석, 문자열 및 리터럴에 대한 C# 규칙을 가정합니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>참조
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
