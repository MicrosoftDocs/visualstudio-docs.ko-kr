---
title: '방법: 관리 코드에 대해 레거시 코드 분석을 수동으로 실행합니다.'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d2693bcff8e83839b4171bae60b138c967f10e5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432086"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>방법: 관리 코드에 대해 레거시 코드 분석을 수동으로 실행합니다.
코드 분석 도구는 소스 코드의 가능한 결함에 대한 정보를 제공합니다. 코드 프로젝트의 각 빌드마다 코드 분석을 자동으로 실행할 수 있으며 코드 분석을 수동으로 실행할 수도 있습니다. 코드 분석을 실행할 때 검사되는 규칙은 프로젝트 속성 페이지의 코드 분석 페이지에 지정됩니다. 자세한 내용은 [관리 코드 프로젝트에 대한 코드 분석 구성 방법을](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)참조하십시오.

## <a name="to-run-code-analysis-manually"></a>코드 분석을 수동으로 실행하려면

1. Visual Studio 2019 버전 16.5 이상에 있는 경우 Visual Studio를 시작하기 전에 명령 프롬프트에 다음 명령을 실행합니다.

```
set EnableLegacyCodeAnalysis = true
```

2. **솔루션 탐색기에서**프로젝트를 클릭합니다.

3. **분석** 메뉴에서 *프로젝트 이름에*대한 코드 **분석 실행을** 클릭합니다.

