---
title: Visual Studio Emulator for Android의 시스템 요구 사항 | Microsoft Docs
ms.custom: ''
ms.prod: visual-studio-dev15
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 35e766ad-269f-41e4-ba23-74a556c315f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f1462769a4ba9929a000bca998c1fe3708908798
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272048"
---
# <a name="system-requirements-for-the-visual-studio-emulator-for-android"></a>Android용 Visual Studio 에뮬레이터에 대한 시스템 요구 사항

Android용 Visual Studio 에뮬레이터는 Windows 8 이상 버전의 가상화 기술인 Hyper-V에서 가상 머신으로 실행됩니다. 에뮬레이터를 실행하려면 컴퓨터가 이 항목의 설명대로 Hyper-V를 실행하기 위한 요구 사항을 충족해야 합니다.

에뮬레이터를 설치할 때 설치 프로그램이 이러한 필수 조건을 자동으로 구성하려고 시도합니다. 설치에서 이 필수 조건이 성공적으로 구성되면 에뮬레이터는 예상대로 작동합니다. 제대로 구성되지 않으면 수동으로 이 필수 조건을 설정해야 할 수도 있습니다. 필수 조건을 수동으로 구성해야 하는 경우 단계 및 도구는 Windows Phone 에뮬레이터에 대해 [여기](/previous-versions/windows/apps/jj863509\(v=vs.105\)) 에서 설명하는 단계와 동일합니다.

> [!IMPORTANT]
> 에뮬레이터에 대한 설치 프로그램은 Android용 Visual Studio 에뮬레이터를 실행하기 위한 필수 조건을 확인합니다. 필수 조건이 없는 경우 경고가 표시되지만 이러한 필수 조건을 필수로 요구하지는 않습니다.

## <a name="Checklist"></a> 빠른 검사 목록

다음은 Android용 Visual Studio 에뮬레이터를 실행하기 위한 요구 사항의 빠른 검사 목록입니다. 자세한 내용은 이 항목의 후속 섹션을 참조하세요.

시스템 요구 사항

- Hyper-V 지원(아래 Hyper-V 요구 사항 참조)

- 6GB 이상의 RAM

- 64비트 버전의 Windows 8 Pro Edition, Windows 8.1 및 Windows10 이상

- SSSE3 이상을 지원하는 프로세서

네트워크 요구 사항

- DHCP

- 자동으로 구성된 DNS 및 게이트웨이 설정

Hyper-V 요구 사항

- BIOS에서 다음 기능을 지원해야 합니다.

  - 하드웨어 지원 가상화

  - SLAT(두 번째 수준 주소 변환)

  - 하드웨어 기반 DEP(데이터 실행 방지)

- Windows에서 Hyper-V가 활성화되어 실행 중이어야 합니다.

- 로컬 Hyper-V Administrators 그룹의 구성원이어야 합니다.

## <a name="system-requirements"></a>시스템 요구 사항
 컴퓨터는 다음 요구 사항을 충족해야 합니다.

