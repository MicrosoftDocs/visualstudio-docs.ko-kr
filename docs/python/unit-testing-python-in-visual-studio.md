---
title: 단위 테스트 Python 코드
description: Visual Studio에서 Python 코드에 대한 단위 테스트를 설정하면 테스트 탐색기 기능을 최대한 활용하여 테스트를 검색, 실행 및 디버그할 수 있습니다.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 2a621cd56f980c8a1404ba8855cdf3544e58d39d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535335"
---
# <a name="set-up-unit-testing-for-python-code"></a>Python 코드에 대해 유닛 테스트 설정

단위 테스트는 애플리케이션의 다른 코드 단위(일반적으로 격리된 함수, 클래스 등)를 테스트하는 코드 조각입니다. 애플리케이션이 모든 단위 테스트를 통과하면 최소한 하위 수준 기능이 올바른 것으로 신뢰할 수 있습니다.

Python은 단위 테스트를 광범위하게 사용하여 프로그램을 설계하는 동안 시나리오를 검증합니다. Visual Studio의 Python 지원에는 테스트를 별도로 실행할 필요 없이 개발 프로세스 컨텍스트 내에서 단위 테스트 검색, 실행, 디버깅이 포함됩니다.

이 문서에서는 Visual Studio에서 Python을 사용하여 유닛 테스트를 수행하는 기능에 대해 간략히 설명합니다. 일반적인 단위 테스트에 대한 자세한 내용은 [코드 단위 테스트](../test/unit-test-your-code.md)를 참조하세요.

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end