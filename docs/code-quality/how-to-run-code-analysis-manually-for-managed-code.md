---
title: '방법: 관리 코드에 대해 코드 분석을 수동으로 실행합니다.'
ms.date: 11/04/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5fdeb56a0c0f4c5904a00ec53d64dae87aa4e9a5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431386"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>방법: 관리 코드에 대해 코드 분석을 수동으로 실행합니다(Visual Studio 2019 버전 16.5 이상 필요)
기본적으로 .NET 컴파일러 플랫폼("Roslyn") 코드 분석기는 빌드 하는 동안뿐만 아니라 라이브 분석을 수행하여 입력할 때 C# 또는 Visual Basic 코드를 분석합니다. 따라서 일반적으로 코드 분석을 수동으로 트리거할 필요가 없습니다. 그러나 코드 분석을 수동으로 트리거할 수 있는 몇 가지 시나리오가 있습니다.

- 기본적으로 라이브 코드 분석은 Visual Studio의 열린 파일에 대해서만 분석기를 실행합니다. 그러나 특정 프로젝트 또는 솔루션의 모든 파일에 대한 코드 분석 경고를 보는 것이 좋습니다. 그렇다면 프로젝트 또는 솔루션에서 코드 분석을 한 번 트리거할 수 있습니다. 또는 연속 라이브 코드 분석을 사용하여 전체 솔루션에서 실행할 수 있습니다. 자세한 내용은 [관리 코드에 대한 라이브 코드 분석 범위를 구성하는 방법을](./configure-live-code-analysis-scope-managed-code.md)참조하십시오.
- 지속적인 실시간 분석 또는 빌드 시간 분석보다 주문형 코드 분석 실행 워크플로를 선호할 수 있습니다. 이 경우 라이브 분석 및/또는 빌드 중에 분석기 실행을 비활성화할 수 있습니다. 분석 비활성화에 대한 자세한 내용은 [소스 코드 분석을 사용하지 않도록 설정하는 방법을](disable-code-analysis.md)참조하십시오. 그런 다음 프로젝트 또는 솔루션에서 코드 분석을 한 번 수동으로 트리거할 수 있습니다. 

### <a name="run-code-analysis-manually"></a>수동으로 코드 분석 실행

1. **솔루션 탐색기에서**프로젝트를 클릭합니다.

2. **분석** 메뉴에서 *프로젝트 이름에*대한 코드 **분석 실행을** 클릭합니다.

코드 분석은 백그라운드에서 실행이 시작됩니다. 왼쪽 아래 모서리를 향한 Visual Studio 상태 표시줄에 **프로젝트> 대한 \<코드 분석 실행** 메시지가 표시됩니다. 코드 분석이 완료되면 상태 메시지가 **프로젝트>대해 \<완료된 코드 분석으로 **변경됩니다. 오류 목록은 모든 코드 분석 진단 과 함께 곧 새로 고쳐집니다.
