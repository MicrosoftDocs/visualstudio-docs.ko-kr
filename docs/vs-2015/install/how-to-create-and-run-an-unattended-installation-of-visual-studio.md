---
title: '방법: 무인 설치 만들기 및 실행 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- installing Visual Studio, unattended
- unattended installation, Visual Studio
ms.assetid: 3867b5dc-ed34-4ee2-be32-a42e7e320517
caps.latest.revision: 44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 26e059d4fdc8eadd422924dd6bbda6f7c945ccfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843270"
---
# <a name="how-to-create-and-run-an-unattended-installation-of-visual-studio"></a>How to: Create and Run an Unattended Installation of Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에 대한 설치 애플리케이션을 DVD와 같은 미디어 대신 인트라넷을 통해 무인(즉, 사용자 지정된 자동 설치) 설치로 실행할 수 있습니다. 이 항목에서는 네트워크 공유에서 이 유형을 사용하여 설치하는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 준비하는 방법을 설명합니다.

## <a name="creating-a-network-image"></a>네트워크 이미지 만들기
 먼저 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 미디어의 네트워크 이미지를 만듭니다.

#### <a name="to-create-a-network-image"></a>네트워크 이미지를 만들려면

1. 서버에 폴더(예: *Drive*:\IDEinstall\\)를 만듭니다.

2. [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)에서 설치 관리자를 다운로드한 다음, *Product*.exe /Layout *Drive*:\IDEinstall\을 실행합니다.

3. 네트워크에서 IDEinstall 폴더를 공유한 다음, 적절한 보안 설정을 지정합니다.

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에 대한 설치 애플리케이션의 네트워크 경로는 \\\\*ServerName*\IDEinstall\\*Product*.exe와 유사합니다.

    > [!NOTE]
    > 경로 및 파일 이름 조합이 260자를 초과하면 설치가 실패할 수 있습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에서 경로의 최대 길이는 221자입니다.  로컬 경로 이름은 70자를 초과하면 안 되고 네트워크 경로 이름은 39자를 초과하면 안 됩니다.

     경로의 폴더 이름에 공백이 포함 된 경우 (예: " \\ \\ *servername*\ide install" 또는 \\ \\ *server\visual*Studio \\ )에도 설치가 실패할 수 있습니다.

## <a name="deploying-visual-studio-in-unattended-mode"></a>무인 모드로 Visual Studio 배포
 무인 모드로 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 를 배포하려면 AdminDeployment.xml 파일을 수정해야 합니다. 이렇게 하려면 먼저 `/CreateAdminFile` 명령줄 매개 변수를 사용 하 여 AdminDeployment.xml 파일을 만들어야 합니다 *\<file location>* . 그런 다음 이 파일을 사용하여 네트워크에 Visual Studio의 배포를 푸시하거나 *Drive*:\IDEinstall\packages 디렉터리에 해당 파일을 복사한 경우 끌어와서 설치할 수 있습니다. AdminDeployment.xml 파일은 운영 체제, 아키텍처, Visual Studio 버전 또는 운영 체제 언어에 고유하지 않습니다.

> [!CAUTION]
> AdminDeployment.xml 파일에서 선택된 것으로 나열된 항목이 설치되지 않는 경우도 있습니다. 이 문제를 해결하려면 "선택됨="yes""로 표시된 항목을 AdminDeployment.xml 파일의 **끝** 에 배치합니다.
>
> 항목의 선택적 종속성을 설치하지 않으려는 경우 부모를 먼저 선택한 후 다음 스크린샷에 표시된 대로 부모 뒤의 선택적 종속성을 선택 취소해야 합니다.
>
> ![AdminDeployment.xml 파일의 끝에 있는 설치 항목](../install/media/vs2015-install-endoffileadmindeploy.PNG "vs2015_Install_EndOfFileAdminDeploy")
>
> 이 작업을 수행하는 또 다른 방법은 단순히 부모의 선택적 자식을 생략하는 것입니다. 즉, "선택됨="no"" 항목을 포함하지 마세요. 하지만 "선택됨="yes"" 항목은 모두 AdminDeployment.xml 파일의 끝에 배치해야 합니다.

