---
title: 레거시 언어 서비스의 자동 창 지원 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 01d2046d7693b23865555abb06962dead4a435ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157590"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>레거시 언어 서비스의 자동 창 지원
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**자동** 창에는 디버그 중인 프로그램이 일시 중지 될 때 (중단점 또는 예외로 인해) 범위 내에 있는 변수 및 매개 변수와 같은 식이 표시 됩니다. 식에는 로컬 범위에서 변경 된 변수, 지역 또는 전역 및 매개 변수가 포함 될 수 있습니다. **자동** 창에는 클래스, 구조체 또는 일부 다른 형식의 인스턴스화가 포함 될 수도 있습니다. 식 계산기에서 평가할 수 있는 모든 항목은 **자동** 창에 표시 될 수 있습니다.  
  
 MPF (관리 되는 패키지 프레임 워크)는 **자동** 창을 직접 지원 하지 않습니다. 그러나 메서드를 재정의 하는 경우 <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> **자동** 창에 표시 될 식의 목록을 반환할 수 있습니다.  
  
## <a name="implementing-support-for-the-autos-window"></a>자동 창에 대 한 지원 구현  
 **자동** 창을 지원 하기 위해 필요한 모든 작업은 <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> 클래스에서 메서드를 구현 하는 것입니다 <xref:Microsoft.VisualStudio.Package.LanguageService> . 소스 파일의 위치를 지정 하 여 구현에서 **자동** 창에 표시 되어야 하는 식을 결정 해야 합니다. 메서드는 각 문자열이 단일 식을 나타내는 문자열 목록을 반환 합니다. 반환 값은 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 목록에 식이 포함 되어 있음을 나타내고,는 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> 표시할 식이 없음을 나타냅니다.  
  
 반환 되는 실제 식은 코드에서 해당 위치에 표시 되는 변수 또는 매개 변수의 이름입니다. 이러한 이름은 식 계산기에 전달 되어 **자동** 창에 표시 되는 값과 형식을 가져옵니다.  
  
### <a name="example"></a>예  
 다음 예제에서는 <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 구문 분석 이유를 사용 하 여 메서드에서 식의 목록을 가져오는 메서드의 구현을 보여 줍니다 <xref:Microsoft.VisualStudio.Package.ParseReason> . 각 식은 `TestVsEnumBSTR` 인터페이스를 구현 하는로 래핑됩니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> .  
  
 `GetAutoExpressionsCount`및 `GetAutoExpression` 메서드는 개체에 대 한 사용자 지정 메서드가 며 `TestAuthoringSink` 이 예제를 지원 하기 위해 추가 되었습니다. 파서 `TestAuthoringSink` 외부에서 메서드를 호출 하 여 개체에 추가 된 식에 액세스할 수 있는 한 가지 방법을 나타냅니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> .  
  
```csharp  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```
