---
title: 레거시 언어 서비스에서 중단점 유효성 검사 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af09e4f8f2156100bea9267c92ffebeb64ce1aa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704090"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>레거시 언어 서비스의 중단점 유효성 검사
중단점은 디버거에서 실행되는 동안 특정 지점에서 프로그램 실행을 중지해야 한다는 것을 나타냅니다. 편집기는 중단점에 대한 유효한 위치를 구성하는 것을 알지 않으므로 사용자는 원본 파일의 모든 줄에 중단점을 배치할 수 있습니다. 디버거가 시작되면 표시된 모든 중단점(보류 중인 중단점이라고 함)이 실행 중인 프로그램의 적절한 위치에 바인딩됩니다. 동시에 중단점은 유효한 코드 위치를 표시하도록 유효성을 검사합니다. 예를 들어 소스 코드에 해당 위치에 코드가 없기 때문에 주석의 중단점은 유효하지 않습니다. 디버거가 잘못된 중단점을 비활성화합니다.

 언어 서비스는 표시되는 소스 코드에 대해 알고 있으므로 디버거가 시작되기 전에 중단점을 확인할 수 있습니다. 중단점에 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 대해 유효한 위치를 지정하는 범위를 반환하는 메서드를 재정의할 수 있습니다. 디버거가 시작될 때 중단점 위치는 여전히 유효성이 검사되지만 디버거가 로드될 때까지 기다리지 않고 잘못된 중단점에 대한 알림을 사용자에게 제공합니다.

## <a name="implementing-support-for-validating-breakpoints"></a>중단점 유효성 검사지원 구현

- 메서드에는 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 중단점의 위치가 지정됩니다. 구현에서는 위치가 유효한지 여부를 결정하고 줄 위치와 연결된 코드를 식별하는 텍스트 범위를 반환하여 이를 나타내야 합니다.

- 위치가 유효한 지 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 또는 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> 유효하지 않은 경우 반환합니다.

- 중단점이 유효한 경우 텍스트 범위는 중단점과 함께 강조 표시됩니다.

- 중단점이 잘못되면 상태 표시줄에 오류 메시지가 나타납니다.

### <a name="example"></a>예제
 이 예제에서는 지정된 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 위치에서 코드 범위(있는 경우)를 얻기 위해 파서를 호출하는 메서드의 구현을 보여 주며 있습니다.

 이 예제에서는 텍스트 범위의 `GetCodeSpan` 유효성을 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 검사하는 메서드를 클래스에 `true` 추가하고 유효한 중단점 위치인 경우 반환하는 메서드를 추가했다고 가정합니다.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

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
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
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

## <a name="see-also"></a>참조
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
