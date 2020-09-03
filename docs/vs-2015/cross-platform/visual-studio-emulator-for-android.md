---
title: Visual Studio Emulator for Android | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: af3dd595b786c57983e44982fa2eb8b9afa2959a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300773"
---
# <a name="visual-studio-emulator-for-android"></a>Android용 Visual Studio Emulator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Android용 Visual Studio 에뮬레이터는 Android 디바이스를 에뮬레이트하는 데스크톱 애플리케이션입니다. 물리적 디바이스를 사용하지 않고도 Android 앱을 디버그하고 테스트할 수 있는 가상화된 환경을 제공합니다. 또한 애플리케이션 프로토타입을 위한 격리된 환경을 제공합니다.  
  
 Android용 Visual Studio 에뮬레이터는 실제 디바이스와 비슷한 성능을 제공하도록 설계되었습니다. 하지만 앱을 게시하기 전에 물리적 디바이스에서 앱을 테스트하는 것이 좋습니다.  
  
 Android 플랫폼, 화면 해상도 및 Android용 Visual Studio 에뮬레이터에서 지원되는 다른 하드웨어 속성 각각에 대해 고유한 디바이스 프로필에서 앱을 테스트할 수 있습니다.  
  
 이 항목에는 다음과 같은 섹션이 포함되어 있습니다.  
  
