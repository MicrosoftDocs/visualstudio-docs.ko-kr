---
title: '연습: ClickOnce 응용 프로그램 수동 배포 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4aad87832a5bdae0d28d461d4cc289551eee7fee
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88249978"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>연습: 수동으로 ClickOnce 애플리케이션 배포
Visual Studio를 사용 하 여 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램을 배포할 수 없거나 신뢰할 수 있는 응용 프로그램 배포와 같은 고급 배포 기능을 사용 해야 하는 경우 *Mage.exe* 명령줄 도구를 사용 하 여 매니페스트를 만들어야 합니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 이 연습에서는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 명령줄 버전 (*Mage.exe*) 또는 매니페스트 생성 및 편집 도구의 그래픽 버전 (*MageUI.exe*) 중 하나를 사용 하 여 배포를 만드는 방법을 설명 합니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습에는 배포를 빌드하기 전에 선택 해야 하는 몇 가지 필수 구성 요소 및 옵션이 있습니다.

- *Mage.exe* 및 *MageUI.exe*를 설치 합니다.

   *Mage.exe* 및 *MageUI.exe* 은의 일부 [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] 입니다. 가 설치 되어 있거나 [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] Visual Studio에 포함 된 버전이 있어야 합니다. 자세한 내용은 MSDN의 [Windows SDK](https://www.microsoft.com/download/details.aspx?id=8279) 을 참조 하세요.

- 배포할 응용 프로그램을 제공 합니다.

   이 연습에서는 사용자가 배포할 준비가 된 Windows 응용 프로그램이 있다고 가정 합니다. 이 응용 프로그램은 AppToDeploy 라고 합니다.

- 배포를 배포 하는 방법을 결정 합니다.

   배포 옵션에는 웹, 파일 공유 또는 CD가 있습니다. 자세한 내용은 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)을 참조하세요.

- 응용 프로그램에 높은 수준의 신뢰가 필요한 지 여부를 결정 합니다.

   응용 프로그램에 완전 신뢰가 필요한 경우 (예: 사용자 시스템에 대 한 모든 권한)Mage.exe옵션을 사용 `-TrustLevel` 하 여 *Mage.exe* 이를 설정할 수 있습니다. 응용 프로그램에 대 한 사용자 지정 권한 집합을 정의 하려면 다른 매니페스트에서 인터넷 또는 인트라넷 권한 섹션을 복사 하 고, 필요에 따라 수정 하 고, 텍스트 편집기나 *MageUI.exe*를 사용 하 여 응용 프로그램 매니페스트에 추가할 수 있습니다. 자세한 내용은 [신뢰할 수 있는 응용 프로그램 배포 개요](../deployment/trusted-application-deployment-overview.md)를 참조 하세요.

- Authenticode 인증서를 가져옵니다.

   Authenticode 인증서를 사용 하 여 배포에 서명 해야 합니다. Visual Studio, *MageUI.exe*또는 *MakeCert.exe* 및 *Pvk2Pfx.exe* 도구를 사용 하 여 테스트 인증서를 생성 하거나 CA (인증 기관)에서 인증서를 가져올 수 있습니다. 신뢰할 수 있는 응용 프로그램 배포를 사용 하도록 선택 하는 경우 모든 클라이언트 컴퓨터에 인증서를 한 번 설치 해야 합니다. 자세한 내용은 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)을 참조하십시오.

  > [!NOTE]
  > 인증 기관에서 얻을 수 있는 CNG 인증서를 사용 하 여 배포에 서명할 수도 있습니다.

- 응용 프로그램에 UAC 정보를 포함 하는 매니페스트가 없는지 확인 합니다.

   응용 프로그램에 요소와 같은 UAC (사용자 계정 컨트롤) 정보를 포함 하는 매니페스트가 포함 되어 있는지 여부를 확인 해야 `<dependentAssembly>` 합니다. 응용 프로그램 매니페스트를 검사 하려면 Windows Sysinternals [Sigcheck](/sysinternals/downloads/sigcheck) 유틸리티를 사용할 수 있습니다.

   응용 프로그램에 UAC 정보를 포함 하는 매니페스트가 포함 된 경우 UAC 정보 없이 다시 빌드해야 합니다. Visual Studio에서 c # 프로젝트의 경우 프로젝트 속성을 열고 응용 프로그램 탭을 선택 합니다. **매니페스트** 드롭다운 목록에서 **매니페스트 없이 응용 프로그램 만들기**를 선택 합니다. Visual Studio의 Visual Basic 프로젝트에 대해 프로젝트 속성을 열고 응용 프로그램 탭을 선택한 후 **UAC 설정 보기**를 클릭 합니다. 열린 매니페스트 파일에서 단일 요소 내의 모든 요소를 제거 `<asmv1:assembly>` 합니다.

