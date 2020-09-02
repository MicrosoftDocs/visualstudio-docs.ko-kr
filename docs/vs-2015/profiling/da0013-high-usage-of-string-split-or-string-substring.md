---
title: 'DA0013: String.Split 또는 String.Substring 사용률이 높습니다. | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.13
- vs.performance.rules.DAAvoidStringSubstr
- vs.performance.DA0013
- vs.performance.rules.DA0013
helpviewer_keywords:
- vs.performance.13
- vs.performance.rules.DA0013
ms.assetid: f501f423-bef9-4e08-bf96-c9ac9957e5a2
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d6ff05e7e8cc74eacb00b5ec8ff42bd48faaa12c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159197"
---
# <a name="da0013-high-usage-of-stringsplit-or-stringsubstring"></a>DA0013: String.Split 또는 String.Substring 사용률이 높습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

규칙 Id | DA0013 |  
| 범주 |. NET Framework 사용 지침 |  
| 프로 파일링 방법 | 샘플링 |  
| 메시지 | 문자열. Split 및 Substring 함수를 사용 하는 것을 줄여 보세요. |  
| 규칙 유형 | 경고 |  
  
## <a name="cause"></a>원인  
 System.String.Split 또는 System.String.Substring 메서드 호출이 프로파일링 데이터의 상당한 부분을 차지합니다. 문자열에 부분 문자열이 있는지 테스트할 경우 System.String.IndexOf 또는 System.String.IndexOfAny를 사용해 보세요.  
  
## <a name="rule-description"></a>규칙 설명  
 Split 메서드는 문자열 개체에서 사용되고 원래 문자열의 부분 문자열이 포함된 문자열의 새 배열을 반환합니다. 이 함수는 반환된 배열 개체의 메모리를 할당하고 함수가 찾은 각 배열 요소의 새 문자열 개체를 할당합니다. 마찬가지로 Substr 메서드는 문자열 개체에서 사용되고 요청된 부분 문자열과 일치하는 새 문자열을 반환합니다.  
  
 애플리케이션에서 메모리 할당 관리가 중요할 경우 String.Split 및 String.Substr 메서드의 대안을 사용해 보세요. 예를 들어 String 클래스의 새 인스턴스를 만들지 않고 IndexOf 또는 IndexOfAny 메서드를 사용하여 문자열 내에서 특정 부분 문자열을 찾을 수 있습니다.  
  
## <a name="how-to-investigate-a-warning"></a>경고를 조사하는 방법  
 오류 목록 창에서 메시지를 두 번 클릭하여 샘플링 프로필 데이터의 [함수 정보 뷰](../profiling/function-details-view.md)로 이동합니다. 호출 함수를 검사하여 System.String.Split 또는 System.String.Substr 메서드를 가장 빈번히 사용하는 프로그램의 섹션을 찾습니다. 가능할 경우 String 클래스의 새 인스턴스를 만들지 않고 IndexOf 또는 IndexOfAny 메서드를 사용하여 문자열 내에서 특정 부분 문자열을 찾으세요.
