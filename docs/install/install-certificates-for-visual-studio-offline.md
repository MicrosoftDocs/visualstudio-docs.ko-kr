---
title: 오프라인 설치에 필요한 인증서 설치
description: Visual Studio 오프라인 설치에 대한 인증서를 설치하는 방법을 알아봅니다.
ms.date: 08/08/2019
ms.custom: seodec18
ms.topic: how-to
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 525294d2cf3c33dfdb1c5796dabf1c2a7a78bf91
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85418810"
---
# <a name="install-certificates-required-for-visual-studio-offline-installation"></a>Visual Studio 오프라인 설치에 필요한 인증서 설치

Visual Studio는 많은 구성 요소가 정기적으로 업데이트되므로 주로 인터넷에 연결된 컴퓨터에서 설치하도록 설계되어 있습니다. 하지만 몇몇 추가 단계를 거치면 인터넷에 연결되지 않은 환경에 Visual Studio를 배포할 수 있습니다.

Visual Studio 설치 엔진은 신뢰할 수 있는 콘텐츠만 설치합니다. 이렇게 하려면 다운로드되는 콘텐츠의 Authenticode 시그니처를 확인하고 모든 콘텐츠를 신뢰할 수 있는지 검증한 후 설치합니다. 그러면 다운로드 위치를 손상시키는 공격으로부터 환경을 보호할 수 있습니다. 따라서 Visual Studio를 설치하려면 여러 표준 Microsoft 루트 및 중간 인증서가 사용자 컴퓨터에 설치되고 최신 상태로 유지되어야 합니다. 컴퓨터가 Windows 업데이트를 통해 최신 상태로 유지되면 서명 인증서는 일반적으로 최신 상태입니다. 컴퓨터가 인터넷에 연결되어 있는 경우 Visual Studio에서 설치 중에 파일 서명을 확인하는 데 필요한 인증서를 새로 고칠 수 있습니다. 시스템이 오프라인 상태인 경우 인증서는 다른 방법으로 새로 고쳐야 합니다.

## <a name="how-to-refresh-certificates-when-offline"></a>오프라인 상태인 경우 인증서를 새로 고치는 방법

오프라인 환경에서 인증서를 설치하거나 업데이트하는 세 가지 옵션이 있습니다.

### <a name="option-1---manually-install-certificates-from-a-layout-folder"></a>옵션 1 - 레이아웃 폴더에서 인증서를 수동으로 설치

::: moniker range="vs-2017"

네트워크 레이아웃을 만들면 필요한 인증서가 Certificates 폴더에 다운로드됩니다. 그러면 각 인증서 파일을 두 번 클릭하고 인증서 관리자 마법사를 통해 클릭하여 인증서를 수동으로 설치할 수 있습니다. 암호를 묻는 메시지가 표시되면 비워 두세요.

**업데이트**: Visual Studio 2017 버전 15.8 미리 보기 2 이상의 경우, 각 인증서 파일을 마우스 오른쪽 단추로 클릭하고 [인증서 설치]를 선택한 다음, [인증서 관리자] 마법사를 클릭하여 인증서를 수동으로 설치할 수 있습니다.

::: moniker-end

::: moniker range="vs-2019"

네트워크 레이아웃을 만들면 필요한 인증서가 Certificates 폴더에 다운로드됩니다. 각 인증서 파일을 마우스 오른쪽 단추로 클릭하고 인증서 설치를 선택한 다음, 인증서 관리자 마법사를 클릭하여 인증서를 수동으로 설치할 수 있습니다. 암호를 묻는 메시지가 표시되면 비워 두세요.

::: moniker-end

### <a name="option-2---distribute-trusted-root-certificates-in-an-enterprise-environment"></a>옵션 2 - 엔터프라이즈 환경에서 신뢰할 수 있는 루트 인증서 배포

최신 루트 인증서가 없는 오프라인 컴퓨터가 있는 엔터프라이즈의 경우 관리자는 [신뢰할 수 있는 루트 및 허용되지 않는 인증서 구성](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) 페이지의 지침에 따라 인증서를 업데이트할 수 있습니다.

### <a name="option-3---install-certificates-as-part-of-a-scripted-deployment-of-visual-studio"></a>옵션 3 - Visual Studio 스크립트 배포의 일부로 인증서 설치

오프라인 환경에서 클라이언트 워크스테이션에 대한 Visual Studio 배포를 스크립팅할 경우 다음 단계를 수행해야 합니다.

