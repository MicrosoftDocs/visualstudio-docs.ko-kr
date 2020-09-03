---
title: 레거시 언어 서비스 파서 및 스캐너 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707323"
---
# <a name="legacy-language-service-parser-and-scanner"></a>레거시 언어 서비스 파서 및 검사기
파서는 언어 서비스의 핵심입니다. MPF (관리 되는 패키지 프레임 워크) 언어 클래스에는 표시 되는 코드에 대 한 정보를 선택 하기 위한 언어 파서가 필요 합니다. 파서는 텍스트를 어휘 토큰으로 구분 하 고 형식 및 기능으로 이러한 토큰을 식별 합니다.

## <a name="discussion"></a>토론(Discussion)
 다음은 c # 메서드입니다.

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

 이 예에서 토큰은 단어와 문장 부호를 나타냅니다. 토큰 종류는 다음과 같습니다.

|토큰 이름|토큰 형식|
|----------------|----------------|
|네임 스페이스, 클래스, public, void, int|키워드(keyword)|
|=|operator|
|{ } ( ) ;|구분 기호|
|MyNamespace, MyClass, MyFunction, arg1, var1|identifier|
|MyNamespace|namespace|
|MyClass|class|
|MyFunction|메서드|
|arg1|매개 변수(parameter)|
|var1|지역 변수(local variable)|

 파서의 역할은 토큰을 식별 하는 것입니다. 일부 토큰에는 두 개 이상의 형식이 있을 수 있습니다. 파서가 토큰을 식별 한 후 언어 서비스는이 정보를 사용 하 여 구문 강조 표시, 중괄호 일치 및 IntelliSense 작업과 같은 유용한 기능을 제공할 수 있습니다.

## <a name="types-of-parsers"></a>파서 유형
 언어 서비스 파서는 컴파일러의 일부로 사용 되는 파서와 동일 하지 않습니다. 그러나 이러한 종류의 파서는 스캐너와 파서를 모두 사용 해야 합니다. 컴파일러 파서와 동일한 방식으로 사용 해야 합니다.

- 스캐너는 토큰 유형을 식별 하는 데 사용 됩니다. 이 정보는 구문 강조에 사용되며 중괄호 일치 등의 다른 작업을 트리거할 수 있는 토큰 유형을 신속하게 식별하는 데 사용됩니다. 이 스캐너는 인터페이스로 표시 됩니다 <xref:Microsoft.VisualStudio.Package.IScanner> .

- 파서는 토큰의 범위와 함수를 설명 하는 데 사용 됩니다. 이 정보는 IntelliSense 작업에서 메서드, 변수, 매개 변수 및 선언과 같은 언어 요소를 식별 하 고 컨텍스트를 기반으로 멤버 및 메서드 시그니처의 목록을 제공 하는 데 사용 됩니다. 이 파서는 중괄호 및 괄호와 같은 일치 하는 언어 요소 쌍을 찾는 데도 사용 됩니다. 이 파서는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 클래스의 메서드를 통해 액세스 됩니다 <xref:Microsoft.VisualStudio.Package.LanguageService> .

  언어 서비스용 스캐너 및 파서를 구현 하는 방법은 사용자가 결정 합니다. 파서가 작동 하는 방법과 사용자 고유의 파서를 작성 하는 방법을 설명 하는 몇 가지 리소스를 사용할 수 있습니다. 또한 파서를 만드는 데 도움이 되는 몇 가지 무료 및 상용 제품을 사용할 수 있습니다.

### <a name="the-parsesource-parser"></a>ParseSource 파서
 토큰을 일종의 실행 코드 형식으로 변환 하는 컴파일러의 일부로 사용 되는 파서와 달리 언어 서비스 파서는 여러 가지 다양 한 이유 및 여러 컨텍스트에서 호출 될 수 있습니다. 클래스의 메서드에서이 접근 방식을 구현 하는 방법은 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 사용자가 결정 합니다. 메서드는 백그라운드 스레드에서 호출 될 수 있다는 점을 명심 해야 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 합니다.

