---
title: Visual Studio가 느린 경우 성능 향상
titleSuffix: ''
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: 6495e8506e12c0c5e5f878a23c609fe53a401bde
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596998"
---
# <a name="optimize-visual-studio-performance"></a>Visual Studio 성능 최적화

이 문서에서는 Visual Studio 느리게 실행되는 경우 몇 가지 시도해볼 제안을 제공합니다. 성능 향상 방법에 대한 더 많은 제안은 [Visual Studio 성능 팁 및 요령](../ide/visual-studio-performance-tips-and-tricks.md)을 참조할 수 있습니다.

## <a name="upgrade-visual-studio"></a>Visual Studio 업그레이드

현재 Visual Studio 2015를 사용하는 경우 무료로 [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 또는 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)를 다운로드하여 향상된 성능을 확인해 보세요. 솔루션은 Visual Studio 2015에 비해 2-3배 더 빠르게 로드되며 다른 영역에서도 성능이 향상됩니다. Visual Studio 2017 및 Visual Studio 2019는 Visual Studio 2015와 호환 가능하므로 사용해도 아무런 손실이 없습니다.

::: moniker range="vs-2017"

이미 Visual Studio 2017을 사용 중인 경우 버전 15.6 이상을 실행하고 있는지 확인합니다. 데이터에 따르면 버전 15.6에서 솔루션이 최대 2-3배 더 빠르게 로드됩니다. [여기](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)에서 다운로드하세요.

::: moniker-end

## <a name="extensions-and-tool-windows"></a>확장명 및 도구 창

확장명이 설치되어 있으면 Visual Studio가 느려질 수 있습니다. 성능 향상을 위한 확장명 관리에 대한 도움말은 [성능 향상을 위한 확장명 설정 변경](../ide/optimize-visual-studio-startup-time.md#extensions)을 참조합니다.

마찬가지로 도구창이 있으면 Visual Studio가 느려질 수 있습니다. 도구 창 관리에 관한 도움말은 [성능 향상을 위한 도구 창 설정 변경](../ide/optimize-visual-studio-startup-time.md#tool-windows)을 참조합니다.

## <a name="hardware"></a>하드웨어

하드웨어 업그레이드를 고려하는 경우 RAM 추가나 더 빠른 CPU 장착보다 SSD(side-by-side)가 성능에는 더 큰 영향을 미칩니다.

최적의 성능을 위해 SSD를 추가하는 경우 HDD(hard disk drive)에 대조적으로 해당 드라이브에 Windows를 설치합니다. Visual Studio 솔루션의 드라이브 위치는 별로 중요하지 않은 것 같습니다.

또한 USB 드라이브에서 솔루션을 실행하지 마십시오. 솔루션을 HDD 또는 SSD에 복사합니다.

## <a name="help-us-improve"></a>개선할 수 있도록 도와주세요

여러분의 의견이 개선에 도움이 됩니다. **문제 보고** 기능을 사용하여 추적을 "레코드"하고 당사에 보내십시오. **빠른 실행** 옆에 있는 피드백 아이콘을 선택하거나 메뉴 모음에서 **도움말** > **의견 보내기** > **문제 보고**를 선택합니다. 자세한 내용은 [Visual Studio의 문제를 보고하는 방법](../ide/how-to-report-a-problem-with-visual-studio.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [성능 팁 및 요령](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio 블로그 - Visual Studio 2017 버전 15.6으로 더 빠르게 솔루션 로드](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
