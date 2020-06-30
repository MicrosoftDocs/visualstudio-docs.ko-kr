---
title: VS 셸 배포
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8793312e0ed022fc7210508efdf20a81b293f0f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535852"
---
# <a name="vs-shell-deployment"></a>VS 셸 배포

격리 된 셸을 사용 하면 도메인별 언어와 상호 작용 하는 데 필요한 Visual Studio 기능과 해당 솔루션이 표시 되는 방법을 결정할 수 있습니다. Visual Studio의 격리 된 셸에 대 한 자세한 내용은 [격리 된 셸 사용자 지정](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell)을 참조 하세요.

Visual Studio Shell을 배포 대상으로 설정 하려면 다음을 수행 합니다.

1. **Dslpackage** 프로젝트에서 **source.extension.tt**를 엽니다.

2. 삽입 아래에서 `<SupportedProducts>` 다음을 수행 합니다.

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   *MyIsolatedShell* 을 격리 된 셸 패키지의 이름으로 바꿉니다.
