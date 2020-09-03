---
title: MSBuild 조건 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71bb48290d0eb64f91b918d22624755c2edb6153
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74303129"
---
# <a name="msbuild-conditions"></a>MSBuild 조건
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]는 `Condition` 특성이 허용될 때마다 적용할 수 있는 특정 조건 집합을 지원합니다. 다음 표에서는 이러한 조건에 대해 설명합니다.  
  
|조건|설명|  
|---------------|-----------------|  
|'`stringA`' == '`stringB`'|`stringA`가 `stringB`와 같으면 `true`로 평가됩니다.<br /><br /> 예를 들어:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> 간단한 영숫자 문자열 또는 부울 값에는 작은따옴표가 필요하지 않습니다. 그러나 빈 값에는 작은따옴표가 필요합니다.|  
|'`stringA`' != '`stringB`'|`stringA`가 `stringB`와 같지 않으면 `true`로 평가됩니다.<br /><br /> 예를 들어:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> 간단한 영숫자 문자열 또는 부울 값에는 작은따옴표가 필요하지 않습니다. 그러나 빈 값에는 작은따옴표가 필요합니다.|  
|\<, >, \<=, >=|피연산자의 숫자 값을 평가합니다. 관계형 평가가 true이면 `true`를 반환합니다. 피연산자는 10진수 또는 16진수 숫자로 평가되어야 합니다. 16진수는 "0x"로 시작해야 합니다. **참고:**  XML에서는 `<` 및 `>` 문자를 이스케이프해야 합니다. `<` 기호는 `<`로 표시됩니다. `>` 기호는 `>`로 표시됩니다.|  
|Exists('`stringA`')|이름이 `stringA`인 파일이나 폴더가 있으면 `true`로 평가됩니다.<br /><br /> 예를 들어:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> 간단한 영숫자 문자열 또는 부울 값에는 작은따옴표가 필요하지 않습니다. 그러나 빈 값에는 작은따옴표가 필요합니다.|  
|HasTrailingSlash('`stringA`')|지정한 문자열에 후행 백슬래시(\\) 또는 슬래시(/) 문자가 있는 경우 `true`로 평가됩니다.<br /><br /> 예를 들어:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> 간단한 영숫자 문자열 또는 부울 값에는 작은따옴표가 필요하지 않습니다. 그러나 빈 값에는 작은따옴표가 필요합니다.|  
|!|피연산자가 `false`로 평가되면 `true`로 평가됩니다.|  
|그리고|피연산자가 `true`로 평가되면 `true`로 평가됩니다.|  
|또는|피연산자 중 하나 이상이 `true`로 평가되면 `true`로 평가됩니다.|  
|()|내부에 포함된 식이 `true`로 평가되면 `true`로 평가되는 그룹화 메커니즘입니다.|  
|$if$ ( %expression% ), $else$, $endif$|지정한 `%expression%`이 전달된 사용자 지정 템플릿 매개 변수의 문자열 값과 일치하는지를 확인합니다. `$if$` 조건이 `true`로 평가되면 해당 문이 실행되고 그렇지 않으면 `$else$` 조건이 확인됩니다. `$else$` 조건이 `true`이면 해당 문이 실행되고 그렇지 않으면 `$endif$` 조건이 식 평가를 종료합니다.<br /><br /> 사용 예제는 [Visual Studio 프로젝트/항목 템플릿 매개 변수 논리](https://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic)를 참조 하세요.|  
  
## <a name="see-also"></a>관련 항목  
 [MSBuild 참조](../msbuild/msbuild-reference.md)   
 [조건부 구문](../msbuild/msbuild-conditional-constructs.md)   
 [연습: 처음부터 새로 MSBuild 프로젝트 파일 만들기](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)
