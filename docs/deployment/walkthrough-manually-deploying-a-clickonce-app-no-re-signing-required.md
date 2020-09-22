---
title: 수동으로 ClickOnce 앱 배포 & 브랜딩 유지
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e3f21f9e377b7d3e2d71d499eed25079c7769c7
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809226"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>연습: 다시 서명할 필요가 없고 브랜딩 정보를 유지 하는 ClickOnce 응용 프로그램을 수동으로 배포
응용 프로그램을 만든 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 다음 게시 하 고 배포할 수 있도록 고객에 게 제공 하려면 일반적으로 배포 매니페스트를 업데이트 하 고 다시 서명 해야 했습니다. 대부분의 경우에는 여전히 선호 되는 방법 이지만 .NET Framework 3.5를 사용 하면 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 새 배포 매니페스트를 다시 생성 하지 않고도 고객이 배포할 수 있는 배포를 만들 수 있습니다. 자세한 내용은 다시 서명를 사용 [하지 않고 테스트 및 프로덕션 서버용 ClickOnce 응용 프로그램 배포](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)를 참조 하세요.

 응용 프로그램을 만든 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 다음 게시 하 고 배포 하도록 고객에 게 제공 하면 응용 프로그램은 고객의 브랜드를 사용 하거나 브랜딩을 유지할 수 있습니다. 예를 들어 응용 프로그램이 단일 소유 응용 프로그램 인 경우 브랜딩 유지를 원할 수 있습니다. 응용 프로그램이 각 고객에 대해 고도로 사용자 지정 된 경우 고객의 브랜드를 사용 하는 것이 좋습니다. .NET Framework 3.5를 사용 하면 배포할 조직에 응용 프로그램을 제공할 때 브랜딩, 게시자 정보 및 보안 서명을 유지할 수 있습니다. 자세한 내용은 [다른 사람이 배포할 ClickOnce 응용 프로그램 만들기](../deployment/creating-clickonce-applications-for-others-to-deploy.md)를 참조 하세요.

> [!NOTE]
> 이 연습에서는 명령줄 도구 *Mage.exe* 또는 그래픽 도구 *MageUI.exe*를 사용 하 여 배포를 수동으로 만듭니다. 수동 배포에 대 한 자세한 내용은 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)를 참조 하세요.

## <a name="prerequisites"></a>사전 요구 사항
 이 연습의 단계를 수행 하려면 다음이 필요 합니다.

- 배포할 준비가 된 Windows Forms 응용 프로그램입니다. 이 응용 프로그램은 *WindowsFormsApp1*라고 합니다.

- Visual Studio 또는 Windows SDK입니다.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Mage.exe를 사용 하 여 여러 배포 및 브랜딩 지원으로 ClickOnce 응용 프로그램을 배포 하려면

1. Visual Studio 명령 프롬프트 또는 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 명령 프롬프트를 열고 파일을 저장할 디렉터리로 변경 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 합니다.

2. 배포의 현재 버전에 따라 이름이 인 디렉터리를 만듭니다. 응용 프로그램을 처음 배포 하는 경우 **1.0.0.0**을 선택 하는 것이 좋습니다.

   > [!NOTE]
   > 배포 버전이 응용 프로그램 파일의 버전과 다를 수 있습니다.

3. **Bin** 이라는 하위 디렉터리를 만들고 실행 파일, 어셈블리, 리소스 및 데이터 파일을 포함 하 여 여기에 모든 응용 프로그램 파일을 복사 합니다.

