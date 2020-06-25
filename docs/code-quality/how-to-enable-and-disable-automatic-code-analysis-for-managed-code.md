---
title: 레거시 코드 분석 사용 안 함
ms.date: 10/04/2019
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 532fe62ceee3ab32fc203976af58dd867b97b453
ms.sourcegitcommit: 48e93538f1e352fc1f972b642bb5fcce2f6834a2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85371887"
---
# <a name="how-to-enable-and-disable-binary-code-analysis-for-managed-code"></a>방법: 관리 코드에 대 한 이진 코드 분석 사용 및 사용 안 함

관리 코드 프로젝트의 각 빌드 후에 레거시 코드 분석 (이진 분석)을 실행 하도록 구성할 수 있습니다. 또한 각 빌드 구성에 대 한 다양 한 설정 (예: 디버그 및 릴리스)을 사용할 수 있습니다.

> [!NOTE]
> .NET Core 및 .NET Standard apps와 같은 최신 프로젝트 형식에는 레거시 분석을 사용할 수 없습니다. 이러한 프로젝트는 [.NET Compiler Platform 기반 코드 분석기](roslyn-analyzers-overview.md) 를 사용 하 여 실시간 및 빌드 시 코드를 분석 합니다. 이러한 프로젝트에서 소스 코드 분석을 사용 하지 않도록 설정 하는 방법에 대 한 자세한 내용은 [소스 코드 분석 사용 안 함을](disable-code-analysis.md)참조 하세요.

레거시 코드 분석을 사용 하거나 사용 하지 않도록 설정 하려면:

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 선택 합니다.

2. 프로젝트에 대 한 속성 대화 상자에서 **코드 분석** 탭을 선택 합니다.

3. **구성** 의 빌드 형식과 **플랫폼**의 대상 플랫폼을 지정 합니다. (Non-.NET Core/.NET Standard 프로젝트에만 해당)

::: moniker range="vs-2017"

4. 자동 코드 분석을 사용 하거나 사용 하지 않도록 설정 하려면 **빌드 시 코드 분석 사용** 확인란을 선택 하거나 선택 취소 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

4. 자동 코드 분석을 사용 하거나 사용 하지 않도록 설정 하려면 **이진 분석기** 섹션에서 **빌드 시 실행** 확인란을 선택 하거나 선택 취소 합니다.

   ![Visual Studio에서 빌드 옵션에 대 한 이진 코드 분석 실행](media/run-on-build-binary-analyzers.png)

::: moniker-end

> [!NOTE]
> 빌드 시 이진 코드 분석을 사용 하지 않도록 설정 해도 [.NET Compiler Platform 기반 코드 분석기](roslyn-analyzers-overview.md)에는 영향을 주지 않습니다 .이 분석기는 NuGet 패키지로 설치한 경우 항상 빌드 시 실행 됩니다. 이러한 분석기에서 분석을 비활성화 하는 방법에 대 한 자세한 내용은 [소스 코드 분석을 비활성화 하는 방법](disable-code-analysis.md)을 참조 하세요.
