---
title: 폭포수형 설정 | Microsoft IntelliTest 개발자 테스트 도구
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 95a2029cee1fd13241aba727f671a164d7272543
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591582"
---
# <a name="settings-waterfall"></a>폭포수형 설정

폭포수형 설정의 개념은 사용자가 **어셈블리**, **설비** 및 **탐색** 수준에서 설정을 지정할 수 있음을 의미합니다.

* 어셈블리 - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* 설비 - [PexClass](attribute-glossary.md#pexclass)
* 탐색 - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

**어셈블리** 수준에서 지정된 설정은 해당 어셈블리 아래 모든 설비 및 탐색에 영향을 줍니다. **설비** 수준에서 지정된 설정은 해당 설비 아래 모든 탐색에 영향을 줍니다. 자식 설정 우선&mdash;설정이 **어셈블리** 및 **설비** 수준에서 지정된 경우 **설비** 설정이 사용됩니다.

일부 설정은 **어셈블리** 수준 또는 **설비** 수준에만 관련됩니다.

**예제**

```csharp
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>피드백이 있나요?

아이디어와 기능 요청을 [개발자 커뮤니티](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)에 게시하세요.
