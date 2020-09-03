---
title: Context 연산자 (c + +) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6351dd9db7e6f8f29bdd15f376f84511c64bfe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161533"
---
# <a name="context-operator-c"></a>컨텍스트 연산자(C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++에서 컨텍스트 연산자를 사용하여 중단점 위치, 변수 이름 또는 식을 한정할 수 있습니다. 컨텍스트 연산자는 로컬 이름에 의해 숨겨진 외부 범위에서 이름을 지정하는 데 유용합니다.  
  
## <a name="syntax"></a><a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> 구문  
 컨텍스트를 지정하는 방법에는 다음 두 가지가 있습니다.  
  
1. {,,[*모듈*] } *식*  
  
     중괄호에는 쉼표 두 개와 모듈(실행 파일 또는 DLL) 이름 또는 전체 경로가 포함되어야 합니다.  
  
     예를 들어 EXAMPLE.dll의 `SomeFunction` 함수에 중단점을 설정하려는 경우는 다음과 같습니다.  
  
    ```cpp  
    {,,EXAMPLE.dll}SomeFunction  
    ```  
  
2. *모듈*!*식*  
  
    ```cpp  
    EXAMPLE.dll!SomeFunction  
    ```  
  
- *모듈* 은 모듈의 이름입니다. 이름이 같은 여러 모듈을 구분하기 위해 전체 경로를 사용할 수 있습니다.  
  
   *모듈* 경로에 쉼표, 공백 또는 중괄호가 포함되어 있으면 컨텍스트 파서가 문자열을 적절하게 인식할 수 있도록 경로에 큰따옴표를 사용해야 합니다. 작은따옴표는 Windows 파일 이름의 일부로 간주되므로 큰따옴표를 사용해야 합니다. 예를 들면 다음과 같습니다.  
  
  ```cpp  
  {,,"a long, long, library name.dll"} g_Var  
  ```  
  
- *식* 은 *모듈*의 함수 이름, 변수 이름 또는 포인터 주소와 같은 올바른 대상으로 확인되는 모든 유효한 C++ 식입니다.  
  
  식 계산기는 식에서 기호가 나오면 다음과 같은 순서로 기호를 검색합니다.  
  
1. 현재 블록(중괄호에 포함된 일련의 문)에서 시작하여 바깥쪽 블록의 외부로 계속되는 바깥쪽 어휘 범위. 현재 블록은 현재 위치(명령 포인터 주소)가 포함된 코드입니다.  
  
2. 함수 범위. 현재 함수입니다.  
  
3. 현재 위치가 C++ 멤버 함수 내부인 경우 클래스 범위. 클래스 범위에는 모든 기본 클래스가 포함됩니다. 식 계산기는 일반 우위 규칙을 사용합니다.  
  
4. 현재 모듈의 전역 기호  
  
5. 현재 프로그램의 공용 기호
