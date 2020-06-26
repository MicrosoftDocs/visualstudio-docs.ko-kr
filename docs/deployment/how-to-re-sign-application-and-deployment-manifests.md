---
title: 응용 프로그램 및 배포 매니페스트에 다시 서명 하는 방법 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 1905ea32a9899a1262e146f264e0a1179f0e8c6e
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382200"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>방법: 애플리케이션 및 배포 매니페스트 다시 서명
Windows Forms 응용 프로그램, xbap (Windows Presentation Foundation 응용 프로그램) 또는 Office 솔루션에 대 한 응용 프로그램 매니페스트에서 배포 속성을 변경한 후에는 인증서를 사용 하 여 응용 프로그램 및 배포 매니페스트에 모두 다시 서명 해야 합니다. 이 프로세스를 수행하면 최종 사용자 컴퓨터에 훼손된 파일이 설치되지 않습니다.

 매니페스트에 다시 서명할 수 있는 또 다른 시나리오는 고객이 자신의 인증서를 사용 하 여 응용 프로그램 및 배포 매니페스트에 서명 하려고 할 때입니다.

## <a name="re-sign-the-application-and-deployment-manifests"></a>애플리케이션 및 배포 매니페스트 다시 서명
 이 절차에서는 응용 프로그램 매니페스트 파일 (*.manifest*)을 이미 변경한 것으로 가정 합니다. 자세한 내용은 [방법: 배포 속성 변경](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472)을 참조 하세요.

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Mage.exe를 사용 하 여 응용 프로그램 및 배포 매니페스트에 다시 서명 하려면

1. **Visual Studio 명령 프롬프트** 창을 엽니다.

2. 서명 하려는 매니페스트 파일이 포함 된 폴더로 디렉터리를 변경 합니다.

3. 다음 명령을 입력 하 여 응용 프로그램 매니페스트 파일에 서명 합니다. *ManifestFileName* 을 매니페스트 파일의 이름 및 확장명으로 바꿉니다. 인증서 *를* 인증서 파일의 상대 또는 정규화 된 경로로 바꾸고 *password* 를 인증서의 암호로 바꿉니다.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     예를 들어 다음 명령을 실행 하 여 추가 기능, Windows Form 응용 프로그램 또는 Windows Presentation Foundation 브라우저 응용 프로그램에 대 한 응용 프로그램 매니페스트에 서명할 수 있습니다. 프로덕션 환경에 배포 하는 경우 Visual Studio에서 만든 임시 인증서를 권장 하지 않습니다.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. 다음 명령을 입력 하 여 배포 매니페스트 파일을 업데이트 및 서명 하 고 이전 단계에서와 같이 자리 표시자 이름을 바꿉니다.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     예를 들어 다음 명령을 실행 하 여 Excel 추가 기능, Windows Forms 응용 프로그램 또는 Windows Presentation Foundation 브라우저 응용 프로그램에 대 한 배포 매니페스트를 업데이트 하 고 서명할 수 있습니다.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. 필요에 따라 마스터 배포 매니페스트 (*publish \\ \<appname> . application*)를 버전 배포 디렉터리 (*publish\Application Files \\ \<appname> _ \<version> *)에 복사 합니다.

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>응용 프로그램 및 배포 매니페스트 업데이트 및 다시 서명
 이 절차에서는 응용 프로그램 매니페스트 파일 (*.manifest*)을 이미 변경 했지만 업데이트 된 다른 파일이 있는 것으로 가정 합니다. 파일이 업데이트 되 면 파일을 나타내는 해시도 업데이트 해야 합니다.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Mage.exe를 사용 하 여 응용 프로그램 및 배포 매니페스트를 업데이트 하 고 다시 서명 하려면

1. **Visual Studio 명령 프롬프트** 창을 엽니다.

2. 서명 하려는 매니페스트 파일이 포함 된 폴더로 디렉터리를 변경 합니다.

3. 게시 출력 폴더의 파일에서 *.deploy* 파일 확장명을 제거 합니다.

4. 업데이트 된 파일에 대 한 새 해시를 사용 하 여 응용 프로그램 매니페스트를 업데이트 하 고 응용 프로그램 매니페스트 파일에 서명 하려면 다음 명령을 입력 합니다. *ManifestFileName* 을 매니페스트 파일의 이름 및 확장명으로 바꿉니다. 인증서 *를* 인증서 파일의 상대 또는 정규화 된 경로로 바꾸고 *password* 를 인증서의 암호로 바꿉니다.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     예를 들어 다음 명령을 실행 하 여 추가 기능, Windows Form 응용 프로그램 또는 Windows Presentation Foundation 브라우저 응용 프로그램에 대 한 응용 프로그램 매니페스트에 서명할 수 있습니다. 프로덕션 환경에 배포 하는 경우 Visual Studio에서 만든 임시 인증서를 권장 하지 않습니다.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. 다음 명령을 입력 하 여 배포 매니페스트 파일을 업데이트 및 서명 하 고 이전 단계에서와 같이 자리 표시자 이름을 바꿉니다.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     예를 들어 다음 명령을 실행 하 여 Excel 추가 기능, Windows Forms 응용 프로그램 또는 Windows Presentation Foundation 브라우저 응용 프로그램에 대 한 배포 매니페스트를 업데이트 하 고 서명할 수 있습니다.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. 응용 프로그램 및 배포 매니페스트 파일을 제외 하 고 파일에 *.deploy* 파일 확장명을 다시 추가 합니다.

7. 필요에 따라 마스터 배포 매니페스트 (*publish \\ \<appname> . application*)를 버전 배포 디렉터리 (*publish\Application Files \\ \<appname> _ \<version> *)에 복사 합니다.

## <a name="see-also"></a>추가 정보
- [ClickOnce 애플리케이션 보안](../deployment/securing-clickonce-applications.md)
- [ClickOnce 애플리케이션의 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce 및 Authenticode](../deployment/clickonce-and-authenticode.md)
- [신뢰할 수 있는 애플리케이션 배포 개요](../deployment/trusted-application-deployment-overview.md)
- [방법: ClickOnce 보안 설정 사용](../deployment/how-to-enable-clickonce-security-settings.md)
- [방법: ClickOnce 응용 프로그램의 보안 영역 설정](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [방법: ClickOnce 응용 프로그램에 대 한 사용자 지정 권한 설정](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [방법: 제한된 권한으로 ClickOnce 애플리케이션 디버그](securing-clickonce-applications.md)
- [방법: ClickOnce 애플리케이션의 클라이언트 컴퓨터에 신뢰할 수 있는 게시자 추가](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [방법: ClickOnce 신뢰 프롬프트 동작 구성](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)