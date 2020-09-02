---
title: 구조체 및 클래스에 주석 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 6db2202971facb0419db68c04835c8d5c848f528
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77271576"
---
# <a name="annotating-structs-and-classes"></a>구조체 및 클래스에 주석 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

고정 처럼 동작 하는 주석을 사용 하 여 구조체 및 클래스 멤버에 주석을 추가할 수 있습니다 .이는 바깥쪽 구조체를 매개 변수 또는 결과 값으로 포함 하는 함수 호출 또는 함수 시작/종료에서 true로 간주 됩니다.  
  
## <a name="struct-and-class-annotations"></a>구조체 및 클래스 주석  
  
- `_Field_range_(low, high)`  
  
     필드가의 범위 (포함)에 있는 경우 `low` `high`  `_Satisfies_(_Curr_ >= low && _Curr_ <= high)`적절 한 사전 또는 사후 조건을 사용 하 여 주석이 달린 개체에 적용 되는 것과 동일 합니다.  
  
- `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     로 지정 된 요소 (또는 바이트)에 쓰기 가능한 크기가 있는 필드 `size` 입니다.  
  
- `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     로 지정 된 요소 (또는 바이트) `size` 와 `count` 읽을 수 있는 요소 (바이트)의 쓰기 가능 크기를 갖는 필드입니다.  
  
- `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     에 지정 된 대로 읽을 수 있는 크기와 쓰기 가능한 크기의 요소 (또는 바이트)가 모두 있는 필드입니다 `size` .  
  
- `_Struct_size_bytes_(size)`  
  
     에 지정 된 대로 읽을 수 있는 크기와 쓰기 가능한 크기의 요소 (또는 바이트)가 모두 있는 필드입니다 `size` .  
  
     구조체 또는 클래스 선언에 적용 됩니다.  에서 지정 하는 바이트 수를 사용 하 여 해당 형식의 유효한 개체가 선언 된 형식 보다 클 수 있음을 나타냅니다 `size` .  예를 들면 다음과 같습니다.  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     형식의 매개 변수 버퍼 크기 (바이트)는 `pM` `MyStruct *` 다음과 같습니다.  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>관련 항목  
 [C/c + + 코드 오류를 줄이기 위해 SAL 주석 사용](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL 이해](../code-quality/understanding-sal.md)   
 [함수 매개 변수 및 반환 값에 주석 달기](../code-quality/annotating-function-parameters-and-return-values.md)   
 [함수 동작에 주석 달기](../code-quality/annotating-function-behavior.md)   
 [잠금 동작에 주석 달기](../code-quality/annotating-locking-behavior.md)   
 [주석이 적용 되는 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [내장 함수](../code-quality/intrinsic-functions.md)   
 [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)