::: moniker range="vs-2017"

1. [인증서 관리자 도구](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool)(certmgr.exe)를 설치 공유(예: \\server\share\vs2017)에 복사합니다. certmgr.exe는 Windows 자체의 일부로 포함되지 않지만 [Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)의 일부로 제공됩니다.

2. 다음 명령으로 배치 파일을 만듭니다.

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA

   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

   **업데이트**: Visual Studio 2017 버전 15.8 미리 보기 2 이상의 경우, 다음 명령을 사용하여 일괄 처리 파일을 만듭니다.

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   또는 다음 명령을 사용하여 Windows와 함께 제공되는 certutil.exe를 사용하는 일괄 처리 파일을 만듭니다.
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. 일괄 처리 파일을 클라이언트에 배포합니다. 이 명령은 관리자 권한 프로세스에서 실행되어야 합니다.

::: moniker-end

::: moniker range="vs-2019"

1. [인증서 관리자 도구](/dotnet/framework/tools/certmgr-exe-certificate-manager-tool)(certmgr.exe)를 설치 공유(예: \\server\share\vs2019)에 복사합니다. certmgr.exe는 Windows 자체의 일부로 포함되지 않지만 [Windows SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk)의 일부로 제공됩니다.

2. 다음 명령으로 배치 파일을 만듭니다.

   ```cmd
   certmgr.exe -add [layout path]\certificates\manifestRootCertificate.cer -n "Microsoft Root Certificate Authority 2011" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\manifestCounterSignRootCertificate.cer -n "Microsoft Root Certificate Authority 2010" -s -r LocalMachine root

   certmgr.exe -add [layout path]\certificates\vs_installer_opc.RootCertificate.cer -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```
   
   또는 다음 명령을 사용하여 Windows와 함께 제공되는 certutil.exe를 사용하는 일괄 처리 파일을 만듭니다.
   
      ```cmd
   certutil.exe -addstore -f "Root" "[layout path]\certificates\manifestRootCertificate.cer

   certutil.exe -addstore -f "Root" [layout path]\certificates\manifestCounterSignRootCertificate.cer"

   certutil.exe -addstore -f "Root" "[layout path]\certificates\vs_installer_opc.RootCertificate.cer"
   ```

3. 일괄 처리 파일을 클라이언트에 배포합니다. 이 명령은 관리자 권한 프로세스에서 실행되어야 합니다.

::: moniker-end

## <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Certificates 폴더에 있는 인증서 파일은 무엇인가요?

::: moniker range="vs-2017"

이 폴더에 있는 세 개의 .P12 파일 각각에는 중간 인증서와 루트 인증서가 포함되어 있습니다. Windows 업데이트로 최신 상태가 유지되는 시스템은 대부분 이러한 인증서가 이미 설치되어 있습니다.

* **ManifestSignCertificates.p12**는 다음을 포함합니다.
  * 중간 인증서: **Microsoft Code Signing PCA 2011**
    * 필요하지 않습니다. 일부 시나리오(있는 경우)에서 성능을 향상합니다.
  * 루트 인증서: **Microsoft Root Certificate Authority 2011**
    * 최신 Windows 업데이트가 설치되지 않은 Windows 7 서비스 팩 1 시스템에 필요합니다.
* **ManifestCounterSignCertificates.p12**는 다음을 포함합니다.
  * 중간 인증서: **Microsoft Time-Stamp PCA 2010**
    * 필요하지 않습니다. 일부 시나리오(있는 경우)에서 성능을 향상합니다.
  * 루트 인증서: **Microsoft Root Certificate Authority 2010**
    * 최신 Windows 업데이트가 설치되지 않은 Windows 7 서비스 팩 1 시스템에 필요합니다.
* **Vs_installer_opc.SignCertificates.p12**는 다음을 포함합니다.
  * 중간 인증서: **Microsoft Code Signing PCA**
    * 모든 시스템에 필요합니다. Windows 업데이트의 모든 업데이트가 적용된 시스템에는 이 인증서가 없을 수 있습니다.
  * 루트 인증서: **Microsoft Root Certificate Authority**
    * 필수 사항입니다. 이 인증서는 Windows 7 이상을 실행하는 시스템과 함께 제공됩니다.

