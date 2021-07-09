---
title: 옵션, 텍스트 편집기, C#, 고급
description: C# 섹션의 고급 페이지를 사용하여 C#에 대한 편집기 서식, 코드 리팩터링 및 XML 문서 주석의 설정을 수정하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 06/01/2021
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 29f6dd2b4a101132bc7bc19664c51fd5d4b8283e
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2021
ms.locfileid: "111351992"
---
# <a name="options-text-editor-c-advanced"></a>옵션, 텍스트 편집기, C#, 고급

**고급** 옵션을 사용하여 C#의 편집기 서식, 코드 리팩터링 및 XML 문서 주석에 대한 설정을 수정합니다. 이 옵션 페이지에 액세스하려면 **도구** > **옵션** 을 선택한 다음, **텍스트 편집기** > **C#**  > **고급** 을 선택합니다.

> [!NOTE]
> 모든 옵션이 여기에 나열되지는 않습니다.

## <a name="analysis"></a>분석

- 실시간 코드 분석 또는 백그라운드 분석 범위

   관리 코드에 대한 백그라운드 분석 범위를 구성합니다. 자세한 내용은 [방법: 관리 코드에 대한 실시간 코드 분석 범위를 구성합니다](../../code-quality/configure-live-code-analysis-scope-managed-code.md).

## <a name="using-directives"></a>Using 지시문

- using 정렬 시 ‘System’ 지시문 먼저 배치

   선택한 경우, 마우스 오른쪽 단추 클릭 메뉴의 **using 제거 및 정렬** 명령은 `using` 지시문을 정렬하고 '시스템' 네임스페이스를 목록의 맨 위에 배치합니다.

   정렬 이전:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   정렬 이후:

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using AutoMapper;
   using FluentValidation;
   using Newtonsoft.Json;
   ```

- Using 지시문 그룹 구분

   선택한 경우, 마우스 오른쪽 단추 클릭 메뉴의 **using 제거 및 정렬** 명령은 동일한 루트 네임스페이스를 가진 지시문 그룹 사이에 빈 줄을 삽입하여 `using` 지시문을 구분합니다.

   정렬 이전:

   ```csharp
   using AutoMapper;
   using FluentValidation;
   using System.Collections.Generic;
   using System.Linq;
   using Newtonsoft.Json;
   using System;
   ```

   정렬 이후:

   ```csharp
   using AutoMapper;

   using FluentValidation;

   using Newtonsoft.Json;

   using System;
   using System.Collections.Generic;
   using System.Linq;
   ```

::: moniker range=">=vs-2019"                                              
- .NET Framework 어셈블리의 형식에 대한 using 제안
::: moniker-end
                                         
::: moniker range="vs-2017"                                                
- 참조 어셈블리의 형식에 대한 using 제안
::: moniker-end                                                            

- NuGet 패키지의 형식에 대한 using 제안

   이러한 옵션을 선택한 경우 [빠른 작업](../quick-actions.md)을 사용하여 NuGet 패키지를 설치하고 참조되지 않은 형식에 대한 `using` 지시문을 추가할 수 있습니다.

   ![Visual Studio의 NuGet 패키지 설치 빠른 작업](media/nuget-lightbulb.png)

- 붙여넣을 때 누락된 using 지시문 추가

    이 옵션을 선택하면 파일에 형식을 붙여넣을 때 `using` 지시문이 코드에 자동으로 추가됩니다.

## <a name="highlighting"></a>강조 표시

- 커서 아래의 기호에 대한 참조 강조

   기호 내부에 커서를 놓거나 기호를 클릭하면 코드 파일에 있는 해당 기호의 모든 인스턴스가 강조 표시됩니다.

## <a name="outlining"></a>개요

- 개요 모드로 파일 열기

   이 옵션을 선택하면 축소 가능한 코드 블록을 만드는 코드 파일이 자동으로 요약됩니다. 파일이 처음 열리면 #regions 블록 및 비활성 코드 블록이 축소됩니다.

- 프로시저 줄 구분선 표시

   텍스트 편집기가 프로시저의 시각적 범위를 표시합니다. 다음 표에 나열된 위치에서 프로젝트의 *.cs* 소스 파일에 줄이 그려집니다.

   |.cs 소스 파일 내 위치|선 위치의 예|
   |---------------------------------|------------------------------|
   |블록 선언 구문의 닫기 뒤|-   클래스, 구조체, 모듈, 인터페이스 또는 열거형의 끝<br />-   속성, 함수 또는 하위 뒤<br />-   속성에서 get 및 set 절 사이 아님|
   |일련의 한 줄 구문 뒤|-   가져오기 문 뒤, 클래스 파일에서 형식 정의 앞<br />-   클래스에서 선언된 모든 프로시저 뒤, 프로시저 앞|
   |한 줄 선언 뒤(블록 수준 선언 외)|-   가져오기 문, 상속 문, 변수 선언, 이벤트 선언, 대리자 선언 및 DLL 선언 문에 이어서|

## <a name="block-structure-guides"></a>블록 구조 가이드

코드에서 중괄호( **{}** ) 사이에 세로 점선을 표시하려면 이 확인란을 선택합니다. 그러면 선언 수준 및 코드 수준 구문의 개별 코드 블록을 쉽게 확인할 수 있습니다.

## <a name="comments"></a>의견

- ///에 대해 XML 문서 주석 생성

   이 옵션을 선택한 경우 `///` 주석 도입부를 입력한 후 XML 문서 주석에 대한 XML 요소를 삽입합니다. XML 문서에 대한 자세한 내용은 [XML 문서 주석(C# 프로그래밍 가이드)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)을 참조하세요.

::: moniker range=">=vs-2019"

## <a name="inline-hints"></a>인라인 힌트

- 인라인 매개 변수 이름 힌트 
    
    선택하면 리터럴, 캐스트 리터럴 및 개체 인스턴스화에 대한 매개 변수 이름 힌트가 함수 호출의 각 인수 앞에 삽입됩니다.  
    
    ![CSharp의 인라인 매개 변수 이름 힌트](media/inline-parameter-name-hints-csharp.png)

- 인라인 형식 힌트 
    
    선택하면 유추된 형식 및 람다 매개 변수 형식의 변수에 대한 형식 힌트를 삽입합니다.  
    
    ![CSharp용 인라인 형식 힌트](media/inline-type-hints-csharp.png)

## <a name="inheritance-margin"></a>상속 여백 

- 선택하면 코드의 구현 및 재정의를 나타내는 여백에 아이콘이 추가됩니다. 상속 여백 아이콘을 클릭하면 선택하여 이동할 수 있는 상속 옵션이 표시됩니다.

    ![상속 여백](media/inheritance-margin.png)

::: moniker-end

## <a name="see-also"></a>참조

- [방법: 문서 생성에 대한 XML 주석 삽입](../../ide/reference/generate-xml-documentation-comments.md)
- [XML 문서 주석(C# 프로그래밍 가이드)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [XML 주석을 사용하여 코드 문서화(C# 가이드)](/dotnet/csharp/codedoc)
- [언어별 편집기 옵션 설정](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)
