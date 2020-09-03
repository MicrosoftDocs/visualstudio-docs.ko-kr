---
title: DSL의 MSI 및 VSIX 배포
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d4de8d7560cb43115a30e29516e0e88b4d02d21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542618"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>DSL의 MSI 및 VSIX 배포
도메인 특정 언어를 사용자의 컴퓨터 또는 다른 컴퓨터에 설치할 수 있습니다. Visual Studio가 대상 컴퓨터에 이미 설치 되어 있어야 합니다.

## <a name="choosing-between-vsix-and-msi-deployment"></a><a name="which"></a> VSIX 및 MSI 배포 중에서 선택
 도메인 특정 언어를 배포 하는 방법에는 다음 두 가지가 있습니다.

|메서드|이점|
|-|-|
|VSX (Visual Studio 확장)|매우 쉬운 배포: DslPackage 프로젝트에서 **.vsix** 파일을 복사 하 고 실행 합니다.<br /><br /> 자세한 내용은 VSX를 [사용 하 여 DSL 설치 및 제거](#Installing)를 참조 하세요.|
|MSI (설치 관리자 파일)|-사용자가 DSL 파일을 두 번 클릭 하 여 Visual Studio를 열 수 있습니다.<br />-대상 컴퓨터에서 아이콘과 DSL 파일 형식을 연결 합니다.<br />-XSD (XML 스키마)를 DSL 파일 형식과 연결 합니다. 이렇게 하면 파일이 Visual Studio로 로드 될 때 경고를 피할 수 있습니다.<br /><br /> MSI를 만들려면 솔루션에 설치 프로젝트를 추가 해야 합니다.<br /><br /> 자세한 내용은 [MSI 파일을 사용 하 여 DSL 배포](#msi)를 참조 하세요.|

## <a name="install-and-uninstall-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> VSX를 사용 하 여 DSL 설치 및 제거

이 방법으로 DSL을 설치 하는 경우 사용자는 Visual Studio 내에서 DSL 파일을 열 수 있지만 Windows 탐색기에서 파일을 열 수는 없습니다.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>VSX를 사용 하 여 DSL을 설치 하려면

1. DSL 패키지 프로젝트를 통해 빌드된 **.vsix** 파일을 찾습니다.

   1. **솔루션 탐색기**에서 **dslpackage** 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **파일 탐색기에서 폴더 열기**를 클릭 합니다.

   2. 파일 ** \\ \* bin \\ **_프로젝트_를 찾습니다 **. 패키지 vsix**

2. DSL을 설치할 대상 컴퓨터에 **.vsix** 파일을 복사 합니다. 이 컴퓨터는 사용 중인 컴퓨터이거나 다른 컴퓨터일 수 있습니다.

   - 대상 컴퓨터에는 런타임에 Dsl을 지 원하는 버전 중 하나가 있어야 합니다 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] . 자세한 내용은 [지원 되는 Visual Studio 버전 시각화 & 모델링 SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)를 참조 하세요.

   - 대상 컴퓨터에는 **DslPackage\source.extensions.manifest**에 지정 된 Visual Studio 버전 중 하나가 있어야 합니다.

3. 대상 컴퓨터에서 **.vsix** 파일을 두 번 클릭 합니다.

    **Visual Studio 확장 설치 관리자** 에서 확장을 열고 설치합니다.

4. [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]를 시작하거나 다시 시작합니다.

5. DSL을 테스트 하려면 Visual Studio를 사용 하 여 DSL에 대해 정의한 확장명이 있는 새 파일을 만듭니다.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>VSX를 사용 하 여 설치 된 DSL을 제거 하려면

1. **도구** 메뉴 모음에서 **확장 및 업데이트**를 선택합니다.

2. **설치된 확장**을 확장합니다.

3. DSL이 정의 된 확장을 선택 하 고 **제거**를 클릭 합니다.

   드물게 결함이 있는 확장은 로드되지 않고 오류 창에 보고서를 생성하지만 확장 관리자에 나타나지 않습니다. 이 경우 다음 위치에서 파일을 삭제하여 확장을 제거할 수 있습니다.

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="deploying-a-dsl-in-an-msi"></a><a name="msi"></a> MSI에 DSL 배포
 DSL의 MSI (Windows Installer) 파일을 정의 하 여 사용자가 Windows 탐색기에서 DSL 파일을 열도록 허용할 수 있습니다. 아이콘 및 간단한 설명을 파일 이름 확장명에 연결할 수도 있습니다. 또한 MSI는 DSL 파일의 유효성을 검사 하는 데 사용할 수 있는 XSD를 설치할 수 있습니다. 원할 경우 동시에 설치 될 다른 구성 요소를 MSI에 추가할 수 있습니다.

 MSI 파일 및 기타 배포 옵션에 대 한 자세한 내용은 [응용 프로그램, 서비스 및 구성 요소 배포](../deployment/deploying-applications-services-and-components.md)를 참조 하세요.

 MSI를 빌드하려면 설치 프로젝트를 Visual Studio 솔루션에 추가 합니다. 설치 프로젝트를 만드는 가장 쉬운 방법은 [VMSDK 사이트](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)에서 다운로드할 수 있는 CreateMsiSetupProject.tt 템플릿을 사용 하는 것입니다.

### <a name="to-deploy-a-dsl-in-an-msi"></a>MSI에서 DSL을 배포 하려면

1. `InstalledByMsi`확장 매니페스트에 설정 합니다. 이렇게 하면 MSI를 제외 하 고 VSX 설치 및 제거 되지 않습니다. 이는 MSI에 다른 구성 요소를 포함 하는 경우에 중요 합니다.

   1. DslPackage\source.extension.tt 열기

   2. 앞에 다음 줄을 삽입 합니다 `<SupportedProducts>` .

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Windows 탐색기에서 DSL을 나타내는 아이콘을 만들거나 편집 합니다. 예를 들어, edit **Dslpackage\source\file\file.ico**

3. DSL의 다음 특성이 올바른지 확인 합니다.

   - DSL 탐색기에서 루트 노드를 클릭 하 고 속성 창에서 다음을 검토 합니다.

       - 설명

       - 버전

   - **편집기** 노드를 클릭 하 고 속성 창에서 **아이콘**을 클릭 합니다. **Dslpackage\resources**의 아이콘 파일 (예: .ico)을 참조 하도록 값을 설정 합니다 **.**

   - **빌드** 메뉴에서 **Configuration Manager**를 열고 빌드 하려는 구성 (예: **릴리스** 또는 **디버그**)을 선택 합니다.

4. [시각화 및 모델링 SDK 홈 페이지로](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)이동 하 고 **다운로드** 탭에서 **CreateMsiSetupProject.tt**를 다운로드 합니다.

5. Dsl 프로젝트에 **CreateMsiSetupProject.tt** 를 추가 합니다.

    Visual Studio에서 **CreateMsiSetupProject. .vdproj**라는 파일을 만듭니다.

6. Windows 탐색기에서 Dsl \\ *. .vdproj를 Setup 이라는 새 폴더에 복사 합니다.

    (원하는 경우 이제 Dsl 프로젝트에서 CreateMsiSetupProject.tt를 제외할 수 있습니다.)

7. **솔루션 탐색기**에서 ** \\ \* .vdproj** 를 기존 프로젝트로 추가 합니다.

8. **프로젝트** 메뉴에서 **프로젝트 종속성**을 클릭 합니다.

    **프로젝트 종속성** 대화 상자에서 설치 프로젝트를 선택 합니다.

    **Dslpackage**옆의 상자를 선택 합니다.

9. 솔루션을 다시 빌드합니다.

10. Windows 탐색기에서 설치 프로젝트의 기본 MSI 파일을 찾습니다.

     DSL을 설치 하려는 컴퓨터에 MSI 파일을 복사 합니다. MSI 파일을 두 번 클릭 합니다. 설치 관리자를 실행합니다.

11. 대상 컴퓨터에서 DSL의 파일 확장명이 있는 새 파일을 만듭니다. 다음 사항을 확인합니다.

    - Windows 탐색기 목록 보기에서 파일은 사용자가 정의한 아이콘과 설명과 함께 표시 됩니다.

    - 파일을 두 번 클릭 하면 Visual Studio가 시작 되 고 dsl 편집기에서 DSL 파일이 열립니다.

    원한다 면 텍스트 템플릿을 사용 하는 대신 수동으로 설치 프로젝트를 만들 수 있습니다. 이 절차를 포함 하는 연습은 [시각화 및 모델링 SDK 랩](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207)의 5 장을 참조 하세요.

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>MSI에서 설치 된 DSL을 제거 하려면

1. Windows에서 **프로그램 및 기능** 제어판을 엽니다.

2. DSL을 제거 합니다.

3. Visual Studio를 다시 시작합니다.