> [!IMPORTANT]
> 설치하는 동안 컴퓨터가 한 번 이상 자동으로 다시 시작될 수 있습니다. 다시 시작한 후, 컴퓨터를 다시 시작하기 전에 설치를 수행하기 위해 로그온했던 사용자 계정으로 다시 로그인해야 합니다. 무인 설치를 실행하기 전에 필수 조건을 설치하여 자동으로 다시 시작되지 않게 할 수 있습니다. 자세한 내용은 [Visual Studio Administrator Guide](../install/visual-studio-administrator-guide.md)에서 “설치 중 다시 시작 방지” 섹션을 참조하세요.

 AdminDeployment 파일 스키마에는 다음 요소가 포함되어 있습니다.

|요소|attribute|값|Description|
|-------------|---------------|------------|-----------------|
|BundleCustomizations|TargetDir|*Path*|설치 애플리케이션의 사용자 인터페이스에서 경로를 재정의하는 작업과 동일하게 동작합니다. Visual Studio가 이미 설치된 경우 이 요소는 무시됩니다.|
|BundleCustomizations|NoWeb|예&#124;기본값|이 요소의 값이 yes이면 설치 애플리케이션이 설치 작업 중 웹으로 이동하려고 시도하지 않습니다.|
|SelectableItemCustomization|숨김|예&#124;아니요|이 요소의 값이 Yes이면 사용자 지정 트리에서 선택 가능한 항목을 숨깁니다.|
|SelectableItemCustomization|선택함|예&#124;아니요|사용자 지정 트리에서 선택 가능한 항목을 선택하거나 선택 취소합니다.|
|BundleCustomizations|피드|경로|사용자가 사용하려는 피드의 위치입니다.  이 피드는 컴퓨터의 후속 수정 작업에 사용됩니다(기본적으로 "Default").|
|BundleCustomizations|SuppressRefreshPrompt|예&#124;기본값|최신 버전을 사용할 수 있는 경우 설치를 새로 고치라는 메시지가 사용자에게 표시되지 않도록 합니다.|
|BundleCustomizations|NoRefresh|예&#124;기본값|최신 버전을 사용할 수 있는 경우 설치를 새로 고치지 않습니다.|
|BundleCustomizations|NoCacheOnlyMode|예&#124;기본값|패키지 캐시 미리 채우기를 방지합니다.|

> [!WARNING]
> 선택 가능한 항목이 숨겨진 경우에도 설치 애플리케이션이 선택함 상태를 적용합니다. 예를 들어 선택 가능한 항목을 항상 설치하려는 경우 이 항목을 숨기고 선택함 상태로 표시할 수 있습니다.

#### <a name="to-create-an-unattended-installation-of-visual-studio"></a>Visual Studio의 무인 설치를 만들려면

1. *Drive*:\IDEinstall\AdminDeployment.xml 파일에서 다음 예제와 같이 BundleCustomizations 요소의 NoWeb 특성 값을 "default"에서 "yes"로 변경합니다.

     `<BundleCustomizations TargetDir="default" NoWeb="default"/>`를 `<BundleCustomizations TargetDir="default" NoWeb="yes"/>`로 변경

2. 선택적 구성 요소에 맞게 SelectableItemCustomization 특성을 변경하고 파일을 저장합니다.

## <a name="running-unattended-setup"></a>무인 설치 실행
 클라이언트 컴퓨터에서 Visual Studio에 대한 설치 애플리케이션을 자동으로 실행하거나 정의한 설정을 사용하여 사용자가 직접 애플리케이션을 실행하도록 허용하여 무인 설치를 실행할 수 있습니다.

