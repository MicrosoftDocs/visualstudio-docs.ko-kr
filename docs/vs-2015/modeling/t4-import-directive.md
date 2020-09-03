---
title: T4 Import 지시문 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4a931ca05f8b12175deded8b316d0177d8f8c74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661814"
---
# <a name="t4-import-directive"></a>T4 Import 지시문
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] T4 텍스트 템플릿의 코드 블록에서 `import` 지시문을 사용하면 정규화된 이름을 제공하지 않고 다른 네임스페이스의 요소를 참조할 수 있습니다. 이 지시문은 C#의 `using` 또는 `imports`의 [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)]에 해당합니다.

 T4 텍스트 템플릿 작성에 대 한 일반적인 개요는 [T4 텍스트 템플릿 작성](../modeling/writing-a-t4-text-template.md)을 참조 하세요.

## <a name="using-the-import-directive"></a>Import 지시문 사용

```
<#@ import namespace="namespace" #>
```

 이 예제에서는 다음과 같이 템플릿 코드에서 System.IO의 멤버에 대한 명시적 네임스페이스를 생략할 수 있습니다.

```
<#@ import namespace="System.IO" #>
<#
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File
#>
The file contains: <#=  fileContent #>
```

## <a name="standard-imports"></a>표준 가져오기
 다음 네임스페이스를 자동으로 가져오므로 해당 네임스페이스에 대한 import 지시문을 작성할 필요가 없습니다.

- `System`

  또한 사용자 지정 지시문을 사용하는 경우 지시문 프로세서에서 일부 네임스페이스를 자동으로 가져올 수 있습니다.

  예를 들어 DSL(도메인별 언어)을 위한 템플릿을 작성하는 경우 다음 네임스페이스에 대한 import 지시문을 작성할 필요가 없습니다.

- `Microsoft.VisualStudio.Modeling`

- DSL의 네임스페이스

## <a name="see-also"></a>관련 항목
 [T4 Assembly 지시문](../modeling/t4-assembly-directive.md)
