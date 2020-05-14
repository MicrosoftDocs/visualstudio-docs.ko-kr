---
title: 레거시 언어 서비스 파서 및 스캐너 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c87f447a4b8bca804d27aae4967f4adaf389c627
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707323"
---
# <a name="legacy-language-service-parser-and-scanner"></a>레거시 언어 서비스 파서 및 검사기
파서는 언어 서비스의 핵심입니다. MPF(관리되는 패키지 프레임워크) 언어 클래스에는 표시되는 코드에 대한 정보를 선택하는 언어 파서가 필요합니다. 파서는 텍스트를 어휘 토큰으로 구분한 다음 유형 및 기능별로 해당 토큰을 식별합니다.

## <a name="discussion"></a>토론
 다음은 C# 메서드입니다.

```csharp
namespace MyNamespace
{
    class MyClass
    {
        public void MyFunction(int arg1)
        {
            int var1 = arg1;
        }
    }
}
```

 이 예제에서 토큰은 단어와 문장 부호입니다. 토큰의 종류는 다음과 같습니다.

|토큰 이름|토큰 형식|
|----------------|----------------|
|네임 스페이스, 클래스, 공공, 무효, int|키워드(keyword)|
|=|operator|
|{ } ( ) ;|구분 기호|
|마이네임스페이스, 마이클래스, 마이기능, arg1, var1|identifier|
|마이네임스페이스|namespace|
|MyClass|class|
|마이 기능|method|
|arg1|매개 변수(parameter)|
|var1|지역 변수(local variable)|

 파서의 역할은 토큰을 식별하는 것입니다. 일부 토큰에는 두 개 이상의 형식이 있을 수 있습니다. 파서가 토큰을 식별한 후 언어 서비스는 이 정보를 사용하여 구문 강조 표시, 중괄호 일치 및 IntelliSense 작업과 같은 유용한 기능을 제공할 수 있습니다.

## <a name="types-of-parsers"></a>파서의 종류
 언어 서비스 파서는 컴파일러의 일부로 사용되는 파서와 다다닙스입니다. 그러나 이러한 종류의 파서는 컴파일러 파서와 동일한 방식으로 스캐너와 파서를 모두 사용해야 합니다.

- 스캐너는 토큰 유형을 식별하는 데 사용됩니다. 이 정보는 구문 강조에 사용되며 중괄호 일치 등의 다른 작업을 트리거할 수 있는 토큰 유형을 신속하게 식별하는 데 사용됩니다. 이 스캐너는 <xref:Microsoft.VisualStudio.Package.IScanner> 인터페이스로 표시됩니다.

- 파서는 토큰의 기능과 범위를 설명하는 데 사용됩니다. 이 정보는 IntelliSense 작업에서 메서드, 변수, 매개 변수 및 선언과 같은 언어 요소를 식별하고 컨텍스트에 따라 멤버 및 메서드 서명 목록을 제공하는 데 사용됩니다. 이 파서는 중괄호 및 괄호와 같은 일치하는 언어 요소 쌍을 찾는 데도 사용됩니다. 이 파서는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스의 메서드를 통해 액세스됩니다.

  언어 서비스에 대한 스캐너 및 파서를 구현하는 방법은 사용자의 책임이 있습니다. 구문 분석자의 작동 방식과 사용자 고유의 파서 작성 방법을 설명하는 몇 가지 리소스를 사용할 수 있습니다. 또한 파서를 만드는 데 도움이되는 여러 무료 및 상용 제품을 사용할 수 있습니다.

### <a name="the-parsesource-parser"></a>파세 소스 파서
 컴파일러의 일부로 사용되는 파서(토큰이 실행 코드의 일종으로 변환되는 경우)와 달리 언어 서비스 파서는 여러 가지 이유와 다양한 컨텍스트에서 호출될 수 있습니다. <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스의 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드에서 이 방법을 구현하는 방법은 해당됩니다. 백그라운드 스레드에서 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 호출할 수 있습니다.

