---
title: 시작 시간 최적화 | Microsoft Docs
ms.date: 11/15/2016
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f00bbc7741768852b5928b249dc7035bc440992
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670396"
---
# <a name="optimize-visual-studio-startup-time"></a>Visual Studio 시작 시간 최적화
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이상적으로 Visual Studio는 항상 최대한 빨리 시작되어야 합니다. 그러나 시작 시 Visual Studio 확장 및 열린 도구 창이 자동으로 로드되기 때문에 시작 시간이 느려질 수 있습니다. **Visual Studio 성능 관리** 창을 사용하면 Visual Studio 시작 시간에 영향을 주는 확장 및 기능을 확인할 수 있을 뿐만 아니라 로드 동작을 결정하여 Visual Studio 시작 속도에 대한 제어를 강화할 수 있습니다.

## <a name="control-startup-behavior"></a>시작 동작 제어

시작 시간이 확장 되지 않도록 하기 위해 Visual Studio 2017 이상에서는 요청 시 로드 방법을 사용 하 여 시작 시 확장 로드를 방지 합니다. 즉, Visual Studio가 시작된 후 즉시 확장이 열리지 않고 시작 후 필요에 따라 비동기적으로 열립니다. 또한 이전 Visual Studio 세션에서 열려 있는 도구 창으로 인해 시작 시간이 느려질 수 있으므로 Visual Studio는 시작 시간에 영향을 주지 않도록 보다 지능적인 방식으로 도구 창을 엽니다.

Visual Studio에서 시작 속도가 느린 것을 감지하면 속도 저하를 초래하는 확장이나 도구 창을 알려주는 팝업 메시지가 나타납니다. 메시지에는 시작 성능에 영향을 주는 확장 및 도구 창을 보여 주는 **Visual Studio 성능 관리** 대화 상자에 대한 링크도 제공됩니다. 이 대화 상자에서 확장 및 도구 창 설정을 변경하여 시작 성능을 향상할 수 있습니다.

![Visual Studio 성능 관리-팝업](../ide/media/vside-perfdialog-popup.PNG "Visual Studio 성능 관리-팝업")

**Visual Studio 성능 관리** 대화 상자에는 **확장** 및 **도구 창**이라는 두 가지 범주가 있습니다.

### <a name="control-extensions"></a>확장 제어
확장으로 인해 Visual Studio 시작 속도가 느려지는 경우 확장 형식 중 하나를 선택하면 **Visual Studio 성능 관리** 대화 상자에 해당 확장이 나타납니다. **영향** 섹션에 표시되는, 시작 시간에 미치는 영향이 너무 크면 **사용 안 함** 단추를 선택하여 시작 시 항상 확장을 사용하지 않도록 선택할 수 있습니다. 확장 관리자 또는 Visual Studio 성능 관리 대화 상자를 통해 이후 세션에 확장을 다시 사용할 수 있습니다.

![Visual Studio 성능 관리-확장](../ide/media/vside-perfdialog-extensions.PNG "Visual Studio 성능 관리-확장")

시작 확장뿐 아니라 솔루션 로드 시 또는 사용자 입력 시 로드되는 확장도 사용하지 않도록 설정할 수 있습니다. 연결된 확장 목록을 보려면 해당 시나리오를 선택합니다.

### <a name="control-tool-windows"></a>도구 창 제어
도구 창으로 인해 Visual Studio 시작 속도가 느려지는 경우 기본 동작으로 유지하거나(시작 속도가 향상되지 않음), 다음 두 가지 동작 중 하나를 선택하여 동작을 재정의할 수 있습니다.

- **시작 시 창 표시 안 함:** 이 옵션을 선택하면 이전 세션에서 열려 있는 경우에도 Visual Studio를 열 때 지정한 도구 창이 항상 닫힙니다. 메뉴에서 도구 창을 열 수 있습니다.
- **시작 시 창 자동 숨기기:** 도구 창이 이전 세션에서 열려 있는 경우 이 옵션을 선택하면 시작 시 도구 창의 그룹이 축소되어 도구 창이 초기화되지 않도록 합니다. 도구 창을 자주 사용하는 경우 도구 창을 여전히 사용할 수 있지만 더 이상 Visual Studio 시작 시간을 지연시키지 않으므로 이 옵션을 선택하는 것이 좋습니다.

![Visual Studio 성능 관리-도구 창](../ide/media/vside-perfdialog-toolwindows.PNG "Visual Studio 성능 관리-도구 창")

나중에 마음이 바뀌면 **Visual Studio 성능 관리** 대화 상자에서 이러한 옵션을 되돌릴 수 있습니다. **Visual Studio 성능 관리** 대화 상자를 열려면 메뉴 모음에서 **도움말**, **Visual Studio 성능 관리**를 차례로 선택합니다.