#### <a name="to-run-an-unattended-installation-on-a-client-computer"></a>클라이언트 컴퓨터에서 무인 설치를 실행하려면

- **시작** 메뉴를 열고, **실행**을 선택한 다음, \\\\*ServerName*\IDEinstall\vs_*Product*.exe /adminfile *PathOfTheAdmindeployment.xmlFile*<em>AdditionalParametersAsNeeded</em>를 입력합니다.

   예를 들어 `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\ IDEinstall\AdminDeployment.xml /quiet /norestart` 명령줄을 지정할 수 있습니다.

#### <a name="to-enable-clients-to-manually-install-visual-studio-with-pre-defined-settings"></a>클라이언트가 미리 정의된 설정을 사용하여 Visual Studio를 수동으로 설치할 수 있도록 하려면

1. 사용자 지정된 AdminDeployment.xml 파일을 읽기 전용인 네트워크 공유 위치에 복사합니다(예: \\\\*ServerName*\IDEinstall\packages\AdminDeployment.xml).

2. 사용자가 해당 공유에서 설치할 수 있도록 설정합니다.

## <a name="maintaining-an-installation"></a>설치 유지 관리
 **제어판** 을 열고 설치 애플리케이션을 다시 실행하면 Visual Studio의 기능을 수정하고 프로그래밍 언어를 제거하고 Visual Studio를 복구하거나 제거할 수 있습니다.

> [!NOTE]
> 유지 관리 모드를 사용하려면 로컬 컴퓨터에서 관리자 자격 증명이 있어야 합니다.

#### <a name="to-maintain-an-installation-on-a-client-computer"></a>클라이언트 컴퓨터에서 설치를 유지 관리하려면

- **제어판**을 열고 **프로그램 및 기능**을 선택합니다.

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 선택한 다음 **변경**을 선택합니다.

#### <a name="to-change-admindeployment-settings-on-a-client-computer-after-visual-studio-has-been-installed"></a>Visual Studio가 설치된 후 클라이언트 컴퓨터에서 AdminDeployment 설정을 변경하려면

1. 필요에 따라 AdminDeployment.xml을 업데이트합니다.

2. **시작** 메뉴를 열고 **실행**을 선택합니다.

3. 다음 텍스트를 입력합니다. \\\\*ServerName*\IDEinstall\vs_*Product*.exe /AdminFile PathToAdmindeployment.xml File

    AdditionalParametersAsNeeded

    예를 들어 `\\server1\IDEinstall\vs_enterprise.exe /adminfile \\server1\IDEinstall\AdminDeployment.xml /quiet /norestart` 명령줄을 지정할 수 있습니다.

   Visual Studio가 설치된 후에는 복구가 기본 매개 변수입니다. 업데이트된 /AdminFile로 Visual Studio를 복구하는 경우 업데이트된 AdminDeployment.xml 파일이 호출하는 설정으로 현재 관리자 배포 설정을 재정의합니다.

## <a name="updating-an-installation"></a>설치 업데이트
 Microsoft에서는 여러 가지 Visual Studio 2015 업데이트를 릴리스했습니다. 이 섹션에서는 업데이트를 포함하도록 Visual Studio 2015의 무인 설치 이미지를 업데이트하는 방법에 대해 설명합니다.

#### <a name="to-update-an-unattended-installation-of-visual-studio"></a>Visual Studio의 무인 설치를 업데이트하려면

1. 기존 네트워크 이미지에서 Product.exe 파일을 찾아 마우스 오른쪽 단추로 클릭한 다음, **속성**을 클릭합니다.

2. **세부 정보** 탭을 클릭한 다음, **제품 버전** 속성을 기록해 둡니다.

    ![Visual Studio 무인 설치의 속성 대화 상자 예제](../install/media/unattended-install-properties-dialog-box.PNG "무인 설치-속성 대화 상자")

