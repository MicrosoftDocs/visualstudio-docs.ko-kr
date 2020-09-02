---
title: 디버거의 식 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VBScript
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3999737a2fad04c9b513722ae11608574a72c410
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315033"
---
# <a name="expressions-in-the-debugger"></a>디버거에서 사용하는 식
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 디버거에는 **간략한 조사식** 대화 상자, **조사식** 창 또는 **직접 실행** 창에 식을 입력할 때 사용되는 식 계산기가 포함되어 있습니다. 식 계산기는 **중단점** 창과 디버거의 여러 가지 다른 부분에서도 사용됩니다.  
  
 다음 섹션에서는 다양한 언어의 식에 대한 세부 정보를 제공합니다.  
  
## <a name="f-expressions-are-not-supported"></a>F# 식은 지원되지 않습니다.  
 F# 식은 인식할 수 없습니다. F# 코드를 디버그하는 경우 디버거 창 또는 대화 상자에 식을 입력하기 전에 식을 C# 구문으로 변환해야 합니다. F#에서 C#으로 식을 변환하는 경우 C#은 `==` 연산자를 사용하여 같은지 테스트하는 반면 F#은 단일 `=`를 사용한다는 것에 유의하세요.  
  
## <a name="c-expressions"></a>C++ 식  
 C++에서 식과 함께 컨텍스트 연산자를 사용하는 방법에 대한 자세한 내용은 [Context Operator (C++)](../debugger/context-operator-cpp.md)를 참조하세요.  
  
### <a name="unsupported-expressions-in-c"></a>C++에서 지원되지 않는 식  
  
#### <a name="constructors-destructors-and-conversions"></a>생성자, 소멸자 및 변환  
 명시적 또는 암시적으로 개체에 대한 생성자나 소멸자를 호출할 수 없습니다. 예를 들어 다음 식을 사용하여 명시적으로 생성자를 호출하면 오류 메시지가 나타납니다.  
  
```cpp  
my_date( 2, 3, 1985 )  
```  
  
 클래스로 변환하는 경우에는 변환 함수를 호출할 수 없습니다. 이러한 변환에는 개체 생성이 포함됩니다. 예를 들어 `myFraction` 이 변환 함수 연산자 `CFraction`를 정의하는 `FixedPoint`의 인스턴스인 경우에 다음 식을 사용하면 오류가 발생합니다.  
  
```cpp  
(FixedPoint)myFraction  
```  
  
 new 또는 delete 연산자를 호출할 수 없습니다. 예를 들어 다음 식은 지원되지 않습니다.  
  
```cpp  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>전처리기 매크로  
 전처리기 매크로는 디버거에서 지원되지 않습니다. 예를 들어 `VALUE` 상수가 `#define VALUE 3`으로 선언된 경우 `VALUE` 조사식 **창에서** 를 사용할 수 없습니다. 이 제한을 방지하려면 가능한 경우 항상 `#define`을 열거형 및 함수로 바꿔야 합니다.  
  
### <a name="using-namespace-declarations"></a>네임스페이스 선언 사용  
 `using namespace` 선언을 사용할 수 없습니다.  현재 네임스페이스 외부에서 유형 이름 또는 변수에 액세스하려면 정규화된 이름을 사용해야 합니다.  
  
### <a name="anonymous-namespaces"></a>익명 네임스페이스  
 익명 네임스페이스는 지원되지 않습니다. 다음 코드가 있는 경우 조사식 창에 `test` 를 추가할 수 없습니다.  
  
```cpp  
namespace mars   
{   
    namespace  
    {  
        int test = 0;   
    }   
}   
int main()   
{   
    // Adding a watch on test does not work.   
    mars::test++;   
    return 0;   
}  
  
```  
  
### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> 디버거 내장 함수를 사용하여 상태 유지  
 디버거 내장 함수는 애플리케이션의 상태를 변경하지 않고 식에서 특정 C/C++ 함수를 호출하는 방법을 제공합니다.  
  
 디버거 내장 함수의 특징은 다음과 같습니다.  
  
- 안전이 보장됩니다. 디버거 내장 함수를 실행하는 경우 디버깅 중인 프로세스가 손상되지 않습니다.  
  
- 모든 식에서 허용됩니다. 파생 작업과 함수 실행이 허용되지 않는 시나리오에서도 허용됩니다.  
  
- 미니덤프 디버깅과 같이 일반 함수 호출이 가능하지 않은 시나리오에서 작동합니다.  
  
  디버거 내장 함수를 사용하면 식 계산도 보다 편리해질 수 있습니다. 예를 들어 `strncmp(str, “asd”)` 는 `str[0] == ‘a’ && str[1] == ‘s’ && str[2] == ‘d’`보다 중단점 조건에서 작성하기가 훨씬 쉽습니다. )  
  
