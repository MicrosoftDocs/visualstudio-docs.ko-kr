---
title: 개발 및 테스트 환경에 게시하기 위해 Windows PowerShell 스크립트 사용하기 | Microsoft Docs
description: Visual Studio에서 Windows PowerShell 스크립트를 사용하여 개발 및 테스트 환경에 게시하는 방법을 알아보세요.
author: ghogen
manager: jillfra
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 6913ec4c80b5cb87cf6cd980ff2da73fab309a02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84184018"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Windows PowerShell 스크립트를 사용하여 개발 및 테스트 환경에 게시

Visual Studio에서 웹 애플리케이션을 만들 경우 Windows PowerShell 스크립트를 생성하여 나중에 Azure에 Azure App Service 또는 가상 머신으로 웹 사이트 게시를 자동화하는 데 사용할 수 있습니다. Visual Studio 편집기에서 요구 사항에 맞게 Windows PowerShell 스크립트를 편집 및 확장하거나 스크립트를 기존 빌드, 테스트, 게시 스크립트와 통합할 수 있습니다.

이러한 스크립트를 사용하면 일시적으로 사용할 사이트의 사용자 지정 버전(개발 및 테스트 환경이라고도 함)을 프로비저닝할 수 있습니다. 예를 들어 Azure 가상 컴퓨터 또는 웹 사이트의 스테이징 슬롯에 특정 버전의 웹 사이트를 설정하고 테스트 제품군 실행, 버그 재현, 버그 수정 사항 테스트, 제안된 변경 사항 시험, 데모 또는 프레젠테이션을 위한 사용자 지정 환경 설정을 수행할 수 있습니다. 프로젝트를 게시하는 스크립트를 만든 다음 필요에 따라 스크립트를 다시 실행하여 동일한 환경을 다시 만들거나 웹 애플리케이션의 자체 빌드로 스크립트를 실행하여 테스트를 위한 사용자 지정 환경을 만들 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

* Azure SDK 2.3 이상 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/)를 참조하세요. (웹 프로젝트용 스크립트를 생성하기 위해 Azure SDK는 필요하지 않습니다. 이 기능은 클라우드 서비스의 웹 역할이 아닌 웹 프로젝트용입니다.)
* Azure PowerShell 0.7.4 이상 [Azure PowerShell 설치 및 구성 방법](/powershell/azure/overview)을 참조하세요.
* [Windows PowerShell 3.0](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control) 이상

## <a name="additional-tools"></a>추가 도구

