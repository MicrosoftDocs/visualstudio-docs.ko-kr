---
title: F#용 이전 .NET Framework 버전 대상 지정
description: Visual Studio에서 F#을 사용하는 경우 .NET Framework의 이전 버전을 대상으로 지정하는 방법을 알아봅니다.
ms.date: 07/11/2018
ms.topic: troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: 4b5cf62dadc38802e477c7588416b4003304e852
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75584584"
---
# <a name="target-older-versions-of-net-f"></a>.NET의 이전 버전 대상 지정(F#)

다음 오류는 Visual Studio가 Windows 8.1에 설치된 경우 F# 프로젝트에서 .NET Framework 2.0, 3.0 또는 3.5를 대상으로 지정하려는 경우 나타날 수 있습니다.

**이 프로젝트에는 2.0 F# 런타임이 필요하지만, 해당 런타임이 설치되어 있지 않습니다.**

이 오류는 다음과 같은 조건의 조합에서 발생하는 것으로 알려져 있습니다.

- Windows 8.1에서 Visual Studio를 설치했습니다.

- Visual Studio를 설치하기 전에 .NET Framework 3.5를 사용하도록 설정하지 않았습니다.

- 프로젝트가 .NET Framework 2.0, 3.0 또는 3.5를 대상으로 지정합니다.

Visual Studio를 설치할 때 설치된 .NET Framework의 버전을 검색합니다. Visual Studio는 .NET Framework 3.5가 설치 및 활성화되어 있는 경우에만 F# 2.0 런타임을 설치합니다.

## <a name="resolve-the-error"></a>오류 해결

이 오류를 해결하려면 다음과 같은 방법으로 해결할 수 있습니다.

- .NET Framework의 새로운 버전을 대상으로 지정합니다.

- Windows 8.1에서 .NET Framework 3.5를 사용하도록 설정한 다음, Visual Studio 설치를 복구하여 F# 2.0 런타임을 설치합니다. 이를 수행하기 위한 단계가 이어집니다.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Windows 8.1에서 .NET Framework 3.5를 사용하도록 설정하려면 다음을 수행합니다.

1. **시작** 화면에서 **제어판**을 입력합니다.

   입력할 때 **제어판** 아이콘이 **앱** 제목 아래에 표시됩니다.

2. **제어판** 아이콘을 선택하고, **프로그램** 아이콘을 선택한 다음, **Windows 기능 사용/사용 안 함** 링크를 선택합니다.

3. **.NET Framework 3.5(.NET 2.0 및 3.0 포함)** 확인란이 선택되어 있는지 확인한 다음, **확인** 단추를 선택합니다. .NET Framework의 선택적 구성 요소에 대한 모든 자식 노드의 확인란을 선택하지 않아도 됩니다.

   .NET Framework 3.5가 사용하도록 설정됩니다(아직 설정하지 않은 경우).

### <a name="to-install-the-f-20-runtime"></a>F# 2.0 런타임을 설치하려면 다음을 수행합니다.

[Visual Studio 복구 단계](../install/repair-visual-studio.md)를 수행합니다.

## <a name="see-also"></a>참고 항목

- [F# 가이드(.NET Framework)](/dotnet/fsharp/)
- [Visual Studio의 F#](fsharp-visual-studio.md)
