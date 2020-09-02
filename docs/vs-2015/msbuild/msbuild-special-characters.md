---
title: MSBuild 특수 문자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- escape characters
- escape
- MSBuild Escape Characters
ms.assetid: 545e6a59-1093-4514-935e-78679a46fb3c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a54f446cb82b3181ee057d4887b37940868a5920
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150758"
---
# <a name="msbuild-special-characters"></a>MSBuild 특수 문자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 특정 컨텍스트에서 특별한 용도로 사용할 일부 문자를 예약합니다. 예약된 컨텍스트에서 문자 그대로 사용하려는 경우 이러한 문자를 이스케이프 처리해야 합니다. 예를 들어 별표는 항목 정의의 `Include` 및 `Exclude` 특성 및 `CreateItem`에 대한 호출에서만 특별한 의미를 가집니다. 별표를 해당 컨텍스트 중 하나에서 별표로 표시하려면 이스케이프 처리해야 합니다. 모든 다른 컨텍스트에서 별표를 표시하려는 곳에 입력합니다.  
  
 특수 문자를 이스케이프 처리하려면 %*xx* 구문을 사용합니다. 여기서 *xx*는 문자의 ASCII 16진수 값을 나타냅니다. 자세한 내용은 [방법: MSBuild의 이스케이프 특수 문자](../msbuild/how-to-escape-special-characters-in-msbuild.md)를 참조하세요.  
  
## <a name="special-characters"></a>특수 문자  
 다음 표에서는 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 특수 문자를 나열합니다.  
  
|**문자**|**ASCII**|**예약 사용량**|  
|-------------------|---------------|------------------------|  
|%|%25|메타데이터 참조|  
|$|%24|속성 참조|  
|@|%40|항목 목록 참조|  
|'|%27|조건 및 기타 식|  
|;|%3B|목록 구분 기호|  
|?|%3F|`Include` 및 `Exclude` 특성의 파일 이름에 대한 와일드 카드 문자|  
|*|%2A|`Include` 및 `Exclude` 특성의 파일 이름에서 사용할 와일드 카드 문자|  
  
## <a name="see-also"></a>관련 항목  
 [고급 개념](../msbuild/msbuild-advanced-concepts.md)   
 [항목](../msbuild/msbuild-items.md)
