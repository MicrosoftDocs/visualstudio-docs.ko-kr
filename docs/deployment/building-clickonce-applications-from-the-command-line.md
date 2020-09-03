---
title: 명령줄에서 ClickOnce 응용 프로그램 빌드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, from command line
- publishing
- publishing, ClickOnce
ms.assetid: d9bc6212-c584-4f72-88c9-9a4b998c555e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 065eea058ffa78c84428e031832e24837eb81d08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74797207"
---
# <a name="build-clickonce-applications-from-the-command-line"></a>명령줄에서 ClickOnce 애플리케이션 빌드
에서 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] IDE (통합 개발 환경)에서 프로젝트를 만든 경우에도 명령줄에서 프로젝트를 빌드할 수 있습니다. 실제로 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] .NET Framework만 설치 된 다른 컴퓨터에서로 만든 프로젝트를 다시 빌드할 수 있습니다. 따라서 자동화 된 프로세스를 사용 하 여 빌드를 재현할 수 있습니다. 예를 들어 중앙 빌드 랩에서 또는 프로젝트 자체 빌드 범위를 벗어나는 고급 스크립팅 기술을 사용할 수 있습니다.

## <a name="use-msbuild-to-reproduce-clickonce-application-deployments"></a>MSBuild를 사용 하 여 ClickOnce 응용 프로그램 배포 재현
 명령줄에서 msbuild/target: publish를 호출 하면 MSBuild 시스템에서 프로젝트를 빌드하고 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] publish 폴더에 응용 프로그램을 만들도록 지시 합니다. 이는 IDE에서 **게시** 명령을 선택 하는 것과 같습니다.

 이 명령은 Visual Studio 명령 프롬프트 환경의 경로에 있는 *msbuild.exe*를 실행 합니다.

 "대상"은 명령을 처리 하는 방법에 대 한 MSBuild에 대 한 표시기입니다. 키 대상은 "빌드" 대상과 "게시" 대상입니다. 빌드 대상은 IDE에서 빌드 명령을 선택 하거나 F5 키를 누르는 것과 같습니다. 프로젝트를 빌드 하려는 경우에는를 입력 하 여이를 달성할 수 있습니다 `msbuild` . 빌드 대상이에 의해 생성 된 모든 프로젝트의 기본 대상이 기 때문에이 명령이 작동 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] 합니다. 즉, 빌드 대상을 명시적으로 지정할 필요가 없습니다. 따라서 입력 `msbuild` 은 입력 하는 것과 같은 작업입니다 `msbuild /target:build` .

 `/target:publish`명령은 MSBuild에 게시 대상을 호출 하도록 지시 합니다. 게시 대상은 빌드 대상에 따라 다릅니다. 즉, 게시 작업은 빌드 작업의 상위 집합입니다. 예를 들어 Visual Basic 또는 c # 소스 파일 중 하나를 변경한 경우 게시 작업을 통해 해당 어셈블리가 자동으로 다시 작성 됩니다.

 Mage.exe 명령줄 도구를 사용 하 여 매니페스트를 만드는 전체 배포를 생성 하는 방법에 대 한 자세한 내용은 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)를 참조 하세요.

## <a name="create-and-build-a-basic-clickonce-application-with-msbuild"></a>MSBuild를 사용 하 여 기본 ClickOnce 응용 프로그램 만들기 및 빌드

#### <a name="to-create-and-publish-a-clickonce-project"></a>ClickOnce 프로젝트를 만들고 게시 하려면

1. Visual Studio를 연 다음 새 프로젝트를 만듭니다.

    **Windows 데스크톱 응용 프로그램** 프로젝트 템플릿을 선택 하 고 프로젝트의 이름을로 `CmdLineDemo` 합니다.

1. **빌드** 메뉴에서 **게시** 명령을 클릭 합니다.

    이 단계에서는 프로젝트가 응용 프로그램 배포를 만들도록 적절히 구성 되어 있는지 확인 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 합니다.

    게시 마법사가 나타납니다.

