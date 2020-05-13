---
title: '방법: 시각화 도우미 설치 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 499d644cc8374b070cedaf058b0e4dc17d155bdc
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880262"
---
# <a name="how-to-install-a-visualizer"></a>방법: 시각화 도우미 설치
시각화 도우미를 만든 후에는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 사용할 수 있도록 이 시각화 도우미를 설치해야 합니다. 시각화 도우미를 설치하는 과정은 간단합니다.

> [!NOTE]
> UWP 앱에서는 표준 텍스트, HTML, XML 및 JSON 시각화 도우미만 지원됩니다. 사용자가 만든 사용자 지정 시각화 도우미는 지원되지 않습니다.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>비주얼 스튜디오 2019에 대한 시각화 도우미를 설치하려면
  
1. 빌드한 시각화 도우미가 포함된 DLL을 찾습니다.

   일반적으로 디버거 측 DLL과 디버그 측 DLL이 **모든 CPU를** 대상 플랫폼으로 지정하는 것이 가장 좋습니다. 디버거 측 DLL은 모든 **CPU** 또는 **32비트여야**합니다. 디버그지 측 DLL의 대상 플랫폼은 디부지 프로세스에 해당해야 합니다.

2. [디버거 사이드](create-custom-visualizers-of-data.md#to-create-the-debugger-side) DLL(및 DLL에 의존하는 모든 DLL)을 다음 위치 중 하나에 복사합니다.

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. [디버그지 사이드](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) DLL을 다음 위치 중 하나에 복사합니다.

    - *비주얼스튜디오설치경로* `\Common7\Packages\Debugger\Visualizers\` *프레임워크*

    - `My Documents\`*비주얼 스튜디오버전* `\Visualizers\` *프레임워크*

    *프레임워크가* 있는 위치:
    - `net2.0`런타임을 실행하는 디버지의 `.NET Framework` 경우
    - `netstandard2.0``.NET Framework v4.6.1+` (또는)를 `.NET Core 2.0+`지원하는 `netstandard 2.0` 런타임을 사용하는 디버기의 경우
    - `netcoreapp`런타임을 실행하는 디버지의 `.NET Core` 경우 (지원) `.NET Core 2.0+`

4. 디버깅 세션을 다시 시작합니다.

> [!NOTE]
> 이 절차는 Visual Studio 2017 이상에서 다릅니다. 이 문서의 [이전 버전을](how-to-install-a-visualizer.md?view=vs-2017) 참조하십시오.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Visual Studio 2017 이상용 시각화 도우미설치

> [!IMPORTANT]
> Visual Studio 2017 이상에서는 .NET Framework 시각화 도우미만 지원됩니다.

1. 빌드한 시각화 도우미가 들어 있는 DLL을 찾습니다.

2. 이 DLL을 다음 위치 중 한 곳에 복사합니다.

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. 디버깅 세션을 다시 시작합니다.

> [!NOTE]
> 원격 디버깅에 관리되는 시각화 도우미를 사용하려면 원격 컴퓨터의 동일한 경로에 DLL을 복사합니다.
::: moniker-end

## <a name="see-also"></a>참조
- [사용자 지정 시각화 도우미 만들기](../debugger/create-custom-visualizers-of-data.md)
- [방법: 시각화 도우미 작성](create-custom-visualizers-of-data.md)