Azure 개발 시 Visual Studio에서 PowerShell을 사용하기 위한 추가 도구와 리소스를 사용할 수 있습니다. [Visual Studio용 PowerShell](https://visualstudiogallery.msdn.microsoft.com/c9eb3ba8-0c59-4944-9a62-6eee37294597)을 참조하세요.

## <a name="generating-the-publish-scripts"></a>게시 스크립트 생성

새 프로젝트를 만들 때 [이 지침](/azure/virtual-machines/windows/classic/web-app-visual-studio?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json)을 따라 웹 사이트를 호스팅하는 가상 머신의 게시 스크립트를 생성할 수 있습니다. 또한 [Azure App Service에서 웹앱용 게시 스크립트를 생성](/azure/app-service/scripts/app-service-powershell-deploy-github)할 수도 있습니다.

## <a name="scripts-that-visual-studio-generates"></a>Visual Studio에서 생성하는 스크립트

Visual Studio는 Windows PowerShell 파일이 두 개 포함된 **PublishScripts**라고 하는 솔루션 수준의 폴더, 가상 컴퓨터 또는 웹 사이트용 게시 스크립트 및 스크립트에서 사용할 수 있는 함수가 포함된 모듈을 생성합니다. Visual Studio는 또한 배포하는 프로젝트의 상세 정보를 지정하는 JSON 형식으로 파일을 생성합니다.

### <a name="windows-powershell-publish-script"></a>Windows PowerShell 게시 스크립트

게시 스크립트에는 웹 사이트 또는 가상 머신에 배포하기 위한 구체적 게시 단계가 포함되어 있습니다. Visual Studio는 Windows PowerShell 배포를 위한 구문 색 지정을 제공합니다. 함수의 도움말을 사용할 수 있으며 달라진 요구 사항에 맞게 스크립트의 함수를 자유롭게 편집할 수 있습니다.

### <a name="windows-powershell-module"></a>Windows PowerShell 모듈

Visual Studio에서 생성하는 Windows PowerShell 모듈에는 게시 스크립트가 사용하는 함수가 포함되어 있습니다. 이러한 Azure PowerShell 함수는 수정할 수 없습니다. [Azure PowerShell 설치 및 구성 방법](/powershell/azure/overview)을 참조하세요.

### <a name="json-configuration-file"></a>JSON 구성 파일

JSON 파일은 **Configurations** 폴더에 만들어지며, Azure에 배포할 리소스를 정확하게 지정하는 구성 데이터가 포함되어 있습니다. 웹 사이트를 만든 경우 Visual Studio가 생성하는 파일의 이름은 project-name-WAWS-dev.json이며 가상 머신을 만든 경우에는 project name-VM-dev.json입니다. 다음은 웹 사이트를 만들 때 생성된 JSON 구성 파일의 예입니다. 대부분의 값은 따로 설명이 필요하지 않습니다. 웹 사이트 이름은 Azure에서 생성하므로 프로젝트 이름과 일치하지 않을 수 있습니다.

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

가상 컴퓨터를 만들면 JSON 구성 파일이 다음과 유사합니다. 클라우드 서비스가 가상 머신의 컨테이너로 생성됩니다. 가상 머신에 HTTP 및 HTTPS를 통한 웹 액세스에 사용할 일반적 엔드포인트가 포함되어 있으며, 웹 배포용 엔드포인트도 포함되어 있어 로컬 컴퓨터, 원격 데스크톱 및 Windows PowerShell에서 웹 사이트에 게시할 수 잇습니다.

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

JSON 구성을 편집하여 게시 스크립트를 실행할 때 발생하는 결과를 변경할 수 있습니다. `cloudService` 및 `virtualMachine` 섹션은 필수이며 `databases` 섹션은 필요하지 않을 경우 삭제할 수 있습니다. Visual Studio에서 생성한 기본 구성 파일이 비어 있는 속성은 선택 사항이고, 기본 구성 파일에 값이 있는 속성은 필수 속성입니다.

Azure에 단일 프로덕션 사이트가 아닌 여러 배포 환경(슬롯이라고 함)이 포함된 웹 사이트가 있을 경우 JSON 구성 파일에서 웹 사이트 이름에 슬롯 이름을 포함할 수 있습니다. 예를 들어 이름이 **mysite**인 웹 사이트가 있고 이 웹 사이트의 슬롯 이름이 **test**이면 URI는 `mysite-test.cloudapp.net`입니다. 그러나 구성 파일에서 사용할 올바른 이름은 mysite(test)입니다. 구독에 웹 사이트와 슬롯이 이미 있는 경우에만 이렇게 할 수 있습니다. 없을 경우에는 슬롯을 지정하지 않고 스크립트를 실행한 다음 [Azure Portal](https://portal.azure.com/)에 슬롯을 만들고 수정한 웹 사이트 이름으로 스크립트를 실행합니다. 웹앱의 배포 슬롯에 대한 자세한 내용은 [Azure App Service에서 웹앱에 대한 스테이징 환경 설정](/azure/app-service/web-sites-staged-publishing)을 참조하세요.

## <a name="how-to-run-the-publish-scripts"></a>게시 스크립트 실행 방법

이전에 Windows PowerShell 스크립트를 실행한 적이 없는 경우 우선 스크립트를 실행할 수 있도록 실행 정책을 설정해야 합니다. 이 정책은 사용자가 맬웨어 또는 바이러스에 취약한 Windows PowerShell 스크립트를 실행하지 못하도록 방지하는 보안 기능입니다.

### <a name="run-the-script"></a>스크립트 실행

1. 프로젝트의 웹 배포 패키지를 만듭니다. 웹 배포 패키지는 웹 사이트 또는 가상 머신에 복사하려는 파일이 포함된 압축 아카이브(.zip 파일)입니다. Visual Studio에서 모든 웹 애플리케이션에 사용할 웹 배포 패키지를 만들 수 있습니다.

   ![웹 배포 패키지 만들기](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   자세한 내용은 [방법: Visual Studio에서 웹 배포 패키지 만들기](https://msdn.microsoft.com/library/dd465323.aspx)를 참조하세요. 또한 [게시 스크립트 사용자 지정 및 확장](#customizing-and-extending-the-publish-scripts)에서 설명하는 대로 웹 배포 패키지 생성을 자동화할 수 있습니다.

1. **솔루션 탐색기**에서 스크립트의 상황에 맞는 메뉴를 연 다음 **PowerShell ISE로 열기**를 선택합니다.
1. 이 컴퓨터에서 Windows PowerShell 스크립트를 처음으로 실행하는 경우 관리자 권한으로 명령 프롬프트 창을 열고 다음 명령을 입력합니다.

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. 다음 명령을 사용하여 Azure에 로그인합니다.

    ```powershell
    Add-AzureAccount
    ```

    메시지가 표시되면 사용자 이름과 암호를 입력합니다.

    스크립트를 자동화하면 이 방법으로 Azure 자격 증명을 제공할 수 없습니다. 대신 `.publishsettings` 파일을 사용하여 자격 증명을 제공해야 합니다. 한 번만 **Get-AzurePublishSettingsFile** 명령을 사용하여 Azure에서 파일을 다운로드한 다음 **Import-AzurePublishSettingsFile**을 사용하여 파일을 가져옵니다. 자세한 지침은 [Azure PoweShell 설치 및 구성 방법](/powershell/azure/overview)을 참조하세요.

1. (선택 사항) 웹 애플리케이션을 게시하지 않고 가상 머신, 데이터베이스, 웹 사이트와 같은 Azure 리소스를 만들려면 **-Configuration** 인수를 JSON 구성 파일로 설정하고 **Publish-WebApplication.ps1** 명령을 사용합니다. 이 명령줄은 JSON 구성 파일을 사용하여 만들 리소스를 결정합니다. 여기서 다른 명령줄 인스턴스에 대해 기본 설정을 사용하므로 리소스를 만들지만 웹 애플리케이션을 게시하지 않습니다. –Verbose 옵션으로 진행 상황에 대한 자세한 정보를 확인할 수 있습니다.

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. 다음 예제 중 하나와 같이 **Publish-WebApplication.ps1** 명령을 사용하여 스크립트를 호출하고 웹 애플리케이션을 게시합니다. 구독 이름, 게시 패키지 이름, 가상 머신 자격 증명, 데이터베이스 서버 자격 증명과 같은 다른 인수의 기본 설정을 재정의하려면 이러한 매개 변수를 지정합니다. 게시 프로세스의 진행률을 자세히 보려면 **-Verbose** 옵션을 사용합니다.

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    가상 머신을 만드는 경우 다음과 유사한 명령을 사용합니다. 이 예제는 여러 데이터베이스의 자격 증명을 지정하는 방법을 보여 줍니다. 이러한 스크립트가 만드는 가상 머신에서 SSL 인증서는 신뢰할 수 있는 루트 인증 기관에서 제공한 인증서가 아닙니다. 따라서 **–AllowUntrusted** 옵션을 사용해야 합니다.

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    스크립트가 데이터베이스를 만들 수 있지만 데이터베이스 서버는 만들 수 없습니다. 데이터베이스 서버를 만들려면 Azure 모드에서 **New-AzureSqlDatabaseServer** 함수를 사용합니다.

## <a name="customizing-and-extending-the-publish-scripts"></a>게시 스크립트 사용자 지정 및 확장

게시 스크립트 및 JSON 구성 파일을 사용자 지정할 수 있습니다. Windows PowerShell 모듈 **AzureWebAppPublishModule.psm1** 의 함수는 수정할 수 없습니다. 다른 데이터베이스를 지정하거나 가상 컴퓨터의 일부 속성을 변경하려면 JSON 구성 파일을 편집합니다. 스크립트의 기능을 확장하여 프로젝트 빌드 및 테스트를 자동화하려면 **Publish-WebApplication.ps1**에 함수 스텁을 구현합니다.

프로젝트 빌드를 자동화하려면 이 코드 예제와 같이 `New-WebDeployPackage` 에 MSBuild를 호출하는 코드를 추가합니다. MSBuild 명령에 대한 경로는 설치한 Visual Studio 버전에 따라 다릅니다. 올바른 경로를 가져오려면 이 예제와 같이 **Get-MSBuildCmd**함수를 사용합니다.

### <a name="to-automate-building-your-project"></a>프로젝트 빌드를 자동화하려면

1. 전역 param 섹션에 `$ProjectFile` 매개 변수를 추가합니다.

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. `Get-MSBuildCmd` 함수를 스크립트 파일에 복사합니다.

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. `New-WebDeployPackage`을(를) 다음 코드로 바꾸고 `$msbuildCmd` 생성 줄에서 자리 표시자를 바꿉니다. 이 코드는 Visual Studio 2015용입니다. Visual Studio 2017을 사용 하는 경우 **VisualStudioVersion** 속성을로 변경 `15.0` `12.0` 합니다 (Visual Studio 2013의 경우).

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    웹 애플리케이션을 빌드하려면 MsBuild.exe를 사용합니다. 도움말은 다음에서 MSBuild 명령줄 참조를 참조 하세요. [http://go.microsoft.com/fwlink/?LinkId=391339](https://msdn.microsoft.com/library/ms164311.aspx)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=14.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>빌드 명령 실행 시작

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. 이 줄보다 먼저 `New-WebDeployPackage` 함수를 호출합니다. 웹 앱의 경우 `$Config = Read-ConfigFile $Configuration`, 가상 머신의 경우 `$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)`.

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. 다음 예제와 같이 `$Project` 인수 전달을 사용하여 명령줄에서 사용자 지정 스크립트를 호출합니다.

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    애플리케이션 테스트를 자동화하려면 `Test-WebApplication`에 코드를 추가합니다. 이러한 함수가 호출되는 **Publish-WebApplication.ps1** 의 줄에서 주석 처리를 제거합니다. 구현을 제공하지 않을 경우 Visual Studio로 프로젝트를 수동으로 빌드한 다음 게시 스크립트를 실행하여 Azure에 게시합니다.

## <a name="publishing-function-summary"></a>게시 함수 요약
Windows PowerShell 명령 프롬프트에서 사용할 수 있는 함수에 대한 도움말을 보려면 `Get-Help function-name`명령을 사용합니다. 도움말에는 매개 변수 도움말과 예제가 포함됩니다. 동일한 도움말 텍스트가 스크립트 소스 파일 **azurewebapppublishmodule.psm1. .psm1** 및 **Publish-WebApplication.ps1**에도 있습니다. 스크립트와 도움말은 Visual Studio 언어로 현지화됩니다.

**AzureWebAppPublishModule**

| 함수 이름 | Description |
| --- | --- |
| Add-AzureSQLDatabase |새 Azure SQL 데이터베이스를 만듭니다. |
| Add-AzureSQLDatabases |Visual Studio에서 생성하는 JSON 구성 파일의 값으로 Azure SQL 데이터베이스를 만듭니다. |
| Add-AzureVM |Azure 가상 머신을 만들고 배포된 VM의 URL을 반환합니다. 함수가 필수 구성 요소를 설정한 다음 **New-AzureVM** 함수(Azure 모듈)를 호출하여 새 가상 머신을 만듭니다. |
| Add-AzureVMEndpoints |가상 머신에 새 입력 엔드포인트를 추가하고 새 엔드포인트로 가상 머신을 반환합니다. |
| Add-AzureVMStorage |현재 구독에 새 Azure Storage 계정을 만듭니다. 계정 이름은 "devtest"로 시작하고 그 다음에 고유한 영숫자 문자열이 포함됩니다. 함수에서 새 스토리지 계정의 이름을 반환합니다. 새 스토리지 계정에 대해 위치 또는 선호도 그룹을 지정합니다. |
| Add-AzureWebsite |지정된 이름 및 위치로 웹 사이트를 만듭니다. 이 함수는 Azure 모듈에서 **New-AzureWebsite** 함수라고 합니다. 구독에 이미 지정된 이름의 웹 사이트가 없을 경우 이 함수는 웹 사이트를 만들고 웹 사이트 개체를 반환합니다. 그렇지 않으면 `$null`을 반환합니다. |
| Backup-구독 |현재 Azure 구독을 스크립트 범위의 `$Script:originalSubscription` 변수에 저장합니다. 이 함수는 현재 Azure 구독(`Get-AzureSubscription -Current`에서 가져옴) 및 해당 스토리지 계정, 이 스크립트로 변경된 구독(`$UserSpecifiedSubscription` 변수에 저장) 및 해당 스토리지 계정을 스크립트 범위에 저장합니다. 이러한 값을 저장하면 원래 현재 상태가 변경된 경우 `Restore-Subscription` 등의 함수를 사용하여 현재 구독 및 스토리지 계정을 현재 상태로 복원할 수 있습니다. |
| Find-AzureVM |지정된 Azure 가상 머신을 가져옵니다. |
| Format-DevTestMessageWithTime |메시지 앞에 날짜와 시간을 추가합니다. 이 함수는 오류 및 자세한 정보 표시 스트림에 작성되는 메시지를 위해 설계되었습니다. |
| Get-AzureSQLDatabaseConnectionString |연결 문자열을 조립하여 Azure SQL 데이터베이스에 연결합니다. |
| Get-AzureVMStorage |*지정 된 위치 또는 선호도 그룹에서 이름 패턴이 "devtest" (대/소문자 구분 안 함) 인 첫 번째 저장소 계정의 이름을 반환 합니다. "Devtest*" 저장소 계정이 위치 또는 선호도 그룹과 일치 하지 않으면 함수는이를 무시 합니다. 위치 또는 선호도 그룹을 지정합니다. |
| Get-MSDeployCmd |MsDeploy.exe 도구를 실행하는 명령을 반환합니다. |
| New-AzureVMEnvironment |JSON 구성 파일의 값과 일치하는 구독에서 가상 머신을 검색하거나 만듭니다. |
| Publish-WebPackage |MsDeploy.exe 및 웹 게시 패키지인 .Zip 파일을 사용하여 리소스를 웹 사이트에 배포합니다. 이 함수는 출력을 생성하지 않습니다. MSDeploy.exe에 대한 호출이 실패할 경우 함수가 예외를 throw합니다. 더 자세한 출력을 가져오려면 **-Verbose** 옵션을 사용합니다. |
| Publish-WebPackageToVM |매개 변수 값을 확인한 다음 **Publish-WebPackage** 함수를 호출합니다. |
| Read-ConfigFile |JSON 구성 파일의 유효성을 검사하고 선택한 값의 해시 테이블을 반환합니다. |
| Restore-Subscription |현재 구독을 원래 구독으로 다시 설정합니다. |
| Test-AzureModule |설치된 Azure 모듈 버전이 0.7.4 이상인 경우 `$true` 을(를) 반환합니다. 모듈이 설치되지 않았거나 이전 버전인 경우 `$false` 을(를) 반환합니다. 이 함수에는 매개 변수가 없습니다. |
| Test-AzureModuleVersion |Azure 모듈의 버전이 0.7.4 이상인 경우 `$true` 을(를) 반환합니다. 모듈이 설치되지 않았거나 이전 버전인 경우 `$false` 을(를) 반환합니다. 이 함수에는 매개 변수가 없습니다. |
| Test-HttpsUrl |입력 URL을 System.Uri 개체로 변환합니다. URL이 절대적이고 해당 스키마가 https인 경우 `$True` 을(를) 반환합니다. URL이 상대적이고 해당 스키마가 HTTPS가 아니거나 입력 문자열을 URL로 변환할 수 없을 경우 `$false` 을(를) 반환합니다. |
| Test-Member |속성 또는 메서드가 개체의 구성원인 경우 `$true` 을(를) 반환합니다. 그렇지 않으면 `$false`을(를) 반환합니다. |
| Write-ErrorWithTime |현재 시간을 접두사로 하는 오류 메시지를 작성합니다. 이 함수는 **Format-DevTestMessageWithTime** 함수를 호출하고 메시지를 쓰기 전의 시간을 오류 스트림 앞에 추가합니다. |
| Write-HostWithTime |현재 시간을 접두사로 하는 호스트 프로그램(**Write-Host**)에 메시지를 씁니다. 호스트 프로그램에 쓰는 효과는 다양합니다. Windows PowerShell을 호스팅하는 대부분의 프로그램은 이러한 메시지를 표준 출력에 씁니다. |
| Write-VerboseWithTime |현재 시간을 접두사로 하는 자세한 정보 메시지를 작성합니다. 이 함수는 **Write-Verbose**를 호출하므로 **Verbose** 매개 변수로 스크립트가 실행되거나 **VerbosePreference** 기본 설정이 **계속**으로 설정된 경우에만 메시지가 표시됩니다. |

**Publish-WebApplication**

| 함수 이름 | Description |
| --- | --- |
| New-AzureWebApplicationEnvironment |웹 사이트, 가상 머신과 같은 Azure 리소스를 만듭니다. |
| New-WebDeployPackage |이 함수는 구현되지 않았습니다. 이 함수에 명령을 추가하여 프로젝트를 빌드할 수 있습니다. |
| Publish-AzureWebApplication |Azure에 웹 애플리케이션을 게시합니다. |
| Publish-WebApplication |Visual Studio 웹 프로젝트를 위한 Web Apps, 가상 머신, SQL 데이터베이스, 스토리지 계정을 만들고 배포합니다. |
| Test-WebApplication |이 함수는 구현되지 않았습니다. 이 함수에 명령을 추가하여 애플리케이션을 테스트할 수 있습니다. |

## <a name="next-steps"></a>다음 단계
[Windows PowerShell을 사용하여 스크립팅](/powershell/scripting/overview)을 읽어 PowerShell 스크립팅에 대해 자세히 알아보고 [스크립트 센터](https://azure.microsoft.com/documentation/scripts/)에서 기타 Azure PowerShell 스크립트에 대해 알아보세요.