> [!CAUTION]
> 구조에 <xref:Microsoft.VisualStudio.Package.ParseRequest> 개체에 대한 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 참조가 포함되어 있습니다. 이 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 개체는 백그라운드 스레드에서 사용할 수 없습니다. 실제로 대부분의 기본 MPF 클래스는 백그라운드 스레드에서 사용할 수 없습니다. 여기에는 <xref:Microsoft.VisualStudio.Package.Source>에 <xref:Microsoft.VisualStudio.Package.ViewFilter> <xref:Microsoft.VisualStudio.Package.CodeWindowManager> 대해 , 클래스 및 뷰와 직접 또는 간접적으로 통신하는 다른 클래스가 포함됩니다.

 이 구문 분석기는 일반적으로 전체 소스 파일이 처음 호출될 때 또는 <xref:Microsoft.VisualStudio.Package.ParseReason> 구문 분석 이유 값이 부여될 때 구문 분석합니다. 메서드에 대한 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 후속 호출은 구문 분석된 코드의 작은 부분을 처리하며 이전 전체 구문 분석 작업의 결과를 사용하여 훨씬 더 빠르게 실행할 수 있습니다. 메서드는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> 및 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체를 통해 구문 분석 작업의 결과를 전달합니다. 개체는 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 특정 구문 분석 이유에 대 한 정보를 수집 하는 데 사용 됩니다., 예를 들어 일치 하는 중괄호 또는 매개 변수 목록이 메서드 서명의 범위에 대 한 정보. 는 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 선언 및 메서드 서명의 컬렉션을 제공 하 고 또한 고급 편집 옵션에 대 한 지원 **(정의로 이동,** **선언으로 이동,** **참조로 이동).**

### <a name="the-iscanner-scanner"></a>I스캐너 스캐너
 또한 을 구현하는 스캐너를 <xref:Microsoft.VisualStudio.Package.IScanner>구현해야 합니다. 그러나 이 스캐너는 <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스를 통해 라인단위로 작동하므로 일반적으로 구현하는 것이 더 쉽습니다. 각 줄의 시작 부분에서 MPF는 <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스에 스캐너에 전달되는 상태 변수로 사용할 값을 제공합니다. 각 줄의 끝에서 스캐너는 업데이트된 상태 변수를 반환합니다. MPF는 각 줄에 대해 이 상태 정보를 캐시하므로 스캐너는 원본 파일의 시작 부분에서 시작하지 않고도 모든 라인에서 구문 분석작업을 시작할 수 있습니다. 한 줄의 빠른 스캔을 통해 편집기는 사용자에게 빠른 피드백을 제공할 수 있습니다.

## <a name="parsing-for-matching-braces"></a>일치하는 중괄호에 대한 구문 분석
 이 예제에서는 사용자가 입력한 닫는 중괄호를 일치시키는 컨트롤 흐름을 보여 주며 있습니다. 이 과정에서 색지정에 사용되는 스캐너는 토큰 의 유형과 토큰이 일치 중괄호 작업을 트리거할 수 있는지 여부를 결정하는 데도 사용됩니다. 트리거가 발견되면 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 일치하는 중괄호를 찾기 위해 메서드가 호출됩니다. 마지막으로 두 중괄호가 강조 표시됩니다.

 중괄호는 트리거 및 구문 분석 이유의 이름에 사용되지만 이 프로세스는 실제 중괄호에만 국한되지 않습니다. 일치하는 쌍으로 지정된 모든 문자 쌍이 지원됩니다. 예로는 (and) \< 및 > 및 [및]이 포함됩니다.

 언어 서비스가 일치하는 중괄호를 지원한다고 가정합니다.

1. 사용자가 닫는 곱슬 대괄호(})를 입력합니다.

2. 곱슬 대괄호는 소스 파일의 커서에 삽입되고 커서가 하나씩 진행됩니다.

3. 클래스의 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> <xref:Microsoft.VisualStudio.Package.Source> 메서드는 형식이 있는 닫는 괄호를 사용하여 호출됩니다.

4. 메서드는 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 클래스의 메서드를 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> <xref:Microsoft.VisualStudio.Package.Source> 호출하여 현재 커서 위치 바로 앞의 위치에서 토큰을 가져옵니다. 이 토큰은 입력된 닫는 중괄호에 해당합니다.

    1. 메서드는 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 현재 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 줄의 <xref:Microsoft.VisualStudio.Package.Colorizer> 모든 토큰을 가져오려면 개체의 메서드를 호출합니다.

    2. 메서드는 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 현재 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> 줄의 <xref:Microsoft.VisualStudio.Package.IScanner> 텍스트를 사용 하 고 개체에 메서드를 호출 합니다.

    3. 메서드는 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 개체의 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> 메서드를 <xref:Microsoft.VisualStudio.Package.IScanner> 반복적으로 호출하여 현재 줄에서 모든 토큰을 수집합니다.

    4. 메서드는 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 클래스에서 private <xref:Microsoft.VisualStudio.Package.Source> 메서드를 호출하여 원하는 위치를 포함하는 토큰을 가져오고 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 메서드에서 얻은 토큰 목록을 전달합니다.

