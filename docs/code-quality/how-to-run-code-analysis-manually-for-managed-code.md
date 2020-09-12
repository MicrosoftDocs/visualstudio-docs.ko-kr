---
title: .NET 용으로 코드 분석을 수동으로 실행 하는 방법
ms.date: 09/02/2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c24fa8e835dced8332aa4c50870d6251bdd43e63
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037161"
---
# <a name="run-code-analysis-manually-for-net"></a>.NET에 대해 수동으로 코드 분석 실행
기본적으로 .NET Compiler Platform ("Roslyn") 분석기는 실시간 분석을 수행 하 고 빌드 중에도 입력할 때 c # 또는 Visual Basic 코드를 분석 합니다. 따라서 일반적으로 코드 분석을 수동으로 트리거할 필요가 없습니다. 그러나 코드 분석을 수동으로 트리거할 수 있는 몇 가지 시나리오가 있습니다.

> [!NOTE]
> 수동으로 코드 분석을 실행 하려면 Visual Studio 2019 버전 16.5 이상이 필요 합니다.

- 기본적으로 라이브 코드 분석은 Visual Studio에서 열려 있는 파일에 대해서만 분석기를 실행 합니다. 그러나 특정 프로젝트 또는 솔루션의 모든 파일에 대 한 코드 분석 경고를 보는 데 관심이 있을 수 있습니다. 이 경우 프로젝트 또는 솔루션에서 코드 분석을 한 번 트리거할 수 있습니다. 또는 연속 라이브 코드 분석을 사용 하 여 전체 솔루션에서 실행할 수 있습니다. 자세한 내용은 [방법: 관리 코드에 대한 실시간 코드 분석 범위를 구성합니다](./configure-live-code-analysis-scope-managed-code.md).
- 연속 라이브 분석 또는 빌드 시간 분석에 대해 주문형 코드 분석 실행 워크플로를 선호 하는 경우가 있습니다. 이 경우 라이브 분석 및/또는 빌드 중에 분석기 실행을 사용 하지 않도록 설정할 수 있습니다. 분석을 사용 하지 않도록 설정 하는 방법에 대 한 자세한 내용은 [소스 코드 분석을 사용 하지 않도록 설정](disable-code-analysis.md) 그런 다음 프로젝트 또는 솔루션에 대해 코드 분석을 수동으로 트리거 하려고 합니다.

### <a name="run-code-analysis-manually"></a>수동으로 코드 분석 실행

1. **솔루션 탐색기**에서 프로젝트를 선택 합니다.

2. **분석** 메뉴에서 *프로젝트 이름* **에 대해 코드 분석 실행** 을 선택 합니다.

코드 분석은 백그라운드에서 실행을 시작 합니다. Visual Studio 상태 표시줄에서 왼쪽 아래 모퉁이에 **대 한 코드 분석을 실행 \<project> ** 하는 중 ... 메시지가 표시 됩니다. 코드 분석이 완료 되 면 상태 메시지가 **에 대해 \<project> 완료 된 코드 분석 **으로 변경 됩니다. 모든 코드 분석 진단 기능을 사용 하 여 오류 목록이 곧 새로 고쳐집니다.