- Hyper-V 지원( [Hyper-V 요구 사항](#hyper-v-requirements)참조)

- 6GB 이상의 RAM

- 64비트 버전의 Windows 8 Pro Edition, Windows 8.1 및 Windows10 이상

RAM 및 Windows에 대한 요구 사항을 확인하려면 제어판에서 시스템 및 보안을 선택한 다음 시스템을 선택합니다.

![시스템 요구 사항 확인](../cross-platform/media/android_emu_system_requirements.png "Android_Emu_System_Requirements")

## <a name="network-requirements"></a>네트워크 요구 사항

네트워크는 다음 요구 사항을 충족해야 합니다.

- DHCP

   에뮬레이터는 네트워크에서 자체 IP 주소를 갖는 별도의 디바이스로 구성되므로 DHCP가 필요합니다.

- 자동으로 구성된 DNS 및 게이트웨이 설정

   에뮬레이터에 대해 DNS 및 게이트웨이 설정을 수동으로 구성할 수 없습니다.

  에뮬레이터의 네트워킹 문제를 해결하려면 다음 항목을 참조합니다.

- [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

## <a name="hyper-v-requirements"></a>Hyper-V 요구 사항

BIOS의 Hyper-V 요구 사항

컴퓨터의 BIOS는 다음 요구 사항을 지원해야 하며, 해당 기능이 사용하도록 설정되어야 합니다.

- 하드웨어 지원 가상화

- SLAT(두 번째 수준 주소 변환)

- 하드웨어 기반 DEP(데이터 실행 방지)

Windows의 Hyper-V 요구 사항

컴퓨터 및 BIOS 설정이 Hyper-V를 지원하도록 이미 구성되어 있는 경우 설치 프로그램이 Hyper-V를 사용하고 시작합니다. 구성되지 않은 경우 수동으로 이 요구 사항을 설정해야 할 수도 있습니다.

|요구 사항|요구 사항을 확인하고 사용하도록 설정하는 방법|
|-----------------|----------------------------------------------|
|Hyper-V를 설치해야 함|[Windows Phone 에뮬레이터용 Hyper-V를 설정](/previous-versions/windows/apps/jj863509(v=vs.105))하는 데 사용되는 것과 동일한 지침을 따릅니다.<br /><br /> 서비스 스냅인에서 **Hyper-V 가상 머신 관리** 서비스의 상태를 확인합니다.|
|Hyper-V를 실행해야 함|서비스 관리에 대한 자세한 내용은 다음 항목을 참조합니다.<br /><br /> -   [서비스 시작, 중지, 일시 중지, 계속 또는 다시 시작](https://technet.microsoft.com/library/cc736564\(v=WS.10\).aspx)<br />-   [서비스 시작 방법 구성](https://technet.microsoft.com/%20library/cc739213\(v=ws.10\))|

 로컬 Hyper-V Administrators 그룹의 구성원이어야 합니다.

 권한을 높이라는 메시지가 되풀이되는 일 없이 Android용 Visual Studio 에뮬레이터를 실행하려면 로컬 Hyper-V Administrators 그룹의 구성원이어야 합니다. SDK를 설치할 때 이미 컴퓨터의 로컬 관리자인 경우 SDK용 설치 프로그램에 의해 Hyper-V Administrators 그룹에 추가됩니다. 구성되지 않은 경우 수동으로 이 요구 사항을 설정해야 할 수도 있습니다.

 아직 Hyper-V Administrators 그룹의 구성원이 아닌 경우에는 에뮬레이터를 실행하면 해당 그룹에 참여하라는 메시지가 표시됩니다(대화 상자는 Windows Phone 에뮬레이터를 참조함). 그룹에 참여하려면 관리자 권한이 필요합니다.

> [!IMPORTANT]
> 그룹에 참여한 후에는 로그오프하거나 다시 부팅하여 변경 내용을 적용합니다.

 ![Hyper&#45;V 관리자 보안 그룹에 가입](../cross-platform/media/android_emu_hyperv_admin.png "Android_Emu_HyperV_Admin")

 자신을 수동으로 그룹에 추가하려면 로컬 사용자 및 그룹 스냅인을 엽니다.

## <a name="running-the-emulator-from-a-bootable-vhd-is-not-supported"></a>부팅 가능한 VHD에서 에뮬레이터 실행은 지원되지 않음
 부팅 가능한 VHD에서 Windows를 실행하는 동안 Android용 Visual Studio 에뮬레이터에서 앱을 실행하려는 경우 에뮬레이터는 일반적으로 시작되는 데 몇 분 정도 걸리거나 시작되지 않습니다. 에뮬레이터를 시작하지 못하면 다음 메시지가 나타납니다. 앱을 배포하지 못했습니다. 다시 시도하세요.

 이 구성은 지원되지 않습니다. 관련된 문제에 대한 자세한 내용은 [Android용 Visual Studio 에뮬레이터 문제 해결](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)을 참조하세요.

## <a name="hyper-v-requires-uncompressed-and-unencrypted-files"></a>Hyper-V에 압축 및 암호화되지 않은 파일 필요
 NTFS 파일 시스템으로 구성된 하드 드라이브에서는 Hyper-V에 사용되는 가상 하드 디스크는 압축되지 않고 암호화되지 않아야 합니다. 다음 디렉터리가 압축 또는 암호화되지 않았는지 확인합니다.

- %localappdata%\Microsoft\XDE

- C:\Program Files (x86)\Microsoft Emulator Manager

- C:\Program Files (x86)\Microsoft Visual Studio Emulator for Android

- %localappdata%\Microsoft\VisualStudioEmulator

ReFS 파일 시스템에서는 가상 하드 디스크 파일에 무결성 비트가 설정되어 있지 않아야 합니다.

## <a name="hardware-graphics-forwarding-opengl-es-support-requirements"></a>하드웨어 그래픽 전달(OpenGL ES 지원) 요구 사항

에뮬레이터가 OpenGL ES에서 사용되는 GPU 등에 대한 호출을 에뮬레이트하기 위해서는 컴퓨터에 적절한 DirectX 드라이버와 함께 DirectX 호환 GPU가 설치되어 있어야 합니다.

## <a name="see-also"></a>참조

- [Android용 Visual Studio 에뮬레이터 문제 해결](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
