---
title: 수동으로 레거시 코드 분석 실행 (.NET)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ca865b33d59f87453cafc337e1595c9d772b17a2
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808615"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>방법: 관리 코드에 대 한 레거시 코드 분석 수동으로 실행

코드 분석 도구는 소스 코드에서 가능한 오류에 대 한 정보를 제공 합니다. 코드 프로젝트의 각 빌드에서 자동으로 코드 분석을 실행할 수 있으며 코드 분석을 수동으로 실행할 수도 있습니다. 코드 분석이 실행 될 때 확인 되는 규칙은 프로젝트 속성 페이지의 코드 분석 페이지에서 지정 합니다. 자세한 내용은 [방법: 관리 코드 프로젝트에 대 한 코드 분석 구성](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)을 참조 하세요.

## <a name="to-run-code-analysis-manually"></a>수동으로 코드 분석을 실행 하려면

1. Visual Studio 2019 버전 16.5 이상에서 Visual Studio를 시작 하기 전에 명령 프롬프트에서 다음 명령을 실행 합니다.

```
set EnableLegacyCodeAnalysis = true
```

2. **솔루션 탐색기**에서 프로젝트를 클릭 합니다.

3. **분석** 메뉴에서 *프로젝트 이름* **에 대해 코드 분석 실행** 을 클릭 합니다.