- 응용 프로그램에 클라이언트 컴퓨터의 필수 구성 요소가 필요한 지 여부를 결정 합니다.

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Visual Studio에서 배포 된 응용 프로그램에는 배포와 함께 필수 구성 요소 설치 부트스트래퍼 (*setup.exe*)가 포함 될 수 있습니다. 이 연습에서는 배포에 필요한 두 개의 매니페스트를 만듭니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . [Generatebootstrapper 작업](../msbuild/generatebootstrapper-task.md)을 사용 하 여 필수 구성 요소 부트스트래퍼를 만들 수 있습니다.

### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Mage.exe 명령줄 도구를 사용 하 여 응용 프로그램을 배포 하려면

1. 배포 파일을 저장할 디렉터리를 만듭니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

2. 방금 만든 배포 디렉터리에서 버전 하위 디렉터리를 만듭니다. 응용 프로그램을 처음 배포 하는 경우에는 버전의 이름을 **1.0.0.0**으로 표시 합니다.

   > [!NOTE]
   > 배포 버전은 응용 프로그램의 버전과 다를 수 있습니다.

3. 실행 파일, 어셈블리, 리소스 및 데이터 파일을 포함 하 여 모든 응용 프로그램 파일을 버전 하위 디렉터리에 복사 합니다. 필요한 경우 추가 파일을 포함 하는 하위 디렉터리를 추가로 만들 수 있습니다.

4. [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]또는 Visual Studio 명령 프롬프트를 열고 버전 하위 디렉터리로 변경 합니다.

5. *Mage.exe*에 대 한 호출을 사용 하 여 응용 프로그램 매니페스트를 만듭니다. 다음 문은 Intel x86 프로세서에서 실행 되도록 컴파일된 코드에 대 한 응용 프로그램 매니페스트를 만듭니다.

   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .
   ```

   > [!NOTE]
   > 옵션 뒤에 점 (.)을 포함 해야 `-FromDirectory` 합니다 .이 옵션은 현재 디렉터리를 나타냅니다. 점을 포함 하지 않으면 응용 프로그램 파일의 경로를 지정 해야 합니다.

6. Authenticode 인증서를 사용 하 여 응용 프로그램 매니페스트에 서명 합니다. *Mycert* 을 인증서 파일의 경로로 바꿉니다. *Passwd* 를 인증서 파일의 암호로 바꿉니다.

   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd
   ```

   Visual Studio 및 Windows SDK를 사용 하 여 배포 되는 .NET Framework 4.6.2 SDK로 시작 하 고, CNG를 사용 하 여 매니페스트에 서명 하 고 Authenticode 인증서를 사용 하 여 매니페스트를 *mage.exe* 합니다. Authenticode 인증서와 동일한 명령줄 매개 변수를 사용 합니다.

7. 배포 디렉터리의 루트로 변경 합니다.

8. *Mage.exe*에 대 한 호출을 사용 하 여 배포 매니페스트를 생성 합니다. 기본적으로 *Mage.exe* 는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포를 설치 된 응용 프로그램으로 표시 하 여 온라인 및 오프 라인 모두에서 실행할 수 있도록 합니다. 사용자가 온라인 상태인 경우에만 응용 프로그램을 사용할 수 있도록 하려면 `-Install` 값에 옵션을 사용 `false` 합니다. 기본값을 사용 하 고 사용자가 웹 사이트 또는 파일 공유에서 응용 프로그램을 설치 하는 경우 옵션 값이 `-ProviderUrl` 웹 서버 또는 공유에서 응용 프로그램 매니페스트의 위치를 가리키는지 확인 합니다.

   ```cmd
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application
   ```

9. Authenticode 또는 CNG 인증서를 사용 하 여 배포 매니페스트에 서명 합니다.

    ```cmd
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd
    ```

10. 배포 디렉터리의 모든 파일을 배포 대상 또는 미디어에 복사 합니다. 이 폴더는 웹 사이트 또는 FTP 사이트의 폴더, 파일 공유 또는 CD-ROM 일 수 있습니다.

