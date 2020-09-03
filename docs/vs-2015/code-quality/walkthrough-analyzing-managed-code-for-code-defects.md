---
title: '연습: 코드 오류에 대 한 관리 코드 분석 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9478394162051fc08c33047cf1ac24275aff75e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609326"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>연습: 관리 코드의 코드 오류 분석
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 코드 분석 도구를 사용 하 여 코드 오류에 대 한 관리 되는 프로젝트를 분석 합니다.

 이 연습에서는 Microsoft .NET Framework 디자인 지침을 준수 하기 위해 코드 분석을 사용 하 여 .NET 관리 코드 어셈블리를 분석 하는 과정을 단계별로 안내 합니다.

 이 연습에서는 다음을 수행합니다.

- 코드 오류 경고를 분석 하 고 수정 합니다.

## <a name="prerequisites"></a>사전 요구 사항

- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].

## <a name="create-a-class-library"></a>클래스 라이브러리 만들기

#### <a name="to-create-a-class-library"></a>클래스 라이브러리를 만들려면

1. 의 **파일** 메뉴에서 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **새로 만들기** 를 클릭 한 다음 **프로젝트**를 클릭 합니다.

2. **새 프로젝트** 대화 상자의 **프로젝트 형식**에서 **Visual c #** 을 클릭 합니다.

3. **템플릿**에서 **클래스 라이브러리**를 선택합니다.

4. **이름** 텍스트 상자에 **CodeAnalysisManagedDemo** 를 입력 한 다음 **확인**을 클릭 합니다.

5. 프로젝트를 만든 후 Class1.cs 파일을 엽니다.

6. Class1.cs의 기존 텍스트를 다음 코드로 바꿉니다.

     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`

7. Class1.cs 파일을 저장 합니다.

## <a name="analyze-the-project"></a>프로젝트 분석

#### <a name="to-analyze-a-managed-project-for-code-defects"></a>코드 오류에 대 한 관리 되는 프로젝트를 분석 하려면

1. **솔루션 탐색기**에서 CodeAnalysisManagedDemo 프로젝트를 선택 합니다.

2. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

     CodeAnalysisManagedDemo 속성 페이지가 표시 됩니다.

3. **Codeanalysis**를 클릭 합니다.

4. **빌드에 코드 분석 사용 (CODE_ANALYSIS 상수 정의**)이 선택 되어 있는지 확인 합니다.

5. **이 규칙 집합 실행** 드롭다운 목록에서 **Microsoft 모든 규칙**을 선택 합니다.

6. **파일** 메뉴에서 **선택한 항목 저장**을 클릭 한 다음 manageddemo 속성 페이지를 닫습니다.

7. **빌드** 메뉴에서 **manageddemo 빌드**를 클릭 합니다.

     CodeAnalysisManagedDemo 프로젝트 빌드 경고는 **코드 분석** 및 **출력** 창에 보고 됩니다.

     **코드 분석** 창이 표시 되지 않으면 **분석** 메뉴에서 **창** 을 선택한 다음 **코드 분석을 선택**합니다.

## <a name="correct-the-code-analysis-issues"></a>코드 분석 문제 해결

#### <a name="to-correct-code-analysis-rule-violations"></a>코드 분석 규칙 위반을 수정 하려면

1. **보기** 메뉴에서 **오류 목록**을 클릭합니다.

     선택한 개발자 프로필에 따라 **보기** 메뉴에서 **다른 창** 을 가리키고 **오류 목록**를 클릭 해야 할 수도 있습니다.

2. **솔루션 탐색기**에서 **모든 파일 표시**를 클릭 합니다.

3. 그런 다음 속성 노드를 확장 하 고 AssemblyInfo.cs 파일을 엽니다.

4. 다음을 사용 하 여 경고를 수정 합니다.

- [CA1014: CLSCompliantAttribute를 사용 하 여 어셈블리를 표시](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)합니다. 디자인: ' demo '는 CLSCompliantAttribute로 표시 되어야 하 고 해당 값은 true 여야 합니다.

  - `using``System;`AssemblyInfo.cs 파일에 코드를 추가 합니다.

       그런 다음 `[assembly: CLSCompliant(true)]` AssemblyInfo.cs 파일의 끝에 코드를 추가 합니다.

       프로젝트를 다시 빌드합니다.

- [CA1032: 표준 예외 생성자를 구현](../code-quality/ca1032-implement-standard-exception-constructors.md)합니다. 디자인:이 클래스에 다음 생성자를 추가 합니다. public Demo (String)

  - 클래스에 생성자를 추가 `public demo (String s) : base(s) { }` `demo` 합니다.

- [CA1032: 표준 예외 생성자 구현](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft 디자인:이 클래스에는 public Demo (문자열, 예외) 생성자를 추가 합니다.

  - 클래스에 생성자를 추가 `public demo (String s, Exception e) : base(s, e) { }` `demo` 합니다.

- [CA1032: 표준 예외 생성자 구현](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft 디자인: protected Demo (SerializationInfo, StreamingContext) 클래스에 다음 생성자를 추가 합니다.

  - `using System.Runtime.Serialization;`Class1.cs 파일의 시작 부분에 코드를 추가 합니다.

       다음으로 생성자를 추가 합니다. `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

       프로젝트를 다시 빌드합니다.