1. 게시 마법사에서 **마침**을 클릭 합니다.

    Visual Studio에서 *Publish.htm*이라는 기본 웹 페이지를 생성 하 고 표시 합니다.

1. 프로젝트를 저장 하 고 저장 된 폴더 위치를 기록해 둡니다.

   위의 단계는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 처음 게시 된 프로젝트를 만듭니다. 이제 IDE 외부에서 빌드를 재현할 수 있습니다.

#### <a name="to-reproduce-the-build-from-the-command-line"></a>명령줄에서 빌드를 재현 하려면

1. [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]을 종료합니다.

2. Windows **시작** 메뉴에서 **모든 프로그램**을 클릭 하 고 **Microsoft Visual Studio**한 다음 **Visual Studio Tools**하 고 **Visual Studio 명령 프롬프트**를 클릭 합니다. 그러면 현재 사용자의 루트 폴더에서 명령 프롬프트가 열립니다.

3. **Visual Studio 명령 프롬프트**에서 방금 만든 프로젝트의 위치로 현재 디렉터리를 변경 합니다. 예를 들어 `chdir My Documents\Visual Studio\Projects\CmdLineDemo`을(를) 입력합니다.

4. "프로젝트를 만들고 게시 하려면"에 생성 된 기존 파일을 제거 하려면을 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 입력 `rmdir /s publish` 합니다.

    이 단계는 선택 사항 이지만, 명령줄 빌드에서 새 파일이 모두 생성 되었는지 확인 합니다.

5. `msbuild /target:publish`을 입력합니다.

   위의 단계를 수행 하면 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] **Publish**라는 프로젝트의 하위 폴더에 전체 응용 프로그램 배포가 생성 됩니다. *Cmdlinedemo. 응용 프로그램* 은 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 배포 매니페스트입니다. *0.0.0 CmdLineDemo_1* 폴더에는 응용 프로그램 매니페스트 *CmdLineDemo.exe* 및 *CmdLineDemo.exe*파일이 포함 되어 있습니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] *Setup.exe* 은 부트스트래퍼로, 기본적으로 .NET Framework를 설치 하도록 구성 되어 있습니다. Dotnetfx.exe 폴더는 .NET Framework에 대 한 재배포 가능 패키지를 포함 합니다. 웹을 통해 또는 UNC 또는 CD/DVD를 통해 응용 프로그램을 배포 하는 데 필요한 전체 파일 집합입니다.
   
> [!NOTE]
> MSBuild 시스템은 출력 위치 (예:)를 지정 **하는 데이 옵션을** 사용 합니다 `msbuild /t:publish /p:PublishDir="<specific location>"` .

## <a name="publish-properties"></a>속성 게시
 위의 절차에서 응용 프로그램을 게시 하면 게시 마법사에서 다음 속성이 프로젝트 파일에 삽입 됩니다. 이러한 속성은 응용 프로그램을 생성 하는 방법에 직접적인 영향을 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 *Cmdlinedemo. .vbproj*  /  *cmdlinedemo*:

```xml
<AssemblyOriginatorKeyFile>WindowsApplication3.snk</AssemblyOriginatorKeyFile>
<GenerateManifests>true</GenerateManifests>
<TargetZone>LocalIntranet</TargetZone>
<PublisherName>Microsoft</PublisherName>
<ProductName>CmdLineDemo</ProductName>
<PublishUrl>http://localhost/CmdLineDemo</PublishUrl>
<Install>true</Install>
<ApplicationVersion>1.0.0.*</ApplicationVersion>
<ApplicationRevision>1</ApplicationRevision>
<UpdateEnabled>true</UpdateEnabled>
<UpdateRequired>false</UpdateRequired>
<UpdateMode>Foreground</UpdateMode>
<UpdateInterval>7</UpdateInterval>
<UpdateIntervalUnits>Days</UpdateIntervalUnits>
<UpdateUrlEnabled>false</UpdateUrlEnabled>
<IsWebBootstrapper>true</IsWebBootstrapper>
<BootstrapperEnabled>true</BootstrapperEnabled>
```

 이러한 속성은 프로젝트 파일 자체를 변경 하지 않고 명령줄에서 재정의할 수 있습니다. 예를 들어 다음은 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 부트스트래퍼 없이 응용 프로그램 배포를 빌드합니다.