- [설치 및 제거](#Installing)  
  
- [시스템 요구 사항 및 이전 버전과의 호환성](#Requirements)  
  
- [Visual Studio Emulator for Android의 네트워킹](#Networking)  
  
- [Visual Studio Emulator for Android 구성](#Configuring)  
  
- [에뮬레이터에서 테스트할 수 있는 기능](#FeaturesTest)  
  
- [에뮬레이터에서 테스트할 수 없는 기능](#FeaturesNonTest)  
  
- [지원 리소스](#Support)  
  
## <a name="installing-and-uninstalling"></a><a name="Installing"></a> 설치 및 제거  
 설치  
  
 Android용 Visual Studio 에뮬레이터는 Visual Studio에서 사용할 수 있는 플랫폼 간 도구의 구성 요소이며 사용자 지정 Visual Studio 설치 과정에 플랫폼 간 모바일 개발, 일반 도구와 소프트웨어 개발 키트, Visual Studio Emulator for Android를 선택하면 설치됩니다.  
  
 제거  
  
 제어판에서 프로그램 추가/제거를 사용하여 Android용 Visual Studio 에뮬레이터를 제거할 수 있습니다.  
  
> [!NOTE]
> Visual Studio를 제거해도 에뮬레이터는 제거되지 않습니다. 에뮬레이터는 별도로 제거해야 합니다.  
  
 Android 용 Visual Studio 에뮬레이터를 제거하는 경우 에뮬레이터에서 사용하도록 만들어진 Hyper-V 가상 이더넷 어댑터는 자동으로 제거되지 않습니다. Hyper-v 관리자를 열고 에뮬레이터 VHD 이미지 중 하나를 선택하고 [네트워킹] 탭을 선택한 다음 이 탭에 표시되는 각 스위치에 대해 **제거**를 선택하면 이러한 가상 어댑터(사용 중이 아닌 경우)를 수동으로 제거할 수 있습니다.  
  
## <a name="system-requirements-and-backward-compatibility"></a><a name="Requirements"></a> 시스템 요구 사항 및 이전 버전과의 호환성  
 Android용 Visual Studio 에뮬레이터의 하드웨어, 소프트웨어 및 구성 요구 사항에 대한 중요한 내용을 보려면 다음 항목을 참조하세요.  
  
- [Android 용 Visual Studio 에뮬레이터에 대 한 시스템 요구 사항](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  Android용 Visual Studio 에뮬레이터를 사용하려면 Visual Studio 2015가 필요합니다. 이전 버전의 Visual Studio와 호환되지 않습니다.  
  
  이전 버전 위에 새로운 버전의 에뮬레이터가 설치됩니다(일부 경우 이전 이미지를 바꾸고 해당 이미지에 설치되어 있던 해당 설정, 앱, 파일을 취소함).  
  
## <a name="networking-in-the-visual-studio-emulator-for-android"></a><a name="Networking"></a> Android 용 Visual Studio 에뮬레이터의 네트워킹  
 Android용 Visual Studio 에뮬레이터의 네트워킹 연결은 데스크톱 컴퓨터의 연결과 비슷하게 동작하며 다음과 같은 특징이 있습니다.  
  
- 에뮬레이터는 네트워크에서 자체 IP 주소를 가진 별도 디바이스로 나타납니다.  
  
- 에뮬레이터에 이미 설치되어 있지 않은 추가 네트워킹 소프트웨어를 요구하지 않습니다.  
  
- Windows 도메인에 가입하지 않습니다.  
  
  에뮬레이터의 네트워크 연결 기능을 이해하려면 Android 휴대폰에서 동일 네트워크로 연결되는 Wi-Fi 연결과 비슷하다고 생각하면 됩니다. 휴대폰에서 실행 중인 앱이 Wi-Fi 연결을 통해 네트워크 리소스를 액세스할 수 있는 경우, 에뮬레이터에서 실행 중인 앱도 동일한 네트워크 리소스에 액세스할 수 있습니다.  
  
  네트워크 요구 사항에 대 한 자세한 내용은 [Android 용 Visual Studio 에뮬레이터에 대 한 시스템 요구 사항](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) 을 참조 하세요.  
  
  네트워킹 문제 해결에 대한 자세한 내용은 [Visual Studio Emulator for Android 문제 해결](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)을 참조하세요.  
  
## <a name="configure-the-visual-studio-emulator-for-android"></a><a name="Configuring"></a> Android 용 Visual Studio 에뮬레이터 구성  
 다양한 Android 하드웨어에서 Android 앱의 호환성을 테스트하기는 어려울 수 있습니다. 출시된 Android 휴대폰 및 태블릿은 버전과 화면 크기가 매우 다양하며 많은 하드웨어 구성(RAM, CPU, 아키텍처 등)으로 제공됩니다. Android 용 Visual Studio 에뮬레이터는 디바이스 프로필을 사용하여 이러한 조건을 단순화합니다. Microsoft가 제공하는 일련의 디바이스 프로필은 시장에 나와 있는 가장 인기 있는 하드웨어(삼성, Motorola, Sony, LG 등의 디바이스 포함)를 대표합니다.  
  
 Visual Studio 2015에서는 에뮬레이터 관리자를 사용하여 디바이스 프로필을 설치, 제거, 시작할 수 있습니다. **도구**를 선택한 후 **Visual Studio Emulator for Android**를 선택하여 에뮬레이터 관리자에 액세스합니다.  
  
 ![Visual Studio Emulator for Android 관리자](../cross-platform/media/android-emu-manager.png "Android_Emu_Manager")  
  
 기본적으로 KitKat 및 롤리팝 휴대폰(5") 및 태블릿(7") 구성에 해당하는 사전 설치 디바이스 프로필 4가지가 제공되며 이는 흰색 텍스트와 아이콘으로 표시됩니다. 목록에 있는 다른 프로필은 **프로필 설치** 단추를 선택하여 설치가 완료되기 전까지 회색으로 나타납니다. API 수준을 기준으로 목록을 필터링하고 프로필 오른쪽 아래에 있는 세부 정보 화살표를 클릭하여 전체 구성 정보를 볼 수 있습니다.  
  
 대상으로 할 프로필 집합을 설치하고 나면 녹색 **재생** 단추를 눌러 이 새로운 프로필을 관리자에서 바로 시작할 수 있습니다. 이 프로필은 또한 Visual Studio 플랫폼 간 모바일 프로젝트 형식의 디버그 대상 드롭다운 메뉴에도 나타납니다.  
  
## <a name="features-that-you-can-test-in-the-emulator"></a><a name="FeaturesTest"></a> 에뮬레이터에서 테스트할 수 있는 기능  
 에뮬레이터에서 테스트할 수 있는 기능에 대한 자세한 내용은 이 [설명서](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/)를 참조하세요.  
  
## <a name="features-that-you-cant-test-in-the-emulator"></a><a name="FeaturesNonTest"></a> 에뮬레이터에서 테스트할 수 없는 기능  
 다음 목록에서는 에뮬레이터에서 테스트할 수 **없는** Android 플랫폼의 기능에 대해 설명합니다. 물리적 디바이스에서 다음 기능을 테스트해야 합니다.  
  
- 나침반  
  
- 자이로스코프  
  
- 진동 컨트롤러  
  
- 밝기. 에뮬레이터의 밝기 수준을 변경해도 디바이스가 화면에 표시되는 방식에 시각적인 영향이 없습니다.  
  
## <a name="support-resources"></a><a name="Support"></a> 지원 리소스  
 호스트 컴퓨터가 시스템 요구 사항을 충족한 상태에서 이 문제 해결 가이드에서 다루지 않은 문제가 발생하는 경우:  
  
- [android-emulator](https://stackoverflow.com/questions/tagged/android-emulator) 및 visual-studio 태그를 사용하여 StackOverflow에 대해 질문합니다.  
  
- Visual Studio 또는 에뮬레이터 관리자에서 웃는 얼굴 보내기 도구를 사용하여 문제를 보고합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Android 용 Visual Studio 에뮬레이터에 대 한 시스템 요구 사항](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Visual Studio Emulator for Android 문제 해결](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