4. Mage.exe에 대 한 호출을 사용 하 여 응용 프로그램 매니페스트를 생성 합니다.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. 디지털 인증서를 사용 하 여 응용 프로그램 매니페스트에 서명 합니다.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. *Mage.exe*에 대 한 호출을 사용 하 여 배포 매니페스트를 생성 합니다. 기본적으로 *Mage.exe* 는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포를 설치 된 응용 프로그램으로 표시 하 여 온라인 및 오프 라인 모두에서 실행할 수 있도록 합니다. 사용자가 온라인 상태인 경우에만 응용 프로그램을 사용할 수 있도록 하려면 `-i` 값으로 인수를 사용 `f` 합니다. 이 응용 프로그램은 여러 배포 기능을 활용 하므로 `-providerUrl` *Mage.exe*에 대 한 인수를 제외 합니다. 버전 3.5 이전 버전의 .NET Framework `-providerUrl` 오프 라인 응용 프로그램의 경우를 제외 하면 오류가 발생 합니다.)

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. 배포 매니페스트에 서명 하지 마십시오.

8. 응용 프로그램을 네트워크에 배포 하는 모든 파일을 고객에 게 제공 합니다.

9. 이 시점에서 고객은 자체 생성 된 인증서로 배포 매니페스트에 서명 해야 합니다. 예를 들어 고객이 놀이 Works 라는 회사에 대해 작업 하는 경우 *MakeCert.exe* 도구를 사용 하 여 자체 서명 된 인증서를 생성할 수 있습니다. 그런 다음 *Pvk2pfx.exe* 도구를 사용 하 여 *MakeCert.exe* 만든 파일을 *Mage.exe*에 전달할 수 있는 PFX 파일로 결합 합니다.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. 고객은 다음에이 인증서를 사용 하 여 배포 매니페스트에 서명 합니다.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. 고객은 응용 프로그램을 사용자에 게 배포 합니다.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>MageUI.exe를 사용 하 여 여러 배포 및 브랜딩 지원으로 ClickOnce 응용 프로그램을 배포 하려면

1. Visual Studio 명령 프롬프트 또는 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] 명령 프롬프트를 열고 파일을 저장할 디렉터리로 이동 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 합니다.

2. **Bin** 이라는 하위 디렉터리를 만들고 실행 파일, 어셈블리, 리소스 및 데이터 파일을 포함 하 여 여기에 모든 응용 프로그램 파일을 복사 합니다.

3. 현재 버전의 배포 후에 라는 하위 디렉터리를 만듭니다. 응용 프로그램을 처음 배포 하는 경우 **1.0.0.0**을 선택 하는 것이 좋습니다.

   > [!NOTE]
   > 배포 버전이 응용 프로그램 파일의 버전과 다를 수 있습니다.

4. \\ **Bin** 디렉터리를 2 단계에서 만든 디렉터리로 이동 합니다.

5. *MageUI.exe*그래픽 도구를 시작 합니다.

   ```cmd
   MageUI.exe
   ```

6. 메뉴에서 **파일**, **새로 만들기**, **응용 프로그램 매니페스트** 를 선택 하 여 새 응용 프로그램 매니페스트를 만듭니다.

7. 기본 **이름** 탭에서이 배포의 이름 및 버전 번호를 입력 합니다. 또한 **게시자**에 대 한 값을 제공 합니다 .이 값은 응용 프로그램을 배포할 때 시작 메뉴에서 응용 프로그램 바로 가기 링크의 폴더 이름으로 사용 됩니다.

8. **응용 프로그램 옵션** 탭을 선택 하 고 **신뢰 정보는 응용 프로그램 매니페스트 사용**을 클릭 합니다. 그러면이 응용 프로그램에 대 한 타사 브랜딩이 사용 됩니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

9. **파일** 탭을 선택 하 고 **응용 프로그램 디렉터리** 텍스트 상자 옆에 있는 **찾아보기** 단추를 클릭 합니다.

10. 2 단계에서 만든 응용 프로그램 파일이 포함 된 디렉터리를 선택 하 고 폴더 선택 대화 상자에서 **확인** 을 클릭 합니다.