11. 응용 프로그램을 설치 하는 데 필요한 URL, UNC 또는 물리적 미디어를 사용자에 게 제공 합니다. URL 또는 UNC를 제공 하는 경우 사용자에 게 배포 매니페스트에 대 한 전체 경로를 제공 해야 합니다. 예를 들어 apptodeploy를 http://webserver01/ apptodeploy 디렉터리에 배포 하는 경우 전체 URL 경로는 http://webserver01/AppToDeploy/AppToDeploy.application 입니다.

### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>MageUI.exe 그래픽 도구를 사용 하 여 응용 프로그램을 배포 하려면

1. 배포 파일을 저장할 디렉터리를 만듭니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

2. 방금 만든 배포 디렉터리에서 버전 하위 디렉터리를 만듭니다. 응용 프로그램을 처음 배포 하는 경우에는 버전의 이름을 **1.0.0.0**으로 표시 합니다.

   > [!NOTE]
   > 배포 버전이 응용 프로그램의 버전과 다를 수 있습니다.

3. 실행 파일, 어셈블리, 리소스 및 데이터 파일을 포함 하 여 모든 응용 프로그램 파일을 버전 하위 디렉터리에 복사 합니다. 필요한 경우 추가 파일을 포함 하는 하위 디렉터리를 추가로 만들 수 있습니다.

4. *MageUI.exe* 그래픽 도구를 시작 합니다.

   ```cmd
   MageUI.exe
   ```

5. 메뉴에서 **파일**, **새로 만들기**, **응용 프로그램 매니페스트** 를 선택 하 여 새 응용 프로그램 매니페스트를 만듭니다.

6. 기본 **이름** 탭에서이 배포의 이름 및 버전 번호를 입력 합니다. 응용 프로그램이 빌드되는 **프로세서** (예: x86)도 지정 합니다.

7. **파일** 탭을 선택한 다음 **응용 프로그램 디렉터리** 텍스트 상자 옆에 있는 줄임표 (**...**) 단추를 선택 합니다. **폴더 찾아보기** 대화 상자가 나타납니다.

8. 응용 프로그램 파일이 포함 된 버전 하위 디렉터리를 선택한 다음 **확인**을 선택 합니다.

9. 인터넷 정보 서비스 (IIS)에서 배포 하는 경우를 **채울 때 .deploy 확장명이 없는 모든 파일에 .deploy 확장명 추가** 확인란을 선택 합니다.

10. 파일 목록에 모든 응용 프로그램 파일을 추가 하려면 **채우기** 단추로 이동 합니다. 응용 프로그램에 둘 이상의 실행 파일이 포함 되어 있는 경우 **파일 형식** 드롭다운 목록에서 **진입점** 을 선택 하 여이 배포에 대 한 주 실행 파일을 시작 응용 프로그램으로 표시 합니다. 응용 프로그램에 하나의 실행 파일만 있는 경우 *MageUI.exe* 표시 됩니다.

11. **필요한 사용 권한** 탭을 선택 하 고 응용 프로그램에서 어설션할 신뢰 수준을 선택 합니다. 기본값은 **FullTrust**이며, 대부분의 응용 프로그램에 적합 합니다.

12. 메뉴에서 **파일**, 다른 **이름으로 저장** 을 선택 합니다. 응용 프로그램 매니페스트에 서명 하 라는 메시지를 표시 하는 서명 옵션 대화 상자가 나타납니다.

13. 파일 시스템에 파일로 저장 된 인증서가 있는 경우 **인증서 파일에 서명** 옵션을 사용 하 고 줄임표 (**...**) 단추를 사용 하 여 파일 시스템에서 인증서를 선택 합니다. 그런 다음 인증서 암호를 입력 합니다.

     또는

     인증서가 컴퓨터에서 액세스할 수 있는 인증서 저장소에 보관 되어 있는 경우에는 **저장 된 인증서로 서명** 옵션을 선택 하 고 제공 된 목록에서 인증서를 선택 합니다.

14. **확인** 을 선택 하 여 응용 프로그램 매니페스트에 서명 합니다. **다른 이름으로 저장** 대화 상자가 나타납니다.

15. 다른 **이름으로 저장** 대화 상자에서 버전 디렉터리를 지정 하 고 **저장**을 선택 합니다.

16. 메뉴에서 **파일**, **새로 만들기**, **배포 매니페스트** 를 선택 하 여 배포 매니페스트를 만듭니다.

17. **이름** 탭에서이 배포에 대 한 이름 및 버전 번호를 지정 합니다 (이 예에서는**1.0.0.0** ). 응용 프로그램이 빌드되는 **프로세서** (예: x86)도 지정 합니다.

