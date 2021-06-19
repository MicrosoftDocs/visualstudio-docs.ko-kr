---
title: T4 CleanUpBehavior 지시문
description: CleanUpBehavior 지시문 및 텍스트 템플릿을 처리한 후 appDomain을 삭제하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 078b688c238bea47e4ab38b3302708bf5e5189cf
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386347"
---
# <a name="t4-cleanupbehavior-directive"></a>T4 CleanUpBehavior 지시문

텍스트 템플릿을 처리한 후 appDomain을 삭제하려면 다음 줄을 포함하십시오.

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

호스트 프로세스와 별개인 appDomain에서 텍스트 템플릿이 처리됩니다. 대부분의 경우 하나의 텍스트 템플릿이 처리되면 다음 템플릿을 처리할 때 appDomain이 다시 사용됩니다. 그러나 CleanupBehavior를 지정하는 경우 appDomain이 삭제되고 다음 템플릿이 새 appDomain에서 처리됩니다.

이렇게 하면 텍스트 처리 속도가 느려지지만, 리소스가 삭제되었는지 확인하는 데에는 유용할 수 있습니다.

이 지시문은 Visual Studio 호스트에서만 작동합니다.