11. **채우기** 단추를 클릭 하 여 모든 응용 프로그램 파일을 파일 목록에 추가 합니다. 응용 프로그램에 둘 이상의 실행 파일이 포함 되어 있는 경우 **파일 형식** 드롭다운 목록에서 **진입점** 을 선택 하 여이 배포에 대 한 주 실행 파일을 시작 응용 프로그램으로 표시 합니다. 응용 프로그램에 하나의 실행 파일만 포함 된 경우 *MageUI.exe* 표시 됩니다.

12. **필요한 사용 권한** 탭을 선택 하 고 응용 프로그램에서 어설션하는 데 필요한 신뢰 수준을 선택 합니다. 기본값은 **완전 신뢰**이며 대부분의 응용 프로그램에 적합 합니다.

13. 메뉴에서 **파일**, **저장** 을 선택 하 고 응용 프로그램 매니페스트를 저장 합니다. 응용 프로그램 매니페스트를 저장할 때 서명 하 라는 메시지가 표시 됩니다.

14. 파일 시스템에 파일로 저장 된 인증서가 있는 경우 **인증서 파일에 서명** 옵션을 사용 하 고 줄임표 (**...**) 단추를 사용 하 여 파일 시스템에서 인증서를 선택 합니다.

     또는

     인증서가 컴퓨터에서 액세스할 수 있는 인증서 저장소에 보관 되어 있는 경우에는 **저장 된 인증서로 서명 옵션**을 선택 하 고 제공 된 목록에서 인증서를 선택 합니다.

15. 메뉴에서 **파일**, **새로 만들기**, **배포 매니페스트** 를 선택 하 여 배포 매니페스트를 만든 다음 **이름** 탭에서 이름 및 버전 번호 (이 예제의 경우**1.0.0.0** )를 제공 합니다.

16. **업데이트** 탭으로 전환 하 고이 응용 프로그램을 업데이트 하는 빈도를 지정 합니다. 응용 프로그램에서 배포 API를 사용 하 여 업데이트 자체를 확인 하는 경우 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **이 응용 프로그램에서 업데이트를 확인 해야 함**확인란의 선택을 취소 합니다.

17. **응용 프로그램 참조** 탭으로 전환 합니다. **매니페스트 선택** 단추를 클릭 하 고 이전 단계에서 만든 응용 프로그램 매니페스트를 선택 하 여이 탭의 모든 값을 미리 채울 수 있습니다.

18. **저장** 을 선택 하 고 배포 매니페스트를 디스크에 저장 합니다. 응용 프로그램 매니페스트를 저장할 때 서명 하 라는 메시지가 표시 됩니다. **취소** 를 클릭 하 여 서명 하지 않고 매니페스트를 저장 합니다.

19. 모든 응용 프로그램 파일을 고객에 게 제공 합니다.

20. 이 시점에서 고객은 자체 생성 된 인증서로 배포 매니페스트에 서명 해야 합니다. 예를 들어 고객이 놀이 Works 라는 회사에 대해 작업 하는 경우 *MakeCert.exe* 도구를 사용 하 여 자체 서명 된 인증서를 생성할 수 있습니다. 그런 다음 *Pvk2pfx.exe* 도구를 사용 하 여 *MakeCert.exe* 만든 파일을 *MageUI.exe*에 전달할 수 있는 PFX 파일로 결합 합니다.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. 인증서를 생성 하 고 나면 고객이 *MageUI.exe*에서 배포 매니페스트를 열고 저장 하 여 배포 매니페스트에 서명 합니다. 서명 대화 상자가 나타나면 고객이 **인증서 파일로 서명** 옵션을 선택 하 고 디스크에 저장 한 PFX 파일을 선택 합니다.

22. 고객은 응용 프로그램을 사용자에 게 배포 합니다.

## <a name="see-also"></a>추가 정보
- [Mage.exe(매니페스트 생성 및 편집 도구)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe(매니페스트 생성 및 편집 도구, 그래픽 클라이언트)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [Makecert.exe](/windows/desktop/SecCrypto/makecert)
