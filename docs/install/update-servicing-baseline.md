---
title: 서비스 기준선에서 Visual Studio 업데이트
description: 서비스 기준선에서 Visual Studio를 업데이트하는 방법을 알아보세요.
ms.date: 07/17/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9f31a3f7ae5e0e0ca4150d88870b9e48493bffcc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114966"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>서비스 기준선에서 Visual Studio 업데이트

제품 수명 주기 동안 Visual Studio를 자주 업데이트합니다. 업데이트에는 다음과 같은 두 가지 유형이 있습니다. 

* **부 릴리스 업데이트**(예: 새 기능 및 구성 요소가 포함된 16.0~16.1)  
* **서비스 업데이트**(예: 중요 문제로 수정 대상이 된 사항만 포함된 16.0.4~16.0.5)

엔터프라이즈 관리자는 해당 클라이언트를 서비스 기준선에 유지할 수 있습니다. 서비스 기준선은 다음 서비스 기준선의 릴리스 이후 1년 동안 서비스 업데이트와 함께 지원됩니다.

서비스 기준선 옵션으로 개발자와 관리자는 새로운 기능, 버그 수정 또는 새로운 부분 업데이트에 포함된 구성 요소를 더욱 유연하게 채택할 수 있습니다. 첫 번째 서비스 기준선은 16.0.x입니다. 자세한 내용은 [Enterprise 및 Professional 고객을 위한 지원 옵션](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers)을 참조하세요.

## <a name="how-to-get-onto-a-servicing-baseline"></a>서비스 기준선을 확인하는 방법

서비스 기준선 사용을 시작하려면 최종 버전의 Visual Studio 설치 관리자 부트스트래퍼를 [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0)에서 다운로드합니다. 이러한 부트스트래퍼에는 제품 구성, 워크로드 및 해당 특정 버전의 구성 요소에 대한 링크가 있습니다.

> [!NOTE]
> 최종 버전의 부트스트래퍼와 표준 부트스트래퍼를 구분해야 합니다. 표준 부트스트래퍼는 Visual Studio의 최신 릴리스를 사용하도록 구성됩니다. 표준 부트스트래퍼는 My.VisualStudio.com에서 다운로드할 때 파일 이름에 숫자가 있습니다(예: vs_enterprise__123456789-123456789.exe).

설치하는 동안 엔터프라이즈 관리자는 클라이언트가 최신 릴리스로 업데이트되지 않도록 구성해야 합니다. 다음과 같은 여러 가지 방법으로 이 작업을 수행할 수 있습니다.
- [레이아웃 또는 로컬 폴더에서 채널 매니페스트를 사용하도록 응답 구성 파일](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network)의 `channelUri` 설정을 변경합니다.
- [존재하지 않는 파일을 사용하도록 명령줄을 실행](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet)하여 channelUri를 수정합니다.
- [클라이언트가 자동 업데이트되지 않도록 클라이언트 시스템에서 업데이트](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating)를 사용하지 않도록 정책을 설정합니다.

### <a name="install-a-servicing-baseline-on-a-network"></a>네트워크에 서비스 기준선 설치

네트워크 레이아웃 설치를 사용하는 관리자는 동일한 폴더에 있는 *channelmanifest.json* 파일을 사용하도록 레이아웃의 *response.json* 파일에서 `channelUri` 값을 수정해야 합니다. 실행 단계는 [네트워크 기반 Visual Studio 배포에 대한 업데이트 제어](controlling-updates-to-visual-studio-deployments.md)를 참조하세요. `channelUri` 값을 변경하면 클라이언트가 레이아웃 위치에서 업데이트를 검색할 수 있습니다.

### <a name="install-a-servicing-baseline-via-the-internet"></a>인터넷을 통해 서비스 기준선 설치

인터넷 기반 설치인 경우 존재하지 않는 채널 매니페스트를 포함한 `--channelUri`를 설치 시작에 사용되는 명령줄에 추가합니다. 그러면 Visual Studio는 업데이트에 대한 최신 릴리스를 사용할 수 없게 됩니다. 예를 들면 다음과 같습니다.

```cmd
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>정책 설정을 사용하여 클라이언트가 업데이트되지 않도록 설정

클라이언트에서 업데이트를 제어하는 또 다른 옵션은 [업데이트 알림 끄기](controlling-updates-to-visual-studio-deployments.md)입니다. 설치 시 channelUri 값이 변경되지 않으면 이 옵션을 사용합니다. 그러면 클라이언트는 최신 릴리스에 대한 링크를 수신하지 못하게 됩니다. 그래도 최종 버전 부트스트래퍼는 클라이언트에서 특정 버전으로 업데이트해야 합니다.

## <a name="how-to-stay-on-a-servicing-baseline"></a>서비스 기준선에서 유지하는 방법

서비스 기준선에 대한 업데이트가 있는 경우 [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0)에서 서비스 업데이트에 대한 최종 버전 부트스트래퍼 파일을 사용할 수 있습니다.

네트워크 레이아웃 설치를 통해 배포하는 관리자의 경우 [레이아웃 위치](update-a-network-installation-of-visual-studio.md)를 업데이트해야 합니다. 이 위치에서 설치된 클라이언트는 업데이트 알림을 받게 됩니다. 업데이트를 클라이언트에 배포해야 하는 경우에는 [이 지침](update-a-network-installation-of-visual-studio.md#deploy-an-update-to-client-machines)을 따릅니다. 업데이트에 대한 ‘response.json’을 수정하는 경우 추가 워크로드, 구성 요소 또는 언어를 추가하지 마십시오. 제품이 업데이트된 후에는 이러한 설정의 관리가 ‘수정’ 배포로 이루어져야 합니다.

인터넷 기반 설치인 경우에는 클라이언트에 존재하지 않는 채널 매니페스트를 가리키는 `--channelUri` 매개 변수로 새로운 최종 버전 부트스트래퍼를 실행합니다. 업데이트를 자동 또는 수동 모드에서 배포하는 경우에 두 가지 명령을 사용합니다.

1. Visual Studio 설치 관리자 업데이트:

    ```cmd
    vs_enterprise.exe --quiet --update
    ```

2. Visual Studio 애플리케이션 자체 업데이트:

    ```cmd
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 설치](install-visual-studio.md)
* [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
* [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 인스턴스 검색 및 관리 도구](tools-for-managing-visual-studio-instances.md)
* [지시 파일에서 설정을 정의하는 방법](automated-installation-with-response-file.md)
* [네트워크 기반 Visual Studio 배포에 대한 업데이트 제어](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio 제품 수명 주기 및 서비스](/visualstudio/releases/2019/servicing/)
