---
title: VS 셸 배포
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ca497244a806324d9d2315fa1b1b89404838ff3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445001"
---
# <a name="vs-shell-deployment"></a>VS 셸 배포

격리된 셸을 사용하면 도메인 별 언어와 상호 작용하는 데 필요한 Visual Studio 기능과 해당 솔루션이 표시되는 방식을 결정할 수 있습니다. Visual Studio 격리셸에 대한 자세한 내용은 [격리셸 사용자 지정을](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell)참조하십시오.

Visual Studio 셸을 배포 대상으로 설정하려면 다음을 수행하십시오.

1. **DslPackage** 프로젝트에서 **source.extension.tt.**

2. 삽입 `<SupportedProducts>` 아래:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   *MyIsolatedShell을* 격리된 셸 패키지의 이름으로 바꿉니다.