```cmd
msbuild /target:publish /property:BootstrapperEnabled=false
```

 게시 속성은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **프로젝트 디자이너**의 **게시**, **보안**및 **서명** 속성 페이지에서에 제어 됩니다. 다음은 응용 프로그램 디자이너의 다양 한 속성 페이지에서 각을 설정 하는 방법에 대 한 설명과 함께 게시 속성에 대 한 설명입니다.

- `AssemblyOriginatorKeyFile` 응용 프로그램 매니페스트를 서명 하는 데 사용 되는 키 파일을 결정 합니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 이 동일한 키를 사용 하 여 어셈블리에 강력한 이름을 할당할 수도 있습니다. 이 속성은 **프로젝트 디자이너**의 **서명** 페이지에서 설정 합니다.

  **보안** 페이지에 설정 되는 속성은 다음과 같습니다.

- **ClickOnce 보안 설정 사용** 매니페스트 생성 여부를 결정 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 합니다. 프로젝트를 처음 만들 때 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 매니페스트 생성은 기본적으로 해제 되어 있습니다. 처음으로 게시 하는 경우 마법사가이 플래그를 자동으로 설정 합니다.

- **Targetzone** 은 응용 프로그램 매니페스트로 내보낼 신뢰 수준을 결정 합니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 가능한 값은 "Internet", "LocalIntranet" 및 "Custom"입니다. 인터넷 및 LocalIntranet를 사용 하면 기본 권한 집합이 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 매니페스트로 내보내집니다. LocalIntranet은 기본값이 며, 기본적으로 완전 신뢰를 의미 합니다. 사용자 지정 *은 기본 응용 프로그램 매니페스트 파일* 에 명시적으로 지정 된 권한만 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램 매니페스트로 내보내도록 지정 합니다. *응용 프로그램 매니페스트* 파일은 신뢰 정보 정의만 포함 하는 부분 매니페스트 파일입니다. 이 파일은 **보안** 페이지에서 권한을 구성할 때 프로젝트에 자동으로 추가 되는 숨겨진 파일입니다.

  **게시** 페이지에 설정 된 속성은 다음과 같습니다.

- `PublishUrl` 는 IDE에서 응용 프로그램이 게시 되는 위치입니다. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `InstallUrl` 또는 `UpdateUrl` 속성이 지정 되지 않은 경우 응용 프로그램 매니페스트에 삽입 됩니다.

- `ApplicationVersion` 응용 프로그램의 버전을 지정 합니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . 이는 네 자리 버전 번호입니다. 마지막 자릿수가 "*" 이면는 `ApplicationRevision` 빌드 시 매니페스트에 삽입 된 값을 대체 합니다.

- `ApplicationRevision` 수정 버전을 지정 합니다. IDE에 게시할 때마다 증가 하는 정수입니다. 명령줄에서 수행 되는 빌드에 대해 자동으로 증가 하지 않습니다.

- `Install` 응용 프로그램이 설치 된 응용 프로그램 인지 아니면 웹에서 실행 되는 응용 프로그램 인지를 결정 합니다.

- `InstallUrl` (표시 되지 않음)는 사용자가 응용 프로그램을 설치 하는 위치입니다. 지정 된 경우 속성을 사용 하는 경우이 값이 *setup.exe* 부트스트래퍼에 기록 됩니다 `IsWebBootstrapper` . 을 지정 하지 않은 경우에도 응용 프로그램 매니페스트에 삽입 됩니다 `UpdateUrl` .

