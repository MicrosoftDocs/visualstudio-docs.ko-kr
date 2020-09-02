---
title: Windows 스토어 앱 배포
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73b4350a2e7f277a11f4d6650d8089df0f87fe4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177457"
---
# <a name="deploy-windows-store-apps-from-visual-studio"></a>Visual Studio에서 Windows 스토어 앱 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows에만 적용 됨] (. /Image/windows_only_content.png "windows_only_content")

 Visual Studio 배포 기능은 대상 디바이스에서 Visual Studio로 만든 Windows 스토어 앱을 빌드 및 등록합니다. 정확히 앱이 등록되는 방법은 대상 디바이스가 로컬 디바이스인지 원격 디바이스인지에 따라 달라집니다.

- 대상이 로컬 Visual Studio 컴퓨터인 경우 Visual Studio는 빌드 폴더에서 앱을 등록합니다.

- 대상이 원격 디바이스인 경우 Visual Studio에서는 원격 컴퓨터로 필수 파일을 복사한 다음 해당 디바이스에서 앱을 등록합니다.

  **디버깅 시작** 옵션(키보드: F5) 또는 **디버그하지 않고 시작** 옵션(키보드: Ctrl+F5)을 사용하면 Visual Studio에서 앱을 디버그할 때 자동 배포가 수행됩니다. 또한 앱을 수동으로 배포할 수도 있습니다. 수동 배포는 다음 시나리오에서 유용합니다.

- 로컬 또는 원격 컴퓨터에서 애드혹 테스트

- 디버깅하려는 다른 앱을 시작할 앱 배포

- 다른 앱 또는 메서드에서 시작되는 경우 디버깅할 앱 배포

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> 항목 내용
 이 항목에서는 다음과 같은 내용을 배울 수 있습니다.

 [Windows 스토어 앱을 배포 하는 방법](#BKMK_How_to_deploy_a_Windows_Store_app)

 [원격 장치를 지정 하는 방법](#BKMK_How_to_specify_a_remote_device)

 [배포 옵션](#BKMK_Deployment_options)

## <a name="how-to-deploy-a-windows-store-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Windows 스토어 앱을 배포하는 방법
 수동 앱 배포 프로세스는 다음과 같이 간단합니다.

1. 원격 디바이스에 배포하는 경우 앱 시작 프로젝트의 속성 프로젝트 페이지에서 디바이스의 이름 또는 IP 주소를 지정합니다. 이 작업 단계는 이 항목 아래에 나열되어 있습니다.

2. 디버거 Visual Studio 도구 모음의 **디버깅 시작** 단추 옆에 있는 드롭다운 목록에서 배포 대상을 선택합니다.

     ![로컬 머신에서 실행](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")

3. **빌드** 메뉴에서 **배포**를 선택합니다.

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> 원격 디바이스 지정 방법
 **필수 구성 요소**

 원격 디바이스에 앱을 배포하려면

- 원격 디바이스에 개발자 라이선스가 설치되어 있어야 합니다.

- Visual Studio 원격 도구는 원격 디바이스에 설치해야 하고 원격 디버깅 모니터가 실행 중이어야 합니다.

     배포 시 원격 디버거 네트워크 채널을 사용하여 원격 디바이스로 앱 파일을 보냅니다.

#### <a name="to-specify-a-remote-device"></a>원격 디바이스를 지정하는 방법

1. 시작 프로젝트의 디버그 속성 페이지에서 원격 배포 대상의 이름 또는 IP 주소를 지정합니다.

2. 디버그 속성 페이지를 열려면 솔루션 탐색기에서 프로젝트를 선택한 다음 바로 가기 메뉴에서 **속성** 을 선택합니다.

3. 그런 다음 속성 페이지 창에서 **디버그** 노드를 선택합니다.

4. 원격 디바이스의 이름 또는 IP 주소를 입력하거나 **원격 디버거 연결 선택** 대화 상자에서 디바이스를 선택할 수 있습니다.

    ![원격 디버거 연결 선택 대화 상자](../debugger/media/vsrun-selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    **원격 디버거 연결 선택** 대화 상자에는 로컬 네트워크 서브넷에 있는 디바이스와 이더넷 케이블을 통해 Visual Studio 컴퓨터에 직접 연결되어 있는 디바이스가 표시됩니다.

   **JavaScript 또는 Visual C++ 프로젝트 페이지에서 원격 디바이스 지정**

   ![원격 디버깅에 대한 C&#43;&#43; 프로젝트 속성](../debugger/media/vsrun-cpp-projprop-remote.png "VSRUN_CPP_ProjProp_Remote")

5. **실행할 디버거** 목록에서 **원격 디버거** 를 선택합니다.

6. **컴퓨터 이름** 상자에 원격 디바이스의 네트워크 이름을 입력합니다. 또는 상자에서 아래쪽 화살표를 선택하여 원격 디버거 연결 선택 대화 상자에서 디바이스를 선택할 수 있습니다.

   **Visual C# 및 Visual Basic 프로젝트 페이지에서 원격 디바이스 지정**

   ![원격 디버깅의 관리형 프로젝트 속성](../debugger/media/vsrun-managed-projprop-remote.png "VSRUN_Managed_ProjProp_Remote")

7. **대상 디바이스** 목록에서 **원격 컴퓨터** 를 선택합니다.

8. **원격 컴퓨터** 상자에 원격 디바이스의 네트워크 이름을 입력하거나 **찾기** 를 클릭하여 **원격 디버거 연결 선택** 대화 상자에서 디바이스를 선택합니다.

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> 배포 옵션
 시작 프로젝트의 디버그 속성 페이지에서 다음 배포 옵션을 설정할 수 있습니다.

 **네트워크 루프백 허용** 보안상의 이유로, [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 표준 방식으로 설치 된 앱은 설치 된 장치에 대 한 네트워크 호출을 수행할 수 없습니다. 기본적으로 Visual Studio를 배포하면 배포된 응용 프로그램에 대한 이 규칙의 예외가 만들어 집니다. 이 예외로 인해 사용자는 단일 컴퓨터에서 통신 프로시저를 테스트할 수 있습니다. 앱을 [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]에 제출하기 전에 이 예외 없이 앱을 테스트해야 합니다.

 앱에서 네트워크 루프백 예외를 제거하려면

- C# 및 VB 디버그 속성 페이지에서 **네트워크 루프백 허용** 확인란을 선택 취소합니다.

- JavaScript 및 디버그 속성 페이지에서 **네트워크 루프백 허용** 값을 **아니요**로 설정합니다.

  시작 **하지 않음 (시작 시 코드 디버그) (c # 및 VB)/응용 프로그램 시작 (JavaScript 및 c + +)** 앱이 시작 될 때 디버깅 세션을 자동으로 시작 하도록 배포를 구성 하려면:

- C# 및 VB 디버그 속성 페이지에서 **시작하지 않음(시작 시 코드 디버그)** 확인란을 선택합니다.

- JavaScript 및 디버그 속성 페이지에서 **애플리케이션 시작** 값을 **예**로 설정합니다.

## <a name="see-also"></a>관련 항목
 [Visual Studio에서 앱 실행](../debugger/run-store-apps-from-visual-studio.md)
