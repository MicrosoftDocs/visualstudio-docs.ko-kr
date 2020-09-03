---
title: 오프라인 설치 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a6a9707d517a8a43d9a9ca156a5f7291ecee9bee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81445066"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Visual Studio의 오프라인 설치 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 최신 설명서는 [Visual Studio의 오프라인 설치 만들기](/visualstudio/install/create-an-offline-installation-of-visual-studio) 또는 [Visual Studio의 네트워크 설치 만들기](/visualstudio/install/create-a-network-installation-of-visual-studio)를 참조하세요.

이 페이지에서는 인터넷에 연결되지 않았을 때 Visual Studio 2015를 설치하는 방법을 설명합니다. 그러나 “연결이 끊어진” 설치를 수행하려면 먼저 인터넷에 연결된 머신을 사용하여 오프라인 설치 레이아웃을 만들어야 합니다. 방법은 다음과 같습니다.

> [!IMPORTANT]
> 오프라인 머신에서 Windows 7 SP1 또는 Windows Server 2008 R2를 실행 중인 경우 이 항목의 [오프라인 설치 문제 해결](#BKMK_tshoot) 섹션에서 특별 지침을 참조하세요.  Visual Studio 2015를 설치하기 전에 이 지침을 따라야 합니다.

## <a name="installing-by-creating-an-offline-installation"></a><a name="BKMK_Offline"></a> 오프라인 설치를 만들어서 설치

#### <a name="to-create-an-offline-installation-layout"></a>오프라인 설치 레이아웃을 만들려면

1. [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) 다운로드 페이지에서 설치할 Visual Studio 버전을 선택합니다.

2. 파일 시스템의 위치에 설치 관리자를 다운로드 한 후에 " \<executable name> /layout"를 실행 합니다.

     예를 들어 다음을 실행합니다. `vs_enterprise.exe /layout D:\VisualStudio2015`

     `/layout` 스위치를 사용하면 다운로드 머신에 적용되는 패키지 외에도 거의 모든 설치 패키지를 다운로드할 수 있습니다. 이 방법을 사용하면 이 설치 관리자를 모든 위치에서 실행하는 데 필요한 파일을 받을 수 있으며 원래 설치되지 않은 구성 요소를 설치하려는 경우 유용할 수 있습니다.

3. 이 명령을 실행한 후 오프라인 설치 레이아웃을 저장할 폴더를 변경할 수 있는 대화 상자가 표시됩니다.   그런 다음 **다운로드** 단추를 클릭 합니다.

     패키지가 성공적으로 다운로드 되 면 설치 완료 라는 메시지가 표시 됩니다 **. 지정 된 모든 구성 요소를 가져왔습니다.**

4. 이전에 지정한 폴더를 찾습니다. (예를 들어 D:\VisualStudio2015.를 찾습니다.) 이 폴더에는 공유 위치로 복사 하거나 미디어를 설치 하는 데 필요한 모든 항목이 포함 되어 있습니다.

    > [!CAUTION]
    > 현재 Android SDK에는 오프라인 설치 환경을 지원하지 않습니다. 인터넷에 연결되지 않은 컴퓨터에서 Android SDK 설치 항목을 설치하면 설치가 실패할 수 있습니다. 자세한 내용은 이 항목의 “오프라인 설치 문제 해결” 섹션을 참조하세요.

5. 파일 위치 또는 설치 미디어에서 설치를 실행합니다.

## <a name="updating-an-offline-installation"></a>오프라인 설치 업데이트
 Microsoft에서는 여러 가지 Visual Studio 2015 업데이트를 릴리스했습니다. Visual Studio 설치를 업데이트하려면 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) 다운로드 페이지에서 원하는 버전을 다운로드하면 됩니다. 다음으로, 이 항목에 설명된 단계에 따라 새 오프라인 설치 레이아웃을 만들고 이 레이아웃을 사용하여 Visual Studio 2015를 업데이트합니다.

## <a name="troubleshooting-an-offline-installation"></a><a name="BKMK_tshoot"></a> 오프라인 설치 문제 해결
 오프라인 설치 캐시에서 오프라인으로 설치하는 경우 일부 구성 요소와 패키지를 설치할 수 없다는 경고 메시지가 표시될 수도 있습니다. 다음 표에는 이러한 시나리오에 대한 가능한 해결 방법이 포함되어 있습니다.

| 구성 요소 또는 패키지 | 해결 방법 |
|-|-|
| Dotfuscator 및 Analytics Community Edition 5.19.1(**Windows 7 SP1** 및 **Windows Server 2008 R2**에 설치된 Visual Studio Community, Professional 및 Enterprise Edition용) | 오프라인 머신에서 **Windows 7 SP1** 또는 **Windows Server 2008 R2**를 실행 중인 경우 Visual Studio 2015를 설치하기 전에 다음 단계를 수행해야 합니다.<br /><br /> 1. CTL 파일을 다운로드 하도록 파일 또는 웹 서버를 구성 합니다.<br /><br /> 2. 연결 되지 않은 환경에 대 한 Microsoft 자동 업데이트 URL을 리디렉션합니다.<br /><br /> 자세한 내용은 Microsoft TechNet 사이트에서 [Configure Trusted Roots and Disallowed Certificates](https://technet.microsoft.com/library/dn265983.aspx)(신뢰할 수 있는 루트 및 허용되지 않는 인증서 구성) 페이지를 참조하세요. |
| Android SDK 설치(API 수준) | Android SDK(API 수준) 패키지를 설치하려면 인터넷 연결이 있어야 합니다. 제한된 네트워크에 있는 경우 Visual Studio를 설치할 때 다음 URL에 대한 액세스를 허용해야 합니다.<br /><br /> -   `https://dl.google.com:443`<br />-   `https://dl-ssl.google.com:443`<br />-   `https://dl-ssl.google.com/android/repository/*`<br /> <br />가능한 프록시 설정 문제를 해결하는 방법에 대한 자세한 내용은 [프록시를 사용하는 Visual Studio 2015 설치 오류(Android SDK 설정)](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) 블로그 게시물을 참조하세요. |
| Visual Studio 확장성 항목 템플릿<br /><br /> Visual Studio용 GitHub 확장<br /><br /> PowerShell Tools for Visual Studio | Visual Studio 2015를 설치할 때 인터넷 연결이 없으면 특수 오프라인 피드를 사용하여 오프라인 설치 레이아웃을 생성할 수 있습니다. **참고:** 이 특수 피드에는 Visual Studio 2015의 최신 업데이트가 포함됩니다. <br /><br /> 특수 오프라인 피드를 만들려면 /layout *Drive:* \VisualStudio2015 /overridefeeduri *URL-to-feed-xml* 명령을 실행합니다.<br /><br /> 예를 들어 Visual Studio 2015 Enterprise용 영어 특수 오프라인 피드의 경우 다음을 실행합니다.<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "https://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> 선택한 언어의 특수 오프라인 피드를 만드는 데 사용할 수 있는 전체 URL 목록은 아래 표를 참조하세요. |

 다음 URL을 사용하여 위의 표에 설명된 대로 언어별 특수 오프라인 피드를 만듭니다.

|       언어        |                            URL                            |
|-----------------------|-----------------------------------------------------------|
| 중국어(간체)  | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| 중국어(번체) | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         체코어         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        독일어         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        영어        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        스페인어        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        프랑스어         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        이탈리아어        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       일본어        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        한국어         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        폴란드어         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      포르투갈어       | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        러시아어        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        터키어        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>관련 항목

- [Visual Studio 설치](install-visual-studio-2015.md)