---
title: 이스케이프할 특수 문자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: beeed84db240ecf57ca18dd9aef08622f14b06fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161348"
---
# <a name="special-characters-to-escape"></a>이스케이프할 특수 문자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

특수 문자는 사용되는 컨텍스트에서 특별한 의미가 있는 경우에만 이스케이프해야 합니다. 예를 들어 별표(*)는 항목 정의의 "Include" 및 "Exclude" 특성이나 <xref:Microsoft.Build.Tasks.CreateItem> 호출에서만 특수 문자이며 다른 모든 경우에는 리터럴 별표로 처리됩니다. 프로젝트 파일의 모든 위치에서 별표를 이스케이프해야 하는 것은 아니지만 이스케이프해도 문제는 발생하지 않습니다.  
  
 특수 문자 대신%*xx* 표기법을 사용 합니다. 여기서 *xx* 는 ASCII 문자의 16 진수 값을 나타냅니다. 예를 들어 별표(*)를 리터럴 문자로 사용하려면 `%2A` 값을 사용합니다.  
  
 이스케이프할 수 있는 특수 문자의 전체 목록은 다음과 같습니다.  
  
|문자|설명|  
|---------------|-----------------|  
|%|메타데이터를 참조하는 데 사용되는 퍼센트 기호입니다.|  
|$|속성을 참조하는 데 사용되는 달러 기호입니다.|  
|@|항목 목록을 참조하는 데 사용되는 @ 기호입니다.|  
|(|목록에 사용되는 여는 괄호입니다.|  
|)|목록에 사용되는 닫는 괄호입니다.|  
|`|조건 및 기타 식에 사용되는 아포스트로피(눈금 표시)입니다.|  
|;|목록 구분 기호인 세미콜론입니다.|  
|?|항목의 Include/Exclude 섹션에서 파일 사양을 설명하는 와일드카드 문자인 물음표입니다.|  
|*|항목의 Include/Exclude 섹션에서 파일 사양을 설명하는 와일드카드 문자인 별표입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [방법: MSBuild의 이스케이프 특수 문자](../msbuild/how-to-escape-special-characters-in-msbuild.md)   
 [MSBuild 참조](../msbuild/msbuild-reference.md)
