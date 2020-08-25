---
title: 단위 테스트를 64비트 프로세스로 실행
ms.date: 03/10/2020
ms.topic: how-to
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 3c5cb51232457a43200c8a71ace51cc4b8a63e02
ms.sourcegitcommit: 8e5b0106061bb43247373df33d0850ae68457f5e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88507988"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>단위 테스트를 64비트 프로세스로 실행

64비트 컴퓨터를 사용하는 경우에는 단위 테스트를 실행하고 코드 검사 정보를 64비트 프로세스로 캡처할 수 있습니다.

## <a name="to-run-a-unit-test-as-a-64-bit-process"></a>단위 테스트를 64비트 프로세스로 실행하려면

1. 코드 또는 테스트를 32비트/x86으로 컴파일했지만 64비트 프로세스로 실행하려면 **모든 CPU**로 다시 컴파일합니다.

   ::: moniker range="vs-2017"
   또는 Visual Studio 2017에서 프로젝트를 **64비트**로 컴파일할 수도 있습니다.
   ::: moniker-end

    > [!TIP]
    > 유연성을 극대화하려면 **Any CPU** 구성으로 테스트 프로젝트를 컴파일합니다. 그러면 32비트 및 64비트 에이전트 모두에서 테스트를 실행할 수 있습니다. 64비트에서만 지원되는 코드를 호출하는 경우를 제외하고는 **64비트** 구성으로 테스트 프로젝트를 컴파일하는 이점이 없습니다.

2. 64비트 프로세스로 실행되도록 단위 테스트를 설정합니다.

   ::: moniker range=">=vs-2019"
   Visual Studio 메뉴에서 **테스트**를 선택한 다음 **AnyCPU 프로젝트의 프로세서 아키텍처**를 선택합니다. **x64**를 선택해서 테스트를 64비트 프로세스로 실행합니다.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Visual Studio 메뉴에서 **테스트**, **테스트 설정**, **프로세서 아키텍처**를 차례로 선택합니다. **x64**를 선택해서 테스트를 64비트 프로세스로 실행합니다.
   ::: moniker-end

   \- 또는 -

   *.runsettings* 파일에서 `<TargetPlatform>x64</TargetPlatform>`을 지정합니다. 이 메서드의 장점은 서로 다른 파일에서 설정 그룹을 지정하고 각 설정 간에 빠르게 전환할 수 있다는 점입니다. 또한 솔루션 간에 설정을 복사할 수도 있습니다. 자세한 내용은 [.runsettings 파일을 사용하여 단위 테스트 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)을 참조하세요.

## <a name="see-also"></a>참조

- [테스트 탐색기를 사용하여 단위 테스트 실행](../test/run-unit-tests-with-test-explorer.md)
- [코드 단위 테스트](../test/unit-test-your-code.md)