18. **설명** 탭을 선택 하 고 **게시자** 및 **제품**의 값을 지정 합니다. (**Product** 는 응용 프로그램이 오프 라인으로 사용 하기 위해 클라이언트 컴퓨터에 설치 될 때 Windows 시작 메뉴에서 응용 프로그램에 제공 되는 이름입니다.)

19. **배포 옵션** 탭을 선택 하 고 **시작 위치** 텍스트 상자에서 웹 서버 또는 공유의 응용 프로그램 매니페스트 위치를 지정 합니다. 예를 들면 * \\ \myServer\myShare\AppToDeploy.application*입니다.

20. 이전 단계에서 *.deploy* 확장명을 추가한 경우에는 여기에서 **파일 이름 확장명을 사용** 합니다 .를 선택 합니다.

21. **업데이트 옵션** 탭을 선택 하 고이 응용 프로그램을 업데이트할 빈도를 지정 합니다. 응용 프로그램에서 <xref:System.Deployment.Application.UpdateCheckInfo> 업데이트 자체를 확인 하는 데를 사용 하는 경우 **이 응용 프로그램이 업데이트를 확인** 합니다. 확인란의 선택을 취소 합니다.

22. **응용 프로그램 참조** 탭을 선택한 다음 **매니페스트 선택** 단추로 이동 합니다. 열기 대화 상자가 나타납니다.

23. 이전에 만든 응용 프로그램 매니페스트를 선택 하 고 **열기**를 선택 합니다.

24. 메뉴에서 **파일**, 다른 **이름으로 저장** 을 선택 합니다. 배포 매니페스트에 서명 하 라는 메시지를 표시 하는 **서명 옵션** 대화 상자가 나타납니다.

25. 파일 시스템에 파일로 저장 된 인증서가 있는 경우 **인증서 파일에 서명** 옵션을 사용 하 고 줄임표 (**...**) 단추를 사용 하 여 파일 시스템에서 인증서를 선택 합니다. 그런 다음 인증서 암호를 입력 합니다.

     또는

     인증서가 컴퓨터에서 액세스할 수 있는 인증서 저장소에 보관 되어 있는 경우에는 **저장 된 인증서로 서명** 옵션을 선택 하 고 제공 된 목록에서 인증서를 선택 합니다.

26. **확인** 으로 이동 하 여 배포 매니페스트를 서명 합니다. **다른 이름으로 저장** 대화 상자가 나타납니다.

27. 다른 **이름으로 저장** 대화 상자에서 한 디렉터리를 배포의 루트로 이동 하 고 **저장**을 선택 합니다.

28. 배포 디렉터리의 모든 파일을 배포 대상 또는 미디어에 복사 합니다. 이 폴더는 웹 사이트 또는 FTP 사이트의 폴더, 파일 공유 또는 CD-ROM 일 수 있습니다.

29. 응용 프로그램을 설치 하는 데 필요한 URL, UNC 또는 물리적 미디어를 사용자에 게 제공 합니다. URL 또는 UNC를 제공 하는 경우 사용자에 게 배포 매니페스트의 전체 경로를 제공 해야 합니다. 예를 들어 apptodeploy를 http://webserver01/ apptodeploy 디렉터리에 배포 하는 경우 전체 URL 경로는 http://webserver01/AppToDeploy/AppToDeploy.application 입니다.

## <a name="next-steps"></a>다음 단계
 응용 프로그램의 새 버전을 배포 해야 하는 경우 새 버전 (예: 1.0.0.1) 다음에 라는 새 디렉터리를 만들고 새 응용 프로그램 파일을 새 디렉터리에 복사 합니다. 다음으로, 이전 단계를 수행 하 여 새 응용 프로그램 매니페스트를 만들고 서명 하 고 배포 매니페스트를 업데이트 하 고 서명 해야 합니다. Mage.exe및 호출 모두에서 더 높은 버전을 지정 해야 *Mage.exe* `-New` `-Update` 합니다 .이 경우에는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 더 높은 버전만 업데이트 하 고 가장 낮은 정수는 가장 중요 합니다. *MageUI.exe*사용 하는 경우 배포 매니페스트를 열고 **응용 프로그램 참조** 탭을 선택 하 여 **매니페스트 선택** 단추로 이동한 후 업데이트 된 응용 프로그램 매니페스트를 선택 하 여 업데이트할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [Mage.exe(매니페스트 생성 및 편집 도구)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe(매니페스트 생성 및 편집 도구, 그래픽 클라이언트)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)