- [CA1032: 표준 예외 생성자를 구현](../code-quality/ca1032-implement-standard-exception-constructors.md)합니다. 디자인:이 클래스에 다음 생성자를 추가 합니다. public demo ()

  - 클래스에 생성자를 추가 `public demo () : base() { }` `demo` **합니다.**

       프로젝트를 다시 빌드합니다.

- [CA1709: 식별자](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)의 대/소문자를 올바르게 지정 해야 합니다. 이름: ' testcode '로 변경 하 여 네임 스페이스 이름 ' testcode '의 대/소문자를 수정 하십시오.

  - 네임 스페이스의 대/소문자를로 변경 합니다 `testCode` `TestCode` .

- [CA1709: 식별자](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)의 대/소문자를 올바르게 지정 해야 합니다. 이름: ' demo '로 변경 하 여 형식 이름 ' demo '의 대/소문자를 수정 하십시오.

  - 멤버의 이름을로 변경 `Demo` 합니다.

- [CA1709: 식별자](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)의 대/소문자를 올바르게 지정 해야 합니다. 이름 지정: 멤버 이름 ' i n s '의 대/소문자를 ' 항목 '으로 변경 하 여 수정 하십시오.

  - 멤버의 이름을로 변경 `Item` 합니다.

- [CA1710: 식별자에 올바른 접미사가 있어야](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)합니다. 이름: ' testcode. demo '의 이름을 ' Exception '으로 끝나야 합니다.

  - 클래스 및 생성자의 이름을로 변경 `DemoException` 합니다.

- [CA2210: 어셈블리](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)에는 강력한 이름 키를 사용 하 여 ' manageddemo ' 서명에 올바른 강력한 이름을 사용 해야 합니다.

  - **프로젝트** 메뉴에서 **manageddemo 속성**을 클릭 합니다.

       프로젝트 속성이 표시 됩니다.

       **서명**을 클릭 합니다.

       **어셈블리 서명** 확인란을 선택 합니다.

       **문자열 이름 키 파일 선택** 목록에서을 선택 **\<New…>** 합니다.

       **강력한 이름 키 만들기** 대화 상자가 나타납니다.

       **키 파일 이름**에 testkey를 입력 합니다.

       암호를 입력 한 다음 **확인**을 클릭 합니다.

       **파일** 메뉴에서 **선택한 항목 저장**을 클릭 한 다음 속성 페이지를 닫습니다.

       프로젝트를 다시 빌드합니다.

- [CA2237: iserializable 형식을 SerializableAttribute로 표시](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)합니다. 사용:이 형식이 iserializable을 구현 하므로 ' demo ' 형식에 [Serializable] 특성을 추가 합니다.

  - `[Serializable ()]`클래스에 특성을 추가 `demo` 합니다.

       프로젝트를 다시 빌드합니다.

  변경을 완료한 후 Class1.cs 파일은 다음과 같습니다.

```
//CodeAnalysisManagedDemo
//Class1.cs
using System;
using System.Runtime.Serialization;

namespace TestCode
{

    [Serializable()]
    public class DemoException : Exception
    {
        public DemoException () : base() { }
        public DemoException(String s) : base(s) { }
        public DemoException(String s, Exception e) : base(s, e) { }
        protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

        public static void Initialize(int size) { }
        protected static readonly int _item;
        public static int Item { get { return _item; } }
    }
}
```

## <a name="exclude-code-analysis-warnings"></a>코드 분석 경고 제외

#### <a name="to-exclude-code-defect-warnings"></a>코드 오류 경고를 제외 하려면

1. 나머지 경고 각각에 대해 다음을 수행합니다.

   1. 코드 분석 창에서 경고를 선택합니다.

   2. **작업**을 선택 하 고 **메시지 표시 안 함**을 선택한 다음 **프로젝트 비 표시 오류 (Suppression) 파일에서**를 선택 합니다.

      자세한 내용은 [방법: 메뉴 항목을 사용 하 여 경고 표시 안 함](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md) 을 참조 하세요.

2. 프로젝트를 다시 빌드합니다.

    프로젝트는 경고 또는 오류 없이 빌드됩니다.
