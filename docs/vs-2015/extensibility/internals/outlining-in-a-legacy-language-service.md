---
title: 레거시 언어 서비스 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6096f89a36cdd47d2dec68af5801a94dc77acb43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841702"
---
# <a name="outlining-in-a-legacy-language-service"></a>레거시 언어 서비스의 개요 표시
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

개요를 사용 하면 복잡 한 프로그램을 개요 또는 개요로 축소할 수 있습니다. 예를 들어 c #에서는 메서드 서명만 표시 하는 모든 메서드를 한 줄로 축소할 수 있습니다. 또한 구조체와 클래스는 구조체 및 클래스의 이름만 표시 하도록 축소할 수 있습니다. 단일 메서드 내에서 복잡 한 논리를 축소 하 여, 및와 같은 문의 첫 번째 줄만 표시 함으로써 전체 흐름을 표시할 수 있습니다 `foreach` `if` `while` .  
  
 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 자세히 알아보려면 [연습: 개요](../../extensibility/walkthrough-outlining.md)를 참조 하세요.  
  
> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.  
  
## <a name="enabling-support-for-outlining"></a>개요 지원 사용  
 `AutoOutlining`자동 개요를 사용 하려면 레지스트리 항목을 1로 설정 합니다. 자동 개요는 숨겨진 영역을 식별 하 고 개요 문자 모양을 표시 하기 위해 파일이 로드 되거나 변경 될 때 전체 원본의 구문 분석을 설정 합니다. 사용자가 개요를 수동으로 제어할 수도 있습니다.  
  
 레지스트리 항목의 값은 `AutoOutlining` 클래스의 속성을 통해 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . `AutoOutlining`특성에 대 한 명명 된 매개 변수를 사용 하 여 레지스트리 항목을 초기화할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . 자세한 내용은 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md) 을 참조 하세요.  
  
## <a name="the-hidden-region"></a>숨겨진 영역  
 개요를 제공 하기 위해 언어 서비스는 숨겨진 영역을 지원 해야 합니다. 확장 하거나 축소할 수 있는 텍스트의 범위입니다. 숨겨진 지역은 중괄호와 같은 표준 언어 기호나 사용자 지정 기호로 구분 될 수 있습니다. 예를 들어 c #에는 `#region` / `#endregion` 숨겨진 영역을 구분 하는 쌍이 있습니다.  
  
 숨겨진 지역은 인터페이스로 노출 되는 숨겨진 지역 관리자에 의해 관리 됩니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> .  
  
 개요는 숨겨진 영역을 인터페이스에 사용 하 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> 고 숨겨진 영역, 현재 표시 되는 상태 및 범위가 축소 될 때 표시 되는 배너의 범위를 포함 합니다.  
  
 언어 서비스 파서는 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 숨겨진 영역에 대 한 기본 동작을 사용 하 여 새 숨겨진 영역을 추가 하 고, 메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 윤곽선의 모양과 동작을 사용자 지정할 수 있도록 합니다. 숨겨진 지역이 숨겨진 지역 세션에 제공 되 면는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 언어 서비스의 숨겨진 영역을 관리 합니다.  
  
 숨겨진 지역 세션이 제거 된 시기를 확인 해야 하는 경우 숨겨진 지역이 변경 되거나 특정 숨겨진 지역이 표시 되는지 확인 해야 합니다. 클래스에서 클래스를 파생 <xref:Microsoft.VisualStudio.Package.Source> 하 고 각각 적절 한,, 및 메서드를 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> .  
  
### <a name="example"></a>예제  
 다음은 중괄호의 모든 쌍에 대해 숨겨진 영역을 만드는 간단한 예제입니다. 언어가 중괄호 일치를 제공 하 고, 일치 하는 중괄호에 중괄호 ({및})가 하나 이상 포함 되어 있다고 가정 합니다. 이 방법은 설명을 위한 목적 으로만 사용 됩니다. 전체 구현에서는의 사례를 완전히 처리 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 합니다. 또한이 예제에서는 기본 설정을 일시적으로 설정 하는 방법을 보여 줍니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> `true` . 다른 방법은 `AutoOutlining` `ProvideLanguageServiceAttribute` 언어 패키지의 특성에 명명 된 매개 변수를 지정 하는 것입니다.  
  
 이 예에서는 주석, 문자열 및 리터럴에 대 한 c # 규칙을 가정 합니다.  
  
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
  
## <a name="see-also"></a>참고 항목  
 [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)   
 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
