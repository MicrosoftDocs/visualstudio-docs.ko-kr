---
title: VS 셸 배포
description: 격리된 셸을 사용하여 DSL과 상호 작용하는 데 필요한 Visual Studio 기능과 해당 솔루션이 표시되는 방식을 결정하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 946cbf99fa7836fa8d7ec5aa1d921e7cda93bf46
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388310"
---
# <a name="vs-shell-deployment"></a>VS 셸 배포

격리된 셸을 사용하면 도메인 특정 언어와 상호 작용하는 데 필요한 Visual Studio 기능과 해당 솔루션이 표시되는 방식을 확인할 수 있습니다. Visual Studio 격리 셸에 대한 자세한 내용은 [격리 셸 사용자 지정을 참조하세요.](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

Visual Studio 셸을 배포 대상으로 설정하려면 다음을 수행합니다.

1. **DslPackage** 프로젝트에서 **source.extension.tt** 엽니다.

2. `<SupportedProducts>`삽입에서 다음을 수행합니다.

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   *MyIsolatedShell을* 격리된 셸 패키지의 이름으로 바꿉다.