> [!CAUTION]
> 구조체에는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 개체에 대 한 참조가 포함 되어 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . 이 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 개체는 백그라운드 스레드에서 사용할 수 없습니다. 실제로 대부분의 기본 MPF 클래스는 백그라운드 스레드에서 사용할 수 없습니다. 여기에는 <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter> 뷰를 <xref:Microsoft.VisualStudio.Package.CodeWindowManager> 사용 하 여 직접 또는 간접적으로 통신 하는,, 클래스 및 기타 클래스가 포함 됩니다.

 이 파서는 일반적으로 처음 호출 될 때 또는 구문 분석 이유 값이 지정 된 경우 전체 소스 파일을 구문 분석 <xref:Microsoft.VisualStudio.Package.ParseReason> 합니다. 이 메서드에 대 한 후속 호출은 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 구문 분석 된 코드의 작은 부분을 처리 하 고 이전 전체 구문 분석 작업의 결과를 사용 하 여 훨씬 더 빠르게 실행할 수 있습니다. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>메서드는 및 개체를 통해 구문 분석 작업의 결과를 전달 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> . <xref:Microsoft.VisualStudio.Package.AuthoringSink>개체는 특정 구문 분석 이유에 대 한 정보 (예: 매개 변수 목록을 포함 하는 일치 하는 중괄호 또는 메서드 시그니처의 범위 정보)를 수집 하는 데 사용 됩니다. 에서는 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 선언 및 메서드 시그니처의 컬렉션과 고급 편집으로 이동 옵션 (**정의**로 이동, **선언으로**이동, **참조로**이동)도 지원 합니다.

### <a name="the-iscanner-scanner"></a>IScanner 스캐너
 또한을 구현 하는 스캐너를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Package.IScanner> . 그러나이 스캐너는 클래스를 통해 줄 단위로 작동 하므로 <xref:Microsoft.VisualStudio.Package.Colorizer> 일반적으로 구현 하기가 더 쉽습니다. MPF는 각 줄의 시작 부분에서 <xref:Microsoft.VisualStudio.Package.Colorizer> 스캐너에 전달 되는 상태 변수로 사용할 값을 클래스에 제공 합니다. 각 줄의 끝에서 스캐너는 업데이트 된 상태 변수를 반환 합니다. MPF는 각 줄에 대해이 상태 정보를 캐시 하므로 스캐너가 소스 파일의 시작 부분에서 시작 하지 않고도 줄에서 구문 분석을 시작할 수 있습니다. 이렇게 빠른 단일 줄을 검색 하면 편집기에서 사용자에 게 빠른 피드백을 제공할 수 있습니다.

## <a name="parsing-for-matching-braces"></a>중괄호에 대 한 구문 분석
 이 예제에서는 사용자가 입력 한 닫는 중괄호와 일치 하는 컨트롤의 흐름을 보여 줍니다. 이 프로세스에서 색 지정에 사용 되는 스캐너는 토큰 형식을 결정 하는 데 사용 되며 토큰에서 일치 하는 중괄호 작업을 트리거할 수 있는지 여부를 결정 하는 데에도 사용 됩니다. 트리거가 있는 경우 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드를 호출 하 여 일치 하는 중괄호를 찾습니다. 마지막으로 두 개의 중괄호가 강조 표시 됩니다.

 트리거 이름 및 구문 분석 이유에서 중괄호가 사용 되더라도이 프로세스는 실제 중괄호로 제한 되지 않습니다. 일치 하는 쌍으로 지정 된 모든 문자 쌍이 지원 됩니다. 예를 들면 (and), \< and > 및 [및]가 있습니다.

 언어 서비스에서 일치 하는 중괄호를 지원 한다고 가정 합니다.

1. 사용자가 닫는 중괄호 (})를 입력 합니다.

2. 중괄호는 소스 파일의 커서에 삽입 되며 커서는 1로 이동 합니다.

3. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>클래스의 메서드는 <xref:Microsoft.VisualStudio.Package.Source> 형식화 된 닫는 중괄호를 사용 하 여 호출 됩니다.

4. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>메서드는 <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 클래스의 메서드를 호출 <xref:Microsoft.VisualStudio.Package.Source> 하 여 현재 커서 위치 바로 앞의 위치에서 토큰을 가져옵니다. 이 토큰은 형식화 된 닫는 중괄호에 해당 합니다.

    1. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>메서드는 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> 개체에 대해 메서드를 호출 <xref:Microsoft.VisualStudio.Package.Colorizer> 하 여 현재 줄의 모든 토큰을 가져옵니다.

    2. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>메서드는 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> <xref:Microsoft.VisualStudio.Package.IScanner> 개체에서 현재 줄의 텍스트를 사용 하 여 메서드를 호출 합니다.

    3. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>메서드는 <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> 개체에 대해 메서드를 반복적 <xref:Microsoft.VisualStudio.Package.IScanner> 으로 호출 하 여 현재 줄에서 모든 토큰을 수집 합니다.

    4. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>메서드는 클래스에서 private 메서드를 호출 <xref:Microsoft.VisualStudio.Package.Source> 하 여 원하는 위치를 포함 하는 토큰을 가져오고 메서드에서 가져온 토큰 목록에 전달 합니다 <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> .

