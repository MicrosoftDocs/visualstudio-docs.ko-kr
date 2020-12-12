---
title: VS 셸 배포
description: 격리 된 셸에서 DSL을 사용 하 여 상호 작용 하는 데 필요한 Visual Studio 기능 및 해당 솔루션이 표시 되는 방법을 결정 하는 방법을 알아보세요.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94cffbf5ea1f7ac3c437a4c22f27f881d5493e79
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361263"
---
# <a name="vs-shell-deployment"></a>VS 셸 배포

격리 된 셸을 사용 하면 도메인별 언어와 상호 작용 하는 데 필요한 Visual Studio 기능과 해당 솔루션이 표시 되는 방법을 결정할 수 있습니다. Visual Studio의 격리 된 셸에 대 한 자세한 내용은 [격리 된 셸 사용자 지정](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)을 참조 하세요.

Visual Studio Shell을 배포 대상으로 설정 하려면 다음을 수행 합니다.

1. **Dslpackage** 프로젝트에서 **source.extension.tt** 를 엽니다.

2. 삽입 아래에서 `<SupportedProducts>` 다음을 수행 합니다.

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   *MyIsolatedShell* 을 격리 된 셸 패키지의 이름으로 바꿉니다.