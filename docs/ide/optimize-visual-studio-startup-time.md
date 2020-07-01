---
title: 작동 시간 향상
ms.date: 11/15/2017
ms.topic: how-to
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 399bab1b95a7f17166f205902d04a1abec10e6dd
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770965"
---
# <a name="optimize-visual-studio-startup-time"></a>Visual Studio 시작 시간 최적화

Visual Studio는 최대한 신속하고 효율적으로 시작되도록 설계되었습니다. 그러나 특정 Visual Studio 확장명 및 도구 창이 로드 될 때 시작 시간에 부정적 영향을 미칠 수 있습니다. **Visual Studio 성능 관리** 대화 상자에서 느린 확장 및 도구 창이라는 동작을 제어할 수 있습니다. 성능 향상에 대한 더 일반적인 팁은 [Visual Studio 성능 팁과 요령](../ide/visual-studio-performance-tips-and-tricks.md)을 참조하세요.

## <a name="startup-behavior"></a>시작 동작

시작 시간이 확장되지 않도록 방지하려면 Visual Studio에서는 _요청 시_ 접근 방식을 사용하여 확장을 로드합니다. 이 동작은 Visual Studio가 시작된 후 즉시 확장이 열리지 않고 필요에 따라 열리도록 합니다. 또한 이전 Visual Studio 세션에서 열려 있는 도구 창으로 인해 시작 시간이 느려질 수 있으므로 Visual Studio는 시작 시간에 영향을 주지 않도록 보다 지능적인 방식으로 도구 창을 엽니다.

Visual Studio에서 시작 속도가 느린 것을 감지하면 속도 저하를 초래하는 확장이나 도구 창을 알려주는 팝업 메시지가 나타납니다. 이 메시지는 **Visual Studio 성능 관리** 대화 상자에 대한 링크를 제공합니다. 메뉴 모음에서 **도움말** > **Visual Studio 성능 관리**를 선택하여 이 대화 상자에 액세스할 수도 있습니다.

![Visual Studio 성능 관리에 ‘... 확장으로 인해 Visual Studio가 느려집니다’라는 팝업이 나타납니다.](../ide/media/vside_perfdialog_popup.png)

이 대화 상자에는 시작 성능에 영향을 미치는 확장 및 도구 창이 나열됩니다. 확장 및 도구 창 설정을 변경하여 시작 성능을 향상할 수 있습니다.

## <a name="to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />시작, 솔루션 로드 및 성능 입력을 개선하기 위해 확장 설정을 변경하려면

1. 메뉴 모음에서 **도움말** > **Visual Studio 성능 관리**를 차례로 선택하여 **Visual Studio 성능 관리** 대화 상자를 엽니다.

    확장으로 인해 Visual Studio 시작, 솔루션 로딩 또는 입력 속도가 느려지는 경우 **확장** > **시작**(또는 **솔루션 로드** 또는 **입력**) 아래에서 **Visual Studio 성능 관리** 대화 상자에 해당 확장이 표시됩니다.

    ![Visual Studio 성능 관리 - 확장 보기](../ide/media/vside_perfdialog_extensions.png)

2. 사용하지 않으려는 확장을 선택한 다음 **사용하지 않음** 단추를 선택합니다.

**확장 관리자** 또는 **Visual Studio 성능 관리** 대화 상자를 통해 이후 세션에 확장을 언제든지 다시 사용할 수 있습니다.

## <a name="to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />시작 시간을 개선하도록 도구 창 설정을 변경하려면

1. 메뉴 모음에서 **도움말** > **Visual Studio 성능 관리**를 차례로 선택하여 **Visual Studio 성능 관리** 대화 상자를 엽니다.

    도구 창에서 Visual Studio 시작 속도가 느려지면 도구 창이 **도구 창** > **시작** 아래의 **Visual Studio 성능 관리** 대화 상자에 나타납니다.

2. 동작을 변경하려는 도구 창을 선택합니다.

3. 다음 세 가지 옵션 중 하나를 선택합니다.

   - **기본 동작 사용:** 도구 창에 대한 기본 동작입니다. 이 옵션을 선택하면 시작 성능이 향상되지 않습니다.

   - **시작 시 창 표시 안 함:** 이전 세션에서 열려 있는 경우에도 Visual Studio를 열 때 지정한 도구 창이 항상 닫힙니다. 원하는 경우 적절한 메뉴에서 도구 창을 열 수 있습니다.

   - **시작 시 창 자동 숨기기:** 도구 창이 이전 세션에서 열려 있는 경우 이 옵션은 시작 시 도구 창의 그룹이 축소되어 도구 창이 초기화되지 않도록 합니다. 이 옵션은 도구 창을 사용하는 경우에 적합합니다. 도구 창을 여전히 사용할 수 있지만 더 이상 Visual Studio 시작 시간에 부정적 영향을 미치지 않습니다.

     ![Visual Studio 성능 관리 - 도구 창 보기](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> 일부 이전 버전의 Visual Studio 2017에는 **경량 솔루션 로드**라는 기능이 있습니다. 현재 버전에서는 경량 솔루션 로드 없이도 관리 코드가 포함된 대규모 솔루션이 이전보다 훨씬 빠르게 로드됩니다.

## <a name="see-also"></a>참조

- [Visual Studio 성능 최적화](../ide/optimize-visual-studio-performance.md)
- [Visual Studio 성능 팁과 요령](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio 블로그 - Visual Studio 2017 버전 15.6으로 더 빠르게 솔루션 로드](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
