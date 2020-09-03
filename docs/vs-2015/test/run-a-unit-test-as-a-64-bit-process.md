---
title: 단위 테스트를 64비트 프로세스로 실행 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, creating
- unit tests, running
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 27
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc379f522d119e76ef8be8ba60a4cc1482e57fd1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660460"
---
# <a name="run-a-unit-test-as-a-64-bit-process"></a>단위 테스트를 64비트 프로세스로 실행
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

64비트 컴퓨터를 사용하는 경우에는 단위 테스트를 실행하고 코드 검사 정보를 64비트 프로세스로 캡처할 수 있습니다.

## <a name="running-a-unit-test-as-a-64-bit-process"></a>단위 테스트를 64비트 프로세스로 실행

#### <a name="to-run-a-unit-test-as-a-64-bit-process"></a>단위 테스트를 64비트 프로세스로 실행하려면

1. 코드 또는 테스트를 32비트/x86으로 컴파일했지만 64비트 프로세스로 실행하려면 **모든 CPU** 또는 원한다면 **64비트**로 다시 컴파일합니다.

    > [!TIP]
    > 유연성을 극대화하려면 **Any CPU** 구성으로 테스트 프로젝트를 컴파일해야 합니다. 그러면 32 비트 및 64비트 에이전트에서 모두 실행할 수 있습니다. **64비트** 구성으로 테스트 프로젝트를 컴파일하는 것은 아무 이점이 없습니다.

2. Visual Studio 메뉴에서 **테스트**, **설정**, **프로세서 아키텍처**를 차례로 선택합니다. **x64**를 선택해서 테스트를 64비트 프로세스로 실행합니다.

     \- 또는 -

     .runsettings 파일에서 `<TargetPlatform>x64</TargetPlatform>`을 지정합니다. 이 메서드의 장점은 서로 다른 파일에서 설정 그룹을 지정하고 각 설정 간에 빠르게 전환할 수 있다는 점입니다. 또한 솔루션 간에 설정을 복사할 수도 있습니다. 자세한 내용은 [.runsettings 파일을 사용하여 단위 테스트 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)을 참조하세요.

## <a name="see-also"></a>관련 항목
 [테스트 탐색기를 사용 하 여 단위 테스트 실행](../test/run-unit-tests-with-test-explorer.md) [Visual Studio 테스트에 대 한 테스트 설정을 지정 하](https://msdn.microsoft.com/library/0c15317e-80c6-4317-aed3-82b8e15e3901) 는 [코드를 테스트 합니다](../test/unit-test-your-code.md) .
