---
title: Visual Studio 및 Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 098d94a1aed9020271db5010e278a4aa8fc68330
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842190"
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio 및 Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Xamarin은 일반적인 C#/.NET 코드베이스에서 네이티브 iOS, Android 및 Windows 앱을 빌드하여 플랫폼 간에 75%에서 거의 100%까지 코드를 재사용할 수 있는 모바일 앱 개발 플랫폼입니다. Xamarin 및 C#으로 작성된 앱에는 기본 플랫폼 API에 대한 모든 권한이 있으며, 네이티브 사용자 인터페이스를 빌드하는 기능 및 런타임 성능에 거의 영향을 주지 않도록 플랫폼별 패키지로 컴파일하는 기능이 있습니다. 참고: Xamarin도 F#을 지원하지만 이 설명서에서는 C#에 대해서만 중점적으로 설명합니다. Visual Basic은 현재 지원되지 않습니다.  
  
 그러나 아직도 C#, .NET 및 Visual Studio에 친숙한 개발자의 경우에도 Objective-C 또는 Java 같은 네이티브 코딩 언어를 배울 필요 없이 Android, iOS 및 Windows 디바이스의 원격 디버깅과 같이 모바일 앱에 Xamarin을 사용할 때 동일한 능력과 생산성을 발휘할 수 있습니다. 따라서 NASCAR, Aviva 및 MixRadio와 같은 뛰어난 사용자 인터페이스를 가진 대부분 고성능 앱이 Xamarin을 사용하여 빌드되었다는 점은 그리 놀랄 일이 아닙니다.  
  
 이 설명서를 참조하여 이러한 환경을 빌드하기 위한 **Xamarin이 포함된 Visual Studio**의 전체 기능을 살펴볼 수 있습니다.  
  
- 약간 시간(인터넷 연결 속도, 이미 설치한 항목 및 선택할 옵션에 따라 일반적으로 2~4시간)이 걸리는 프로세스인 [Setup and install](../cross-platform/setup-and-install.md)부터 시작합니다.  
  
- 설치 관리자를 실행하는 동안 [Xamarin을 사용한 모바일 개발에 대해 알아보기](../cross-platform/learn-about-mobile-development-with-xamarin.md)를 살펴볼 수 있습니다. 여기서는 Xamarin의 특성, Xamarin.Forms와 네이티브 UI를 비교한 내용 등이 제공됩니다.  
  
- 설치가 완료되면 [Verify your Xamarin environment](../cross-platform/verify-your-xamarin-environment.md)을 수행합니다.  
  
- 그리고 마지막으로 [Visual Studio에서 Xamarin.Forms를 사용한 앱 빌드 기본 사항 알아보기](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md) 자습서를 진행합니다.  
  
  [모든 Visual Studio 2015 버전](https://www.visualstudio.com/vs-2015-product-editions)(Community, Professional, Enterprise)을 통해 모든 Xamarin 기능으로 작업할 수 있습니다. 또한 2016년 3월 31일부터는 Xamarin이 모든 Visual Studio 2015 버전에 포함되었으며 더 이상 개별 라이선스는 필요하지 않습니다. Visual Studio 2013의 경우에는 [설정 및 설치](../cross-platform/setup-and-install.md) 항목의 설명에 따라 Xamarin을 별도로 설치할 수 있습니다.  
  
> [!NOTE]
> 이러한 지침에서는 Windows 및 Visual Studio에 친숙한 사용자에게 가장 간편하고 직관적인 컴퓨터 구성을 설명합니다. 이 구성에서는 Mac을 조작해서 iOS 시뮬레이터와 테더링된 디바이스를 사용하면 되므로 전체 개발 환경이 간소화됩니다. Mac에 친숙한 경우에는 Parallels/VMWare 내부에서 Visual Studio를 실행하거나 Xamarin Studio Community를 사용하는 것이 좋습니다. 관련 지침은 [Mac 사용자용 설정, 설치 및 확인](../cross-platform/setup-install-and-verifications-for-mac-users.md)을 참조하세요.  
  
> [!NOTE]
> HTML 및 CSS를 기반으로 하는 플랫폼 간 개발 솔루션을 찾고 있다면 [Visual Studio에서 플랫폼 간 개발](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML)에 설명 된 Apache Cordova에 대 한 Visual Studio Tools를 확인 하세요.
