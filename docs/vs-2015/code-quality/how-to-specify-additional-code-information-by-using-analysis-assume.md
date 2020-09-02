---
title: '방법: __analysis_assume를 사용 하 여 추가 코드 정보 지정 Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- __analysis_assume
helpviewer_keywords:
- __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: f2f18c9284ec96de7a7b8663aff485962d194282
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277981"
---
# <a name="how-to-specify-additional-code-information-by-using-__analysis_assume"></a>How to: Using __analysis_assume 사용하여 추가 코드 정보 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

분석 프로세스에 도움이 되는 C/c + + 코드의 코드 분석 도구에 대 한 힌트를 제공 하 고 경고를 줄일 수 있습니다. 추가 정보를 제공 하려면 다음 함수를 사용 합니다.  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr` -true로 평가 되는 것으로 간주 되는 식입니다.  
  
 코드 분석 도구는 함수가 표시 되는 지점에서 식이 나타내는 조건이 true 인 것으로 가정 합니다. 예를 들어 변수에 대 한 할당을 통해 식이 변경 될 때까지 true로 유지 됩니다.  
  
> [!NOTE]
> `__analysis_assume` 코드 최적화에 영향을 주지 않습니다. 코드 분석 도구 외부에서 `__analysis_assume` 는 no op로 정의 됩니다.  
  
## <a name="example"></a>예  
 다음 코드에서는를 사용 하 여 `__analysis_assume` 코드 분석 경고 [C6388](../code-quality/c6388.md)을 수정 합니다.  
  
```  
#include<windows.h>  
#include<codeanalysis\sourceannotations.h>  
  
using namespace vc_attributes;  
  
// calls free and sets ch to null  
void FreeAndNull(char* ch);  
  
//requires pc to be null  
void f([Pre(Null=Yes)] char* pc);  
  
void test( )  
{  
  char *pc = (char*)malloc(5);  
  FreeAndNull(pc);  
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [__assume](https://msdn.microsoft.com/library/d8565123-b132-44b1-8235-5a8c8bff85a7)