3. ###### <a name="if-the-product-version-is-140247200-or-140247201-follow-these-steps"></a>제품 버전이 14.0.24720.0 또는 14.0.24720.1이면 다음 단계를 수행합니다.
   1. 인터넷에 연결된 머신에서 *Product.exe* /Layout *Drive:* \IDEinstall을 실행합니다. 예를 들어 다음을 실행합니다. `vs_enterprise.exe /Layout d:\IDEinstall`

   2. /Layout이 완료되면 새 이미지를 새 위치로 복사합니다.

   3. AdminDeployment.xml 파일을 만들고 수정합니다. 이렇게 하려면 `/CreateAdminFile` *\<file location>* 명령줄 매개 변수를 사용 합니다. (자세한 내용은 이 문서의 “무인 모드에서 Visual Studio 배포” 섹션을 참조하세요.)

   4. 클라이언트 머신에서 다음 명령을 실행하여 이전에 설치한 Visual Studio를 업데이트합니다. “\\\\*server1*\IDEinstall_Updated_1\\*Product.exe* /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart”

        예를 들어 다음을 실행합니다. `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`
5. ###### <a name="for-other-product-version-values-follow-these-steps"></a>기타 제품 버전 값의 경우 다음 단계를 수행합니다.
   1. 인터넷에 연결된 머신에서 *Product.exe* /Layout *Drive:* \IDEinstall을 실행합니다. 예를 들어 다음을 실행합니다. `vs-enterprise.exe /Layout d:\IDEinstall`

   2. /Layout이 완료되면 새 이미지를 새 위치로 복사합니다. (또는 기존 네트워크 이미지를 대신 재정의할 수 있습니다.)

   3. AdminDeployment.xml 파일을 만들고 수정합니다. 이렇게 하려면 `/CreateAdminFile` *\<file location>* 명령줄 매개 변수를 사용 합니다. (자세한 내용은 이 문서의 “무인 모드에서 Visual Studio 배포” 섹션을 참조하세요.)

   4. 이미지를 새 위치로 복사할 경우 클라이언트 머신에서 다음 명령을 실행하여 이전에 설치한 Visual Studio를 업데이트해야 합니다. “\\\\*server1*\IDEinstall_Updated_1\\*Product.exe* /adminfile \\\server1\ IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart”

        예를 들어 다음을 실행합니다. `\\server1\IDEinstall_Updated_1\vs_enterprise.exe /adminfile \\server1\IDEinstall_Updated_1\AdminDeployment.xml /quiet /norestart`

   5. 기존 네트워크 이미지를 재정의하는 경우 이전 단계에 나열된 대로 명령을 실행하거나 다음을 수행할 수 있습니다.
       1. **제어판**을 열고 **프로그램 및 기능**을 선택합니다.

       2. **Visual Studio**를 선택한 다음, **변경**을 선택합니다.

       3. Visual Studio가 유지 관리 모드에서 시작되면 **수정**을 클릭합니다.

       4. 최신 업데이트가 기능 페이지에 표시됩니다. 설치할 다른 기능을 선택하고 **다음**을 클릭한 후 **업데이트**를 클릭하여 업데이트 및 새 기능을 모두 설치합니다.

## <a name="registering-the-product"></a>프로그램 등록
 설치가 완료된 후 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 내에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 복사본을 등록할 수 있습니다.

#### <a name="to-register"></a>등록하려면

1. **도움말** 메뉴를 열고 **제품 등록**을 선택합니다.

2. 제품 키를 입력합니다.

     (자세한 내용은 [방법: Visual Studio 제품 키 찾기](../install/how-to-locate-the-visual-studio-product-key.md) 및 [방법: Visual Studio를 배포할 때 제품 키를 자동으로 적용](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md) 항목을 참조하세요.)

## <a name="see-also"></a>참고 항목
 [Visual Studio 설치](../install/install-visual-studio-2015.md)