---
title: '방법: 응용 프로그램 및 배포 매니페스트에 다시 서명 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc69ce1f79644d7f4b35fbb1c1e3a41691761390
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649181"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>방법: 애플리케이션 및 배포 매니페스트 다시 서명
Windows Forms 응용 프로그램, Windows 프레젠테이션 파운데이션(xbap) 또는 Office 솔루션에 대한 응용 프로그램 매니페스트에서 배포 속성을 변경한 후 응용 프로그램 및 배포 매니페스트를 인증서로 다시 서명해야 합니다. 이 프로세스를 수행하면 최종 사용자 컴퓨터에 훼손된 파일이 설치되지 않습니다.

 매니페스트에 다시 서명할 수 있는 또 다른 시나리오는 고객이 자체 인증서로 응용 프로그램 및 배포 매니페스트에 서명하려는 경우입니다.

## <a name="re-sign-the-application-and-deployment-manifests"></a>애플리케이션 및 배포 매니페스트 다시 서명
 이 절차에서는 응용 프로그램 매니페스트*파일(.manifest)을*이미 변경했다고 가정합니다. 자세한 내용은 [배포 속성 변경 방법을 참조하세요.](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472)

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Mage.exe를 사용하여 응용 프로그램 및 배포 매니페스트에 다시 서명하려면

1. 시각적 **스튜디오 명령 프롬프트** 창을 엽니다.

2. 서명할 매니페스트 파일이 포함된 폴더로 디렉터리를 변경합니다.

3. 다음 명령을 입력하여 응용 프로그램 매니페스트 파일에 서명합니다. *ManifestFileName을* 매니페스트 파일의 이름과 확장명으로 바꿉니다. *인증서를 인증서* 파일의 상대적 또는 정규화된 경로로 바꾸고 *암호를* 인증서의 암호로 바꿉습니다.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     예를 들어 다음 명령을 실행하여 추가 기능, Windows Form 응용 프로그램 또는 Windows 프레젠테이션 기반 브라우저 응용 프로그램에 대한 응용 프로그램 매니페스트에 서명할 수 있습니다. Visual Studio에서 만든 임시 인증서는 프로덕션 환경에 배포하는 데 권장되지 않습니다.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. 배포 매니페스트 파일을 업데이트하고 서명할 다음 명령을 입력하여 이전 단계에서와 같이 자리 표시자 이름을 대체합니다.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     예를 들어 다음 명령을 실행하여 Excel 추가 기능, Windows Forms 응용 프로그램 또는 Windows 프레젠테이션 기반 브라우저 응용 프로그램에 대한 배포 매니페스트를 업데이트하고 서명할 수 있습니다.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. 선택적으로 마스터 배포*\\\<매니페스트(응용 프로그램 이름>.application)를*버전 배포 디렉토리(publish\Application*Files\\\<앱 이름>_>\< *버전)에 복사합니다.

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>응용 프로그램 및 배포 매니페스트 업데이트 및 다시 서명
 이 절차에서는 응용 프로그램 매니페스트*파일(.manifest)을*이미 변경했지만 업데이트된 다른 파일이 있다고 가정합니다. 파일이 업데이트되면 파일을 나타내는 해시도 업데이트해야 합니다.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Mage.exe를 사용하여 응용 프로그램 및 배포 매니페스트를 업데이트하고 다시 서명하려면

1. 시각적 **스튜디오 명령 프롬프트** 창을 엽니다.

2. 서명할 매니페스트 파일이 포함된 폴더로 디렉터리를 변경합니다.

3. 게시 출력 폴더의 파일에서 파일 확장자 *.deploy를* 제거합니다.

4. 다음 명령을 입력하여 업데이트된 파일에 대한 새 해시로 응용 프로그램 매니페스트를 업데이트하고 응용 프로그램 매니페스트 파일에 서명합니다. *ManifestFileName을* 매니페스트 파일의 이름과 확장명으로 바꿉니다. *인증서를 인증서* 파일의 상대적 또는 정규화된 경로로 바꾸고 *암호를* 인증서의 암호로 바꿉습니다.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     예를 들어 다음 명령을 실행하여 추가 기능, Windows Form 응용 프로그램 또는 Windows 프레젠테이션 기반 브라우저 응용 프로그램에 대한 응용 프로그램 매니페스트에 서명할 수 있습니다. Visual Studio에서 만든 임시 인증서는 프로덕션 환경에 배포하는 데 권장되지 않습니다.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. 배포 매니페스트 파일을 업데이트하고 서명할 다음 명령을 입력하여 이전 단계에서와 같이 자리 표시자 이름을 대체합니다.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     예를 들어 다음 명령을 실행하여 Excel 추가 기능, Windows Forms 응용 프로그램 또는 Windows 프레젠테이션 기반 브라우저 응용 프로그램에 대한 배포 매니페스트를 업데이트하고 서명할 수 있습니다.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. 응용 프로그램 및 배포 매니페스트 파일을 제외한 *.deploy* 파일 확장프로그램을 파일에 다시 추가합니다.

7. 선택적으로 마스터 배포*\\\<매니페스트(응용 프로그램 이름>.application)를*버전 배포 디렉토리(publish\Application*Files\\\<앱 이름>_>\< *버전)에 복사합니다.

## <a name="see-also"></a>참고 항목
- [ClickOnce 애플리케이션 보안](../deployment/securing-clickonce-applications.md)
- [ClickOnce 애플리케이션의 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce 및 Authenticode](../deployment/clickonce-and-authenticode.md)
- [신뢰할 수 있는 애플리케이션 배포 개요](../deployment/trusted-application-deployment-overview.md)
- [방법: ClickOnce 보안 설정 사용](../deployment/how-to-enable-clickonce-security-settings.md)
- [방법: ClickOnce 애플리케이션의 보안 영역 설정](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [방법: ClickOnce 애플리케이션의 사용자 지정 권한 설정](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [방법: 제한된 권한으로 ClickOnce 애플리케이션 디버그](securing-clickonce-applications.md)
- [방법: ClickOnce 애플리케이션의 클라이언트 컴퓨터에 신뢰할 수 있는 게시자 추가](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [방법: ClickOnce 신뢰 프롬프트 동작 구성](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)