**업데이트**: Visual Studio 2017 버전 15.8 미리 보기 2 이상의 경우, Visual Studio 설치 관리자에서는 시스템에 루트 인증서만 설치해야 합니다. 이러한 인증서는 .p12 대신 .cer 파일에 저장됩니다.

::: moniker-end

::: moniker range="vs-2019"

* **ManifestSignCertificates.cer**은 다음을 포함합니다.
  * 루트 인증서: **Microsoft Root Certificate Authority 2011**
    * 최신 Windows 업데이트가 설치되지 않은 Windows 7 서비스 팩 1 시스템에 필요합니다.
* **ManifestCounterSignCertificates.cer**은 다음을 포함합니다.
  * 루트 인증서: **Microsoft Root Certificate Authority 2010**
    * 최신 Windows 업데이트가 설치되지 않은 Windows 7 서비스 팩 1 시스템에 필요합니다.
* **Vs_installer_opc.SignCertificates.cer**은 다음을 포함합니다.
  * 루트 인증서: **Microsoft Root Certificate Authority**
    * 필수 사항입니다. 이 인증서는 Windows 7 이상을 실행하는 시스템과 함께 제공됩니다.

Visual Studio 설치 관리자에서는 시스템에 루트 인증서만 설치해야 합니다.

::: moniker-end

## <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Certificates 폴더의 인증서가 자동으로 설치되지 않는 이유는 무엇인가요?

시그니처가 온라인 환경에서 검증되면 Windows API를 사용하여 인증서를 다운로드하고 시스템에 추가합니다. 인증서가 신뢰할 수 있고 관리 설정을 통해 허용되는지에 대한 검증이 이 프로세스 중에 수행됩니다. 대부분의 오프라인 환경에서는 이 검증 프로세스를 수행할 수 없습니다. 인증서를 수동으로 설치하면 엔터프라이즈 관리자는 인증서가 신뢰할 수 있고 조직의 보안 정책을 충족하는지 확인할 수 있습니다.

## <a name="checking-if-certificates-are-already-installed"></a>인증서가 설치되어 있는지 확인

설치하는 시스템을 확인할 한 가지 방법은 다음 단계를 수행하는 것입니다.

1. **mmc.exe**를 실행합니다.<br/>
  a. **파일**을 클릭한 다음, **스냅인 추가/제거**를 선택합니다.<br/>
  b. **인증서**를 두 번 클릭하고, **컴퓨터 계정**을 선택하고 **다음**을 클릭합니다.<br/>
  다. **로컬 컴퓨터**를 선택하고, **마침**을 클릭하고, **확인**을 클릭합니다.<br/>
  d. **인증서(로컬 컴퓨터)** 를 확장합니다.<br/>
  e. **신뢰할 수 있는 루트 인증 기관**을 확장하고 **인증서**를 선택합니다.<br/>
    * 이 목록에서 필요한 루트 인증서를 확인합니다.<br/>

   f. **중간 인증 기관**을 확장하고 **인증서**를 선택합니다.<br/>
    * 이 목록에서 필요한 중간 인증서를 확인합니다.<br/>

2. **파일**을 클릭한 다음, **스냅인 추가/제거**를 선택합니다.<br/>
  a. **인증서**를 두 번 클릭하고, **내 사용자 계정**을 선택하고, **마침**, **확인**을 차례로 클릭합니다.<br/>
  b. **인증서 – 현재 사용자**를 확장합니다.<br/>
  다. **중간 인증 기관**을 확장하고 **인증서**를 선택합니다.<br/>
    * 이 목록에서 필요한 중간 인증서를 확인합니다.<br/>

인증서 이름이 **발급 대상** 열에 없는 경우 이러한 인증서를 설치해야 합니다.  중간 인증서가 **현재 사용자** 중간 인증서 저장소에만 있는 경우 로그인한 사용자만 해당 인증서를 사용할 수 있습니다. 다른 사용자를 위해 설치해야 할 수도 있습니다.

## <a name="install-visual-studio"></a>Visual Studio 설치

인증서가 설치되면 "Visual Studio의 네트워크 설치 만들기" 페이지에 있는 [네트워크 설치에서 배포](create-a-network-installation-of-visual-studio.md#deploy-from-a-network-installation) 섹션의 지침에 따라 Visual Studio 배포를 진행할 수 있습니다.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 설치](install-visual-studio.md)
* [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
* [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 작업 및 구성 요소 ID](workload-and-component-ids.md)