- `SupportUrl` (표시 되지 않음)는 설치 된 응용 프로그램에 대 한 **프로그램 추가/제거** 대화 상자에서 연결 된 위치입니다.

  다음 속성은 **게시** 페이지에서 액세스할 수 있는 **응용 프로그램 업데이트** 대화 상자에서 설정 됩니다.

- `UpdateEnabled` 응용 프로그램에서 업데이트를 확인 해야 하는지 여부를 나타냅니다.

- `UpdateMode` 포그라운드 업데이트 또는 백그라운드 업데이트를 지정 합니다.

- `UpdateInterval` 응용 프로그램이 업데이트를 확인 하는 빈도를 지정 합니다.

- `UpdateIntervalUnits``UpdateInterval`값이 시간, 일 또는 주 단위로 지정 되는지 여부를 지정 합니다.

- `UpdateUrl` (표시 되지 않음) 응용 프로그램에서 업데이트를 수신 하는 위치입니다. 지정 된 경우이 값은 응용 프로그램 매니페스트에 삽입 됩니다.

  **게시 페이지에서** 액세스할 수 있는 **게시 옵션** 대화 상자에는 다음 속성이 설정 되어 있습니다.

- `PublisherName` 응용 프로그램을 설치 하거나 실행할 때 표시 되는 프롬프트에 표시 되는 게시자의 이름을 지정 합니다. 설치 된 응용 프로그램의 경우 **시작** 메뉴에서 폴더 이름을 지정 하는 데도 사용 됩니다.

- `ProductName` 응용 프로그램을 설치 하거나 실행할 때 표시 되는 프롬프트에 표시 되는 제품의 이름을 지정 합니다. 설치 된 응용 프로그램의 경우 **시작** 메뉴에서 바로 가기 이름을 지정 하는 데도 사용 됩니다.

  다음 속성은 **게시** 페이지에서 액세스할 수 있는 **필수 구성 요소** 대화 상자에서 설정 됩니다.

- `BootstrapperEnabled`*setup.exe* 부트스트래퍼를 생성할지 여부를 결정 합니다.

- `IsWebBootstrapper`*setup.exe* 부트스트래퍼가 웹 또는 디스크 기반 모드에서 작동 하는지 여부를 결정 합니다.

## <a name="installurl-supporturl-publishurl-and-updateurl"></a>InstallURL, SupportUrl, PublishURL, 및 UpdateURL
 다음 표에서는 ClickOnce 배포에 대 한 네 가지 URL 옵션을 보여 줍니다.

|URL 옵션|설명|
|----------------|-----------------|
|`PublishURL`|ClickOnce 응용 프로그램을 웹 사이트에 게시 하는 경우에 필요 합니다.|
|`InstallURL`|선택 사항입니다. 설치 사이트가와 다른 경우이 URL 옵션을 설정 `PublishURL` 합니다. 예를 들어를 `PublishURL` FTP 경로로 설정 하 고을 `InstallURL` 웹 URL로 설정할 수 있습니다.|
|`SupportURL`|선택 사항입니다. 지원 사이트가와 다른 경우이 URL 옵션을 설정 `PublishURL` 합니다. 예를 들어를 `SupportURL` 회사의 고객 지원 웹 사이트로 설정할 수 있습니다.|
|`UpdateURL`|선택 사항입니다. 업데이트 위치가와 다른 경우이 URL 옵션을 설정 합니다 `InstallURL` . 예를 들어를 `PublishURL` FTP 경로로 설정 하 고을 `UpdateURL` 웹 URL로 설정할 수 있습니다.|

## <a name="see-also"></a>추가 정보
- <xref:Microsoft.Build.Tasks.GenerateBootstrapper>
- <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>
- <xref:Microsoft.Build.Tasks.GenerateDeploymentManifest>
- [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)
- [연습: 수동으로 ClickOnce 애플리케이션 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
