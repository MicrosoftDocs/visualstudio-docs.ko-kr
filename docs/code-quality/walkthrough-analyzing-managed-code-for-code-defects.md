---
title: 코드 오류에 대 한 관리 코드 분석 연습 | Microsoft Docs
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ab1e0b890d6241742770ed38ff61fc1c2c0ed2f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72535695"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>연습: 정적 코드 분석을 사용 하 여 코드 오류 찾기

이 연습에서는 레거시 코드 분석을 사용 하 여 코드 오류에 대 한 관리 되는 프로젝트를 분석 합니다.

이 문서에서는 .net 디자인 지침을 준수 하기 위해 레거시 분석을 사용 하 여 .NET 관리 코드 어셈블리를 분석 하는 과정을 단계별로 안내 합니다.

## <a name="create-a-class-library"></a>클래스 라이브러리 만들기

1. Visual Studio를 열고 **클래스 라이브러리 (.NET Framework)** 템플릿에서 새 프로젝트를 만듭니다.

1. 프로젝트 이름을 **CodeAnalysisManagedDemo**로 합니다.

1. 프로젝트를 만든 후 *Class1.cs* 파일을 엽니다.

1. Class1.cs의 기존 텍스트를 다음 코드로 바꿉니다.

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Class1.cs 파일을 저장 합니다.

## <a name="analyze-the-project-for-code-defects"></a>프로젝트에서 코드 오류를 분석 합니다.

1. **솔루션 탐색기**에서 CodeAnalysisManagedDemo 프로젝트를 선택 합니다.

2. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

   CodeAnalysisManagedDemo 속성 페이지가 표시 됩니다.

3. **코드 분석** 탭을 선택 합니다.

::: moniker range="vs-2017"

4. **빌드에 코드 분석 사용** 이 선택 되어 있는지 확인 합니다.

5. **이 규칙 집합 실행** 드롭다운 목록에서 **Microsoft 모든 규칙**을 선택 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

4. **이진 분석기** 섹션에서 **빌드 시 실행** 이 선택 되어 있는지 확인 합니다.

5. **활성 규칙** 드롭다운 목록에서 **Microsoft 모든 규칙**을 선택 합니다.

::: moniker-end

6. **파일** 메뉴에서 **선택한 항목 저장**을 클릭 한 다음 속성 페이지를 닫습니다.

7. **빌드** 메뉴에서 **CodeAnalysisManagedDemo 빌드**를 클릭 합니다.

    CodeAnalysisManagedDemo 프로젝트 빌드 경고는 **오류 목록** 및 **출력** 창에 표시 됩니다.

## <a name="correct-the-code-analysis-issues"></a>코드 분석 문제 해결

1. **보기** 메뉴에서 **오류 목록**를 선택 합니다.

    선택한 개발자 프로필에 따라 **보기** 메뉴에서 **다른 창** 을 가리킨 다음 **오류 목록**를 선택 해야 할 수 있습니다.

1. **솔루션 탐색기**에서 **모든 파일 표시**를 선택합니다.

1. 속성 노드를 확장 한 다음 *AssemblyInfo.cs* 파일을 엽니다.

1. 다음 팁을 사용 하 여 경고를 수정 하십시오.

   [CA1014: CLSCompliantAttribute를 사용 하 여 어셈블리 표시](../code-quality/ca1014.md): `[assembly: CLSCompliant(true)]` AssemblyInfo.cs 파일의 끝에 코드를 추가 합니다.

   [CA1032: 표준 예외 생성자 구현](../code-quality/ca1032.md): 클래스에 생성자를 추가 `public demo (String s) : base(s) { }` `demo` 합니다.

   [CA1032: 표준 예외 생성자 구현](../code-quality/ca1032.md): 클래스에 생성자를 추가 `public demo (String s, Exception e) : base(s, e) { }` `demo` 합니다.

   [CA1032: 표준 예외 생성자 구현](../code-quality/ca1032.md): `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` 클래스 데모에 생성자를 추가 합니다. 또한 `using` 에 대 한 문을 추가 해야 <xref:System.Runtime.Serialization?displayProperty=fullName> 합니다.

   [CA1032: 표준 예외 생성자 구현](../code-quality/ca1032.md): 클래스에 생성자를 추가 `public demo () : base() { }` `demo` 합니다.

   [CA1709: 식별자](../code-quality/ca1709.md)의 대/소문자를 올바르게 지정 해야 합니다. 네임 스페이스의 대/소문자를로 변경 합니다 `testCode` `TestCode` .

   [CA1709: 식별자](../code-quality/ca1709.md)의 대/소문자를 올바르게 지정 해야 합니다. 멤버의 `Demo` 이름을로 변경 합니다.

   [CA1709: 식별자](../code-quality/ca1709.md)의 대/소문자를 올바르게 지정 해야 합니다. 멤버의 `Item` 이름을로 변경 합니다.

   [CA1710: 식별자에 올바른 접미사가 있어야](../code-quality/ca1710.md)합니다. 클래스 및 생성자의 이름을로 변경 합니다 `DemoException` .

   [CA2237: ISerializable 형식을 SerializableAttribute로 표시](../code-quality/ca2237.md) `[Serializable ()]` 합니다. 특성을 클래스에 추가 `demo` 합니다.

   CA2210: 어셈블리에는 강력한 이름 키를 사용 하 여 ' CodeAnalysisManagedDemo ' 서명에 [올바른 강력한 이름을 사용 해야 합니다](../code-quality/ca2210.md).

   1. **프로젝트** 메뉴에서 **CodeAnalysisManagedDemo 속성**을 선택 합니다.

      프로젝트 속성이 표시 됩니다.

   1. **서명** 탭을 선택합니다.

   1. **어셈블리 서명** 확인란을 선택 합니다.

   1. **문자열 이름 키 파일 선택** 목록에서을 선택 **\<New>** 합니다.

      **강력한 이름 키 만들기** 대화 상자가 나타납니다.

   1. **키 파일 이름**에 **testkey**를 입력 합니다.

   1. 암호를 입력 한 다음 **확인**을 선택 합니다.

   1. **파일** 메뉴에서 **선택한 항목 저장**을 선택한 다음 속성 페이지를 닫습니다.

   모든 변경을 완료 한 후 Class1.cs 파일은 다음과 같습니다.

   ```csharp
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

1. 프로젝트를 다시 빌드합니다.

## <a name="exclude-code-analysis-warnings"></a>코드 분석 경고 제외

1. 나머지 경고 각각에 대해 다음을 수행합니다.

    1. **오류 목록**에서 경고를 선택 합니다.

    1. 오른쪽 클릭 메뉴 (상황에 맞는 메뉴)에서 비 **표시 표시 안 함 파일에서 표시 안 함**을 선택  >  **In Suppression File**합니다.

1. 프로젝트를 다시 빌드합니다.

     프로젝트는 경고 또는 오류 없이 빌드됩니다.

## <a name="see-also"></a>추가 정보

[관리 코드에 대한 코드 분석](../code-quality/code-analysis-for-managed-code-overview.md)
