---
title: Python 코드의 성능 측정
description: CPython 기반 인터프리터를 사용할 때 Visual Studio 프로파일러를 통해 Python 코드의 성능을 확인합니다.
ms.date: 11/12/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e31286a9b0ea3852ad1fe788d4ff6c4c66e7e4f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62784285"
---
# <a name="profile-python-code"></a>Python 코드 프로파일링

CPython 기반 인터프리터를 사용하는 경우 Python 애플리케이션을 프로파일링할 수 있습니다. (서로 다른 버전의 Visual Studio에 대해 이 기능을 사용할 수 있는지 여부는 [기능 매트릭스 - 프로파일링](overview-of-python-tools-for-visual-studio.md#matrix-profiling)을 참조하십시오.)

## <a name="profiling-for-cpython-based-interpreters"></a>CPython 기반 인터프리터에 대한 프로파일링

프로파일링은 **분석** > **Python 프로파일링 시작** 메뉴 명령을 통해 시작되며, 구성 대화 상자가 열립니다.

![프로파일링 구성 대화 상자](media/profiling-start.png)

**확인**을 선택하면 프로파일러가 실행되고 애플리케이션에서 소요된 시간을 탐색할 수 있는 성능 보고서를 엽니다.

![프로파일링 성능 보고서](media/profiling-results.png)

> [!Note]
> 현재 Visual Studio는 이 수준의 전체 애플리케이션 프로파일링만 지원하지만 향후 기능에 대한 여러분의 피드백을 보내 주시기 바랍니다. 이 페이지 아래쪽에 있는 **제품 피드백** 단추를 사용하세요.

## <a name="profiling-for-ironpython"></a>IronPython에 대한 프로파일링

IronPython이 CPython 기반 인터프리터가 아니기 때문에 위의 프로파일링 기능이 작동하지 않습니다.

대신, *ipy.exe*를 직접 대상 애플리케이션으로 시작하여 Visual Studio .NET 프로파일러를 사용하고 시작 스크립트를 실행하기 위해 적절한 인수를 사용합니다. 명령줄에 `-X:Debug`를 포함하면 모든 Python 코드를 디버그하고 프로파일링할 수 있습니다. 이 인수는 IronPython 런타임 및 사용자 코드 둘 다에서 소요된 시간을 포함하는 성능 보고서를 생성합니다. 코드는 변환된 이름을 사용하여 식별됩니다.

또는 IronPython에는 고유한 기본 내장 프로파일링이 일부 포함되어 있지만 현재 이를 위한 시각화 도우미가 없습니다. 제공되는 기능에 대해서는 [IronPython 프로파일러](https://blogs.msdn.microsoft.com/curth/2009/03/30/an-ironpython-profiler/)(MSDN 블로그)를 참조하세요.