5. 메서드는 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 메서드에서 반환되는 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 토큰의 토큰 트리거 플래그를 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 찾습니다. 즉, 닫는 중괄호를 나타내는 토큰)입니다.

6. 의 트리거 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 플래그가 발견되면 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 클래스의 <xref:Microsoft.VisualStudio.Package.Source> 메서드가 호출됩니다.

7. 메서드는 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> <xref:Microsoft.VisualStudio.Package.ParseReason>의 구문 분석 이유 값으로 구문 분석 작업을 시작합니다. 이 작업은 궁극적으로 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 클래스에서 <xref:Microsoft.VisualStudio.Package.LanguageService> 메서드를 호출합니다. 비동기 구문 분석이 활성화된 경우 백그라운드 스레드에서 메서드에 대한 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 이 호출이 발생합니다.

8. 구문 분석 작업이 완료되면 클래스에서 명명된 `HandleMatchBracesResponse` 내부 완료 처리기(콜백 메서드라고도 함)가 <xref:Microsoft.VisualStudio.Package.Source> 호출됩니다. 이 호출은 파서가 <xref:Microsoft.VisualStudio.Package.LanguageService> 아닌 기본 클래스에 의해 자동으로 이루어집니다.

9. 메서드는 `HandleMatchBracesResponse` <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.ParseRequest> 개체에 저장 되는 개체에서 범위 목록을 가져옵니다. 범위는 소스 파일의 줄과 문자 범위를 지정하는 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> 구조입니다. 이 범위 목록에는 일반적으로 개구및 닫기 중괄호에 대해 각각 하나씩 두 개의 범위가 포함됩니다.

10. 메서드는 `HandleBracesResponse` <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 개체에 저장 되는 개체에 <xref:Microsoft.VisualStudio.Package.ParseRequest> 메서드를 호출 합니다. 이렇게 하면 지정된 범위가 강조 표시됩니다.

11. 속성이 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 활성화된 경우 `HandleBracesResponse` 메서드는 일치하는 범위로 둘러싸인 텍스트를 가져오고 상태 표시줄에 해당 범위의 처음 80자를 표시합니다. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 이 방법은 일치하는 쌍과 함께 제공되는 언어 요소를 포함하는 경우에 가장 적합합니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 속성을 참조하세요.

12. 완료되었습니다.

### <a name="summary"></a>요약
 일치하는 중괄호 작업은 일반적으로 간단한 언어 요소 쌍으로 제한됩니다. 일치하는`if(...)`삼중 요소("" "`{`" 및 "`}`" 또는`else`"`{`" 및`}`"" 및 "")와 같은 더 복잡한 요소는 단어 완성 작업의 일부로 강조 표시될 수 있습니다. 예를 들어 "else" 단어가 완료되면 일치하는 "`if`" 문을 강조 표시할 수 있습니다. 일련의 `if` / `else if` 문이 있는 경우 일치하는 중괄호와 동일한 메커니즘을 사용하여 모든 문을 강조 표시할 수 있습니다. 기본 <xref:Microsoft.VisualStudio.Package.Source> 클래스는 이미 다음과 같이 이를 지원합니다: 스캐너는 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 커서 위치 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 이전의 토큰에 대한 트리거 값과 결합된 토큰 트리거 값을 반환해야 합니다.

 자세한 내용은 [레거시 언어 서비스에서 중괄호 일치를](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)참조하십시오.

