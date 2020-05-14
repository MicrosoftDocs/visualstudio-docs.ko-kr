---
title: 레거시 언어 서비스의 자동 창 지원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75f8c761721dde5dad4bb75b8675f71f678b06df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704890"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>레거시 언어 서비스의 자동 창 지원
**Autos** 창에는 디버깅 중인 프로그램이 일시 중지될 때(중단점 또는 예외로 인해) 범위에 있는 변수 및 매개 변수와 같은 식이 표시됩니다. 식에는 변수, 로컬 또는 전역 및 로컬 범위에서 변경된 매개 변수가 포함될 수 있습니다. **자동** 창에는 클래스, 구조체 또는 다른 형식의 인스턴스화도 포함될 수 있습니다. 식 평가자가 평가할 수 있는 모든 것은 자동 **창에** 잠재적으로 표시될 수 있습니다.

 MPF(관리되는 패키지 프레임워크)는 **자동** 창에 대한 직접 지원을 제공하지 않습니다. 그러나 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> 재정의하는 경우 **Autos** 창에 표시할 식 목록을 반환할 수 있습니다.

## <a name="implementing-support-for-the-autos-window"></a>자동 창에 대한 지원 구현
 **자동** 창을 지원하기 위해 수행해야 하는 것은 <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스에서 메서드를 구현하는 것입니다. 구현은 소스 파일의 위치가 주어지면 **Autos** 창에 표시되어야 하는 식을 결정해야 합니다. 메서드는 각 문자열이 단일 식을 나타내는 문자열 목록을 반환합니다. return 값은 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 목록에 식이 포함되어 있음을 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> 나타내고 표시할 식이 없음을 나타냅니다.

 반환되는 실제 표현식은 코드의 해당 위치에 나타나는 변수 또는 매개 변수의 이름입니다. 이러한 이름은 자동 **창에** 표시되는 값과 형식을 얻기 위해 식 계산기로 전달됩니다.

### <a name="example"></a>예제
 다음 예제에서는 구문 <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> 분석 이유를 <xref:Microsoft.VisualStudio.Package.ParseReason>사용 하 여 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드에서 식 목록을 가져옵니다 메서드의 구현을 보여 합니다. 각 식은 `TestVsEnumBSTR` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> 인터페이스를 구현하는 것으로 래핑됩니다.

 `GetAutoExpressionsCount` 및 `GetAutoExpression` 메서드는 개체의 `TestAuthoringSink` 사용자 지정 메서드이며 이 예제를 지원하기 위해 추가되었습니다. 이러한 표현식은 `TestAuthoringSink` <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> 파서(메서드를 호출하여)에 의해 개체에 추가된 식에 파서 외부에서 액세스할 수 있는 한 가지 방법을 나타냅니다.

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
