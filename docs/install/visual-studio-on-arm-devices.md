---
title: ARM 기반 디바이스에서의 Visual Studio
description: ARM 기반 프로세서를 사용하는 디바이스에서 Visual Studio를 사용하기 위한 권장 사항입니다.
ms.date: 09/10/2020
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 6aacd4639e440998a5123dae8c38a64c84ebb948
ms.sourcegitcommit: d9dd86c421532cfca6c0c5761d160f35829419c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90026305"
---
# <a name="visual-studio-on-arm-powered-devices"></a>ARM 기반 디바이스에서의 Visual Studio

> [!IMPORTANT]
> Visual Studio는 x86 또는 AMD64/x64 기반 프로세서를 사용하는 디바이스에서만 지원됩니다.

Visual Studio는 x86 아키텍처를 기반으로 하는 프로세서를 대상으로 하며 ARM 기반 프로세서용 Visual Studio 버전은 없습니다. 그러나 Windows는 [ARM에 대한 x86 에뮬레이션](https://www.docs.microsoft.com/windows/uwp/porting/apps-on-arm-x86-emulation)을 제공하므로 이를 통해 Visual Studio를 실행할 수 있습니다. ARM 프로세서에서 x86 에뮬레이션을 통해 Visual Studio를 실행하는 경우 Visual Studio의 성능이 심각하게 저하되며 Visual Studio의 여러 기능은 이러한 시나리오에서 작동하도록 설계되지 않았습니다. 따라서 ARM 기반 프로세서를 사용하는 디바이스에서 Visual Studio를 실행하지 않는 것이 좋으며, 대신 원격 대상으로 지정된 ARM 디바이스를 사용하는 것이 좋습니다.

## <a name="remote-targeting-arm-devices"></a>ARM 디바이스 원격 대상 지정
최상의 환경을 위해 별도의 x86 기반 컴퓨터에서 Visual Studio를 사용하고 Visual Studio의 원격 배포 및 디버깅 기능을 사용하여 ARM 기반 디바이스를 대상으로 지정하는 것이 좋습니다. 디바이스에 이미 설치된 Windows 유니버설 애플리케이션을 디버깅하려면 [설치된 앱 패키지 디버그](../debugger/debug-installed-app-package.md) 설명서를 참조하세요. 새 앱을 배포하려면 [원격으로 Windows 스토어 앱 실행](../debugger/run-windows-store-apps-on-a-remote-machine.md)을 참조하세요. 다른 모든 애플리케이션 유형은 [원격 디버깅](../debugger/remote-debugging.md) 설명서를 참조하세요.

## <a name="tips-for-running-visual-studio-on-arm-devices"></a>ARM 디바이스에서 Visual Studio를 실행하기 위한 팁

### <a name="use-only-when-needed"></a>필요한 경우에만 사용
ARM 관련 작업에 필요한 경우에만 Visual Studio를 사용하여 시간을 최적화합니다. 모든 ARM 기반 디바이스에서 성능이 저하되므로 정기적인 사용은 불가능할 수 있습니다.

### <a name="install-time"></a>설치 시간
Visual Studio를 설치하는 데 더 오래 걸리고 일정 시간 동안 일시 중지하거나 다시 시작이 필요합니다.
 
### <a name="remote-tools"></a>원격 도구
원격 디바이스에서 실행되는 앱을 디버그하려면 ARM용 [원격 도구를 다운로드 및 설치](../debugger/remote-debugging.md#download-and-install-the-remote-tools)해야 합니다.

### <a name="start-debugging-f5"></a>디버깅 시작(F5)
ARM 디바이스에서 디버깅(**F5**)을 시작하는 경우 일부 Visual Studio 프로젝트는 로컬로 프로젝트를 시작하도록 구성되지 않았습니다. 앱이 로컬로 실행되는 경우에도 Visual Studio에서 원격 디버깅을 구성해야 할 수 있습니다. 자세한 내용은 [원격 디버깅](../debugger/remote-debugging.md)을 참조하세요.

## <a name="we-need-your-help"></a>사용자 여러분의 도움이 필요합니다!
Visual Studio를 ARM 디바이스에서 기본적으로 실행하려는 경우 필요한 시나리오 및 지원에 대한 의견을 보내주시기 바랍니다. [개발자 커뮤니티](https://developercommunity.visualstudio.com/idea/1161018/native-arm-support-for-visual-studio.html)에 게시하여 Microsoft와 연락할 수 있습니다. 