5. 메서드는 메서드에서 반환 되는 토큰 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 에 대 한 토큰 트리거 플래그 ( <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> 닫는 중괄호를 나타내는 토큰)를 찾습니다.

6. 의 트리거 플래그가 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 발견 되 면 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 클래스의 메서드가 <xref:Microsoft.VisualStudio.Package.Source> 호출 됩니다.

7. <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>메서드는 구문 분석 이유 값을 사용 하 여 구문 분석 작업을 시작 합니다 <xref:Microsoft.VisualStudio.Package.ParseReason> . 이 작업은 궁극적 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 으로 클래스의 메서드를 호출 <xref:Microsoft.VisualStudio.Package.LanguageService> 합니다. 비동기 구문 분석을 사용 하는 경우 메서드에 대 한이 호출은 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 백그라운드 스레드에서 발생 합니다.

8. 구문 분석 작업이 완료 되 면 라는 내부 완료 처리기 (콜백 메서드 라고도 함) `HandleMatchBracesResponse` 가 클래스에서 호출 됩니다 <xref:Microsoft.VisualStudio.Package.Source> . 이 호출은 <xref:Microsoft.VisualStudio.Package.LanguageService> 파서가 아닌 기본 클래스에 의해 자동으로 수행 됩니다.

9. `HandleMatchBracesResponse`메서드는 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 개체에 저장 된 개체에서 범위 목록을 가져옵니다 <xref:Microsoft.VisualStudio.Package.ParseRequest> . Span은 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> 소스 파일에서 줄과 문자의 범위를 지정 하는 구조체입니다. 이 범위 목록에는 일반적으로 여는 중괄호와 닫는 중괄호 각각에 해당 하는 두 개의 범위가 포함 되어 있습니다.

10. `HandleBracesResponse`메서드는 개체에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> 저장 된 개체에 대해 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.Package.ParseRequest> . 그러면 지정 된 범위가 강조 표시 됩니다.

11. 속성을 사용 하는 경우 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 메서드는 일치 하는 범위에 속하는 `HandleBracesResponse` 텍스트를 가져오고 상태 표시줄에 해당 범위의 처음 80 자를 표시 합니다. 이는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드에 일치 하는 쌍과 함께 제공 되는 언어 요소가 포함 된 경우에 가장 적합 합니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> 속성을 참조하세요.

12. 완료되었습니다.

### <a name="summary"></a>요약
 일치 하는 중괄호 연산은 일반적으로 단순 언어 요소 쌍으로 제한 됩니다. 일치 삼중 쌍 ("", "", "", "", "" 및 "")와 같은 더 복잡 한 요소는 `if(...)` `{` `}` `else` `{` `}` 단어 완성 작업의 일부로 강조 표시할 수 있습니다. 예를 들어 "else" 단어가 완료 되 면 일치 하는 " `if` " 문을 강조 표시할 수 있습니다. 일련의 문이 있는 경우 일치 하는 `if` / `else if` 중괄호와 동일한 메커니즘을 사용 하 여 모든 문을 강조 표시할 수 있습니다. <xref:Microsoft.VisualStudio.Package.Source>기본 클래스는 다음과 같이이를 이미 지원 합니다. 스캐너는 토큰 트리거 값을 <xref:Microsoft.VisualStudio.Package.TokenTriggers> <xref:Microsoft.VisualStudio.Package.TokenTriggers> 커서 위치 앞에 있는 토큰의 트리거 값과 결합 하 여 반환 해야 합니다.

 자세한 내용은 [레거시 언어 서비스의 중괄호 일치](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)를 참조 하세요.