|영역|내장 함수|  
|----------|-------------------------|  
|**문자열 길이**|strlen, wcslen, strnlen, wcsnlen|  
|**문자열 비교**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**문자열 검색**|strchr, wcschr, strstr, wcsstr|  
|**Win32**|GetLastError(), TlsGetValue()|  
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> 이러한 함수를 사용하려면 디버깅 중인 프로세스가 Windows 8에서 실행되어야 합니다. Windows 8 디바이스에서 생성된 덤프 파일을 디버깅하려면 Visual Studio 컴퓨터에서 Windows 8이 실행되어야 합니다. 그러나 Windows 8 디바이스를 원격으로 디버그하는 경우에는 Visual Studio 컴퓨터에서 Windows 7이 실행될 수 있습니다.|  
|**기타**|__log2<br /><br /> 가장 가까운 낮은 정수로 반올림된 밑이 2인 지정된 정수의 로그 값을 반환합니다.|  
  
## <a name="ccli---unsupported-expressions"></a>C++/CLI - 지원되지 않는 식  
  
- 포인터와 관련된 캐스트 또는 사용자 정의 캐스트는 지원되지 않습니다.  
  
- 개체 비교 및 할당은 지원되지 않습니다.  
  
- 오버로드된 연산자 및 오버로드된 함수는 지원되지 않습니다.  
  
- boxing 및 unboxing은 지원되지 않습니다.  
  
- `Sizeof` 연산자는 지원되지 않습니다.  
  
## <a name="c---unsupported-expressions"></a>C# - 지원되지 않는 식  
  
### <a name="dynamic-objects"></a>동적 개체  
 디버거 식에서 정적으로 형식화된 변수를 동적으로 사용할 수 있습니다. <xref:System.Dynamic.IDynamicMetaObjectProvider>를 구현하는 개체가 조사식 창에서 평가될 때 동적 뷰 노드가 추가됩니다. 동적 뷰 노드에서는 개체 멤버가 표시되지만 멤버의 값을 편집할 수는 없습니다.  
  
 동적 개체의 다음 기능은 지원되지 않습니다.  
  
- 복합 연산자 `+=`, `-=`, `%=`, `/=`및 `*=`  
  
- 숫자 캐스트 및 형식 인수 캐스트를 비롯한 다양한 캐스트  
  
- 세 개 이상의 인수가 있는 메서드 호출  
  
- 세 개 이상의 인수가 있는 속성 getter  
  
- 여러 인수가 있는 속성 setter  
  
- 인덱서에 할당  
  
- 부울 연산자 `&&` 및 `||`  
  
### <a name="anonymous-methods"></a>무명 메서드  
 새 무명 메서드 만들기는 지원되지 않습니다.  
  
## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - 지원되지 않는 식  
  
### <a name="dynamic-objects"></a>동적 개체  
 디버거 식에서 정적으로 형식화된 변수를 동적으로 사용할 수 있습니다. <xref:System.Dynamic.IDynamicMetaObjectProvider>를 구현하는 개체가 조사식 창에서 평가될 때 동적 뷰 노드가 추가됩니다. 동적 뷰 노드에서는 개체 멤버가 표시되지만 멤버의 값을 편집할 수는 없습니다.  
  
 동적 개체의 다음 기능은 지원되지 않습니다.  
  
- 복합 연산자 `+=`, `-=`, `%=`, `/=`및 `*=`  
  
- 숫자 캐스트 및 형식 인수 캐스트를 비롯한 다양한 캐스트  
  
- 세 개 이상의 인수가 있는 메서드 호출  
  
- 세 개 이상의 인수가 있는 속성 getter  
  
- 여러 인수가 있는 속성 setter  
  
- 인덱서에 할당  
  
- 부울 연산자 `&&` 및 `||`  
  
### <a name="local-constants"></a>지역 상수  
 지역 상수는 지원되지 않습니다.  
  
### <a name="import-aliases"></a>Import 별칭  
 Import 별칭은 지원되지 않습니다.  
  
### <a name="variable-declarations"></a>변수 선언  
 디버거 창에서는 새 변수를 명시적으로 선언할 수 없습니다. 그러나 **직접 실행** 창 내에서 새 암시적 변수를 할당할 수 있습니다. 이러한 암시적 변수의 범위는 디버그 세션으로 제한되고 디버거 외부에서 액세스할 수 없습니다. 예를 들어 `o = 5` 문은 새 변수 `o` 를 암시적으로 만들고 이 변수에 5를 값으로 할당합니다. 디버거에서 형식을 유추할 수 없는 경우 이와 같은 암시적 변수의 형식은 **Object** 입니다.  
  
### <a name="unsupported-keywords"></a>지원되지 않는 키워드  
  
- `AddressOf`  
  
- `End`  
  
- `Error`  
  
- `Exit`  
  
- `Goto`  
  
- `On Error`  
  
- `Resume`  
  
- `Return`  
  
- `Select/Case`  
  
- `Stop`  
  
- `SyncLock`  
  
- `Throw`  
  
- `Try/Catch/Finally`  
  
- `With`  
  
- `End Sub` 또는 `Module`과 같은 네임스페이스 또는 모듈 수준 키워드  
  
## <a name="see-also"></a>관련 항목  
 [C + +의 형식 지정자](../debugger/format-specifiers-in-cpp.md)   
 [Context 연산자 (c + +)](../debugger/context-operator-cpp.md)   
 [C의 형식 지정자 #](../debugger/format-specifiers-in-csharp.md)   
 [의사 변수](../debugger/pseudovariables.md)