## <a name="parsing-for-colorization"></a>색상 화를 위한 구문 분석
 소스 코드 색상을 지정하는 것은 간단하며 토큰 유형을 식별하고 해당 유형에 대한 색상 정보를 반환하기만 하면 됩니다. 클래스는 <xref:Microsoft.VisualStudio.Package.Colorizer> 모든 토큰에 대한 색상 정보를 제공하기 위해 편집기와 스캐너 사이의 중개자 역할을 합니다. 클래스는 <xref:Microsoft.VisualStudio.Package.Colorizer> 개체를 <xref:Microsoft.VisualStudio.Package.IScanner> 사용하여 줄의 색상을 지정하고 소스 파일의 모든 줄에 대한 상태 정보를 수집합니다. MPF 언어 서비스 클래스에서는 <xref:Microsoft.VisualStudio.Package.Colorizer> <xref:Microsoft.VisualStudio.Package.IScanner> 인터페이스를 통해서만 스캐너와 통신하기 때문에 클래스를 재정의할 필요가 없습니다. 클래스에서 <xref:Microsoft.VisualStudio.Package.IScanner> <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 메서드를 재정의하여 인터페이스를 구현하는 개체를 <xref:Microsoft.VisualStudio.Package.LanguageService> 제공합니다.

 스캐너는 <xref:Microsoft.VisualStudio.Package.IScanner> 메서드를 통해 소스 코드 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> 줄이 제공됩니다. 메서드에 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> 대한 호출은 줄이 토큰이 소진될 때까지 줄에서 다음 토큰을 얻기 위해 반복됩니다. 색상화를 위해 MPF는 모든 소스 코드를 일련의 선으로 처리합니다. 따라서 스캐너는 라인으로 오는 소스에 대처할 수 있어야 합니다. 또한 모든 회선은 언제든지 스캐너에 전달할 수 있으며, 유일한 보장은 스캐너가 스캔할 라인 전에 라인에서 상태 변수를 수신한다는 것입니다.

 클래스는 <xref:Microsoft.VisualStudio.Package.Colorizer> 토큰 트리거를 식별하는 데도 사용됩니다. 이러한 트리거는 MPF에 특정 토큰이 단어 완성 또는 일치 하는 중괄호와 같은 보다 복잡한 작업을 시작할 수 있음을 알려줍니다. 이러한 트리거를 식별하는 것은 빠르고 모든 위치에서 발생해야 하므로 스캐너가 이 작업에 가장 적합합니다.

 자세한 내용은 [레거시 언어 서비스의 색지정 구문을](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)참조하십시오.

## <a name="parsing-for-functionality-and-scope"></a>기능 및 범위에 대한 구문 분석
 기능 및 범위에 대한 구문 분석은 발생하는 토큰 유형을 식별하는 것보다 더 많은 노력이 필요합니다. 파서는 토큰 의 유형뿐만 아니라 토큰이 사용되는 기능도 식별해야합니다. 예를 들어 식별자는 이름일 뿐이지만 해당 언어에서 식별자는 컨텍스트에 따라 클래스, 네임스페이스, 메서드 또는 변수의 이름일 수 있습니다. 토큰의 일반적인 유형은 식별자일 수 있지만 식별자는 토큰이 무엇이고 정의된 위치에 따라 다른 의미를 가질 수도 있습니다. 이 식별을 사용하려면 구문 분석중인 언어에 대한 보다 광범위한 지식을 구문 분석해야 합니다. 이것은 클래스가 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 들어오는 곳입니다. 클래스는 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 식별자, 메서드, 일치하는 언어 쌍(예: 괄호 및 괄호) 및 언어 삼중(예: " "`foreach()``{`및 ""와`}`같은 세 부분으로 는 언어 쌍과 유사)에 대한 정보를 수집합니다. 또한 디버거를 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 로드할 필요가 없도록 중단점의 초기 유효성 검사에 사용되는 코드 식별을 지원하기 위해 클래스를 재정의할 수 있으며, 프로그램이 디버깅될 때 로컬 변수 와 매개 변수를 자동으로 표시하고 디버거가 제공하는 것 외에도 적절한 로컬 변수 및 매개 변수를 식별하기 위해 parser가 필요한 **Autos** 디버깅 창입니다.

 개체는 <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.ParseRequest> 개체의 일부로 파서에 전달되고 새 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 개체가 만들어날 때마다 <xref:Microsoft.VisualStudio.Package.ParseRequest> 새 개체가 만들어집니다. 또한 메서드는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 다양한 IntelliSense 작업을 처리하는 데 사용되는 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체를 반환해야 합니다. 개체는 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 구문 분석 이유에 따라 선언 목록과 메서드에 대한 목록을 유지 관리합니다. 클래스를 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 구현해야 합니다.

## <a name="see-also"></a>참조
- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [레거시 언어 서비스 개요](../../extensibility/internals/legacy-language-service-overview.md)
- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [레거시 언어 서비스의 중괄호 일치](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
