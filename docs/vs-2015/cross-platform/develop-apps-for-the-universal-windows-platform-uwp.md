---
title: UWP(유니버설 Windows 플랫폼)용 앱 개발 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b3f38f519444de7876046baf242f74a18b8c5a59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844365"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>UWP(유니버설 Windows 플랫폼)용 앱 개발
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

유니버설 Windows 플랫폼과 단일 Windows 코어를 사용하여 휴대폰에서 데스크톱에 이르는 모든 Windows 10 디바이스에서 동일한 앱을 실행할 수 있습니다. Visual Studio 2015 및 유니버설 Windows 앱 개발 도구를 사용하여 이러한 유니버설 Windows 앱을 만듭니다.

 ![유니버설 Windows 플랫폼](../cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 Windows 10 Phone, Windows 10 데스크톱 또는 Xbox에서 이 앱을 실행합니다. 동일한 앱 패키지입니다. Windows 10 단일 통합 코어가 도입되면서 하나의 앱 패키지를 모든 플랫폼에서 실행할 수 있습니다. 일부 플랫폼에는 플랫폼 특정 동작을 활용하기 위해 앱에 추가할 수 있는 확장 SDK가 있습니다. 예를 들어 모바일용 SDK 확장은 Windows Phone에서 뒤로 단추를 누르는 동작을 처리합니다. 프로젝트에서 확장 SDK를 참조하는 경우 런타임 검사를 추가하여 해당 플랫폼에서 SDK를 사용할 수 있는지 테스트하면 됩니다. 이런 방식으로 각 플랫폼에 동일한 앱 패키지를 사용할 수 있습니다.

 **Windows Core란 무엇인가요?**

 처음으로 Windows가 모든 Windows 10 플랫폼에서 공통 코어를 사용하도록 리팩터링되었습니다. 하나의 공통 소스, 하나의 공통 Windows 커널, 하나의 파일 I/O 스택 및 하나의 앱 모델이 있습니다. UI의 경우 하나의 XAML UI 프레임워크와 하나의 HTML UI 프레임워크가 있습니다. 따라서 다양한 Windows 10 디바이스에서 앱을 쉽게 실행할 수 있으므로 뛰어난 앱을 개발하는 데만 집중할 수 있습니다.

 **유니버설 Windows 플랫폼이란 정확히 무엇인가요?**

 단순히 계약 및 버전 컬렉션입니다. 앱을 실행할 수 있는 대상을 지정하는 데 사용됩니다. 더 이상 운영 체제를 대상으로 지정하지 않습니다. 이제 하나 이상의 디바이스 제품군을 앱의 대상으로 지정합니다. 자세한 내용은 이 [플랫폼 가이드](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx)를 참조하세요.

## <a name="requirements"></a>요구 사항
 유니버설 Windows 앱 개발 도구에는 여러 다른 디바이스에서의 앱 모양을 확인하는 데 사용할 수 있는 에뮬레이터가 제공됩니다. 이러한 에뮬레이터를 사용하려는 경우 물리적 컴퓨터에서 이 소프트웨어를 설치해야 합니다. 물리적 컴퓨터는 Windows 8.1(x64) Professional Edition 이상을 실행하고 클라이언트 Hyper-V 및 SLAT(두 번째 수준 주소 변환)를 지원하는 프로세서가 있어야 합니다. Visual Studio가 가상 머신에 설치된 경우에는 에뮬레이터를 사용할 수 없습니다.

 필요한 소프트웨어 목록은 다음과 같습니다.

- [Windows 10](https://windows.microsoft.com/windows/downloads)

- [Visual Studio 2015](https://visualstudio.microsoft.com/downloads/). 유니버설 Windows 앱 개발 도구가 선택적 기능 목록에서 선택되었는지 확인합니다. 이러한 도구가 없으면 유니버설 앱을 만들 수 없습니다.

  이 소프트웨어를 설치한 후 개발을 위해 [Windows 10 장치를 사용 하도록 설정](https://msdn.microsoft.com/library/windows/apps/xaml/dn706236.aspx) 해야 합니다. 각 Windows 10 디바이스에 대한 개발자 라이선스는 더 이상 필요하지 않습니다.

  **Windows 8.1 및 Windows 7 지원**

  Windows 10 이외의 플랫폼에서 Visual Studio 2015를 사용하여 유니버설 Windows 앱을 개발하기로 선택한 경우 다음과 같은 제한 사항이 적용됩니다.

- Windows 8.1: 앱을 로컬로 실행할 수 없습니다(원격 Windows 10 디바이스에서만). Visual Studio에서 에뮬레이터를 사용할 수 있지만 시뮬레이터는 사용할 수 없습니다.

- Windows 7: 앱을 로컬로 실행할 수 없습니다(원격 Windows 10 디바이스에서만). Visual Studio에서 에뮬레이터나 시뮬레이터 중 하나만 사용할 수 있습니다.

  개발 플랫폼이 Windows 10인 경우에만 XAML 디자이너를 사용할 수 있습니다.

## <a name="universal-windows-apps"></a>Universal Windows 앱
 C#, Visual Basic, C++ 또는 JavaScript에서 기본 설정 개발 언어를 선택하여 [Windows 10 디바이스용 유니버설 Windows 앱을 만드세요](https://msdn.microsoft.com/library/windows/apps/xaml/dn609832.aspx#target_win10). 또는 [이 시작 동영상](https://channel9.msdn.com/Series/ConnectOn-Demand/229)을 시청하세요.

 기존 Windows 스토어 8.1 앱, Windows Phone 8.1 앱 또는 Visual Studio 2015 RC를 사용하여 만든 유니버설 Windows 앱이 있으면 [이러한 기존 앱을 포팅](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) 하여 최신 유니버설 Windows 플랫폼을 사용합니다.

 유니버설 Windows 앱을 만든 후에는 앱을 [패키지](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) 하 여 windows 10 장치에 설치 하거나 windows 스토어에 제출 해야 합니다.
