---
title: '방법: MSBuild의 이스케이프 특수 문자 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94fc8d858e2db9bd1e00bb8770cf52672a900ab0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178352"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>방법: MSBuild의 이스케이프 특수 문자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트 파일에서 특정 문자는 특수한 의미로 사용됩니다. 이러한 문자의 예로는 세미콜론(;) 및 별표(*)를 들 수 있습니다. 이러한 특수 문자의 전체 목록은 [MSBuild 특수 문자](../msbuild/msbuild-special-characters.md)를 참조 하세요.  
  
 프로젝트 파일에서 이러한 특수 문자를 리터럴로 사용 하려면%*xx*구문을 사용 하 여 지정 해야 합니다. 여기서 *XX* 는 문자의 ASCII 16 진수 값을 나타냅니다.  
  
## <a name="msbuild-special-characters"></a>MSBuild 특수 문자  
 항목 목록의 `Include` 특성에서 특수 문자가 사용되는 하나의 예가 있습니다. 예를 들어 다음 항목 목록은 두 개의 항목, `MyFile.cs` 및 `MyClass.cs`를 선언합니다.  
  
```  
<Compile Include="MyFile.cs;MyClass.cs"/>  
```  
  
 이름에 세미콜론이 포함 된 항목을 선언 하려면%*xx* 구문을 사용 하 여 세미콜론을 이스케이프 하 고 별도의 두 항목을 선언 하지 않아야 합니다 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . 예를 들어 다음 항목은 세미콜론을 이스케이프하고 `MyFile.cs;MyClass.cs`라는 하나의 항목을 선언합니다.  
  
```  
<Compile Include="MyFile.cs%3BMyClass.cs"/>  
```  
  
#### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>MSBuild 특수 문자를 리터럴 문자로 사용하려면  
  
- 특수 문자 대신%*xx* 표기법을 사용 합니다. 여기서 *xx* 는 ASCII 문자의 16 진수 값을 나타냅니다. 예를 들어 별표(*)를 리터럴 문자로 사용하려면 `%2A` 값을 사용합니다.  
  
## <a name="see-also"></a>관련 항목  
 [MSBuild 개념](../msbuild/msbuild-concepts.md)   
 [MSBuild](msbuild.md) [항목](../msbuild/msbuild-items.md)