## <a name="parsing-for-colorization"></a>색 지정을 위한 구문 분석
 소스 코드를 색으로 지정 하면 토큰 형식을 식별 하 고 해당 형식에 대 한 색 정보를 반환 합니다. <xref:Microsoft.VisualStudio.Package.Colorizer>클래스는 편집기와 스캐너 간의 중개자 역할을 하 여 모든 토큰에 대 한 색 정보를 제공 합니다. 클래스는 개체를 사용 하 여 줄의 색을 하 <xref:Microsoft.VisualStudio.Package.Colorizer> <xref:Microsoft.VisualStudio.Package.IScanner> 고 소스 파일의 모든 줄에 대 한 상태 정보를 수집 하는 데 도움이 됩니다. MPF 언어 서비스 클래스에서 <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스는 인터페이스를 통해서만 스캐너와 통신 하므로 재정의할 필요가 없습니다 <xref:Microsoft.VisualStudio.Package.IScanner> . <xref:Microsoft.VisualStudio.Package.IScanner>클래스에서 메서드를 재정의 하 여 인터페이스를 구현 하는 개체를 제공 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> .

 스캐너에는 <xref:Microsoft.VisualStudio.Package.IScanner> 메서드를 통해 소스 코드 줄이 제공 됩니다 <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> . <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A>줄이 토큰을 모두 사용할 때까지 줄에서 다음 토큰을 가져오기 위해 메서드에 대 한 호출이 반복 됩니다. 색을 지정 하기 위해 MPF는 모든 소스 코드를 일련의 선으로 처리 합니다. 따라서 스캐너는 원본에서 제공 되는 소스를 선으로 처리할 수 있어야 합니다. 또한 언제 든 지 모든 줄을 스캐너에 전달할 수 있으며, 스캐너가 검색할 줄 앞의 줄에서 상태 변수를 수신 하는 경우에만 보장 됩니다.

 <xref:Microsoft.VisualStudio.Package.Colorizer>클래스는 토큰 트리거를 식별 하는 데도 사용 됩니다. 이러한 트리거는 특정 토큰이 단어 완성 또는 중괄호와 같은 좀 더 복잡 한 작업을 시작할 수 있음을 MPF에 알립니다. 이러한 트리거는 신속 하 게 식별 해야 하며 어떤 위치에서 나 발생 해야 하므로 스캐너는이 작업에 가장 적합 합니다.

 자세한 내용은 [레거시 언어 서비스의 구문 색 색상화](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)를 참조 하세요.

## <a name="parsing-for-functionality-and-scope"></a>기능 및 범위에 대 한 구문 분석
 기능 및 범위에 대 한 구문 분석에는 발생 하는 토큰의 유형을 식별 하는 것 보다 더 많은 노력이 필요 합니다. 파서는 토큰의 유형 뿐만 아니라 토큰이 사용 되는 기능을 식별 해야 합니다. 예를 들어 식별자는 이름 이지만 언어에서 식별자는 컨텍스트에 따라 클래스, 네임 스페이스, 메서드 또는 변수의 이름일 수 있습니다. 토큰의 일반 형식은 식별자 일 수 있지만 식별자는 정의 된 위치 및 정의 된 위치에 따라 다른 의미를 가질 수도 있습니다. 이 id를 사용 하려면 구문 분석 되는 언어에 대 한 보다 광범위 한 정보를 파서가 받아야 합니다. 클래스가 제공 되는 위치입니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink> . <xref:Microsoft.VisualStudio.Package.AuthoringSink>클래스는 식별자, 메서드, 일치 하는 언어 쌍 (예: 중괄호 및 괄호) 및 언어 삼중 쌍에 대 한 정보를 수집 합니다 (세 부분 (예: "" "" `foreach()` `{` 및 "")을 제외 하 고 언어 쌍과 유사) `}` . 또한 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 디버거를 로드 하지 않아도 되도록 중단점의 초기 유효성 검사에 사용 되는 코드 id를 지원 하도록 클래스를 재정의할 수 있으며, 프로그램이 디버깅 되는 동안 로컬 변수와 매개 변수를 자동으로 표시 하 고 디버거가 표시 하는 것 외에도 파서가 적절 한 지역 변수 및 매개 변수를 식별 해야 하는 **자동** 디버깅 창을 지원 하도록 클래스를 재정의할 수 있습니다.

 개체는 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 개체의 일부로 파서에 전달 되 고 새 개체가 <xref:Microsoft.VisualStudio.Package.ParseRequest> 만들어질 때마다 새 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 개체가 만들어집니다 <xref:Microsoft.VisualStudio.Package.ParseRequest> . 또한 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 메서드는 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 다양 한 IntelliSense 작업을 처리 하는 데 사용 되는 개체를 반환 해야 합니다. <xref:Microsoft.VisualStudio.Package.AuthoringScope>개체는 구문 분석의 이유에 따라 선언 목록 및 메서드에 대 한 목록을 유지 관리 합니다. <xref:Microsoft.VisualStudio.Package.AuthoringScope>클래스를 구현 해야 합니다.

## <a name="see-also"></a>참고 항목
- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [레거시 언어 서비스 개요](../../extensibility/internals/legacy-language-service-overview.md)
- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [레거시 언어 서비스의 중괄호 일치](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
