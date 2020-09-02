---
title: '방법: ClickOnce를 사용 하 여 여러 버전의 .NET Framework에서 실행할 수 있는 응용 프로그램 배포 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, multiple .NET Framework versions
- ClickOnce deployment, multiple .NET Framework versions
- deploying applications [ClickOnce], multiple .NET Framework versions
ms.assetid: e0a8c330-21bc-4eb2-b936-fd0f3c3221f1
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 164fe64f360e41c06ef3f7bfd2d8091a6ebefecd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679943"
---
# <a name="how-to-use-clickonce-to-deploy-applications-that-can-run-on-multiple-versions-of-the-net-framework"></a>방법: ClickOnce를 사용하여 여러 버전의 .NET Framework에서 실행할 수 있는 애플리케이션 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce 배포 기술을 사용 하 여 여러 버전의 .NET Framework를 대상으로 하는 응용 프로그램을 배포할 수 있습니다. 이렇게 하려면 응용 프로그램 및 배포 매니페스트를 생성 하 고 업데이트 해야 합니다.  
  
> [!NOTE]
> 여러 버전의 .NET Framework를 대상으로 하도록 응용 프로그램을 변경 하기 전에 응용 프로그램이 여러 버전의 .NET Framework으로 실행 되는지 확인 해야 합니다. 버전 공용 언어 런타임은 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 2.0, .NET Framework 3.0 및 .NET Framework 3.5와 .NET Framework 다릅니다.  
  
 이 프로세스에는 다음 단계가 필요 합니다.  
  
1. 응용 프로그램 및 배포 매니페스트를 생성 합니다.  
  
2. 여러 .NET Framework 버전을 나열 하도록 배포 매니페스트를 변경 합니다.  
  
3. app.config 파일을 변경 하 여 호환 되는 .NET Framework 런타임 버전을 나열 합니다.  
  
4. 응용 프로그램 매니페스트를 변경 하 여 종속 어셈블리를 .NET Framework 어셈블리로 표시 합니다.  
  
5. 응용 프로그램 매니페스트에 서명 합니다.  
  
6. 배포 매니페스트를 업데이트 하 고 서명 합니다.  
  
### <a name="to-generate-the-application-and-deployment-manifests"></a>응용 프로그램 및 배포 매니페스트를 생성 하려면  
  
- 게시 마법사 또는 프로젝트 디자이너의 게시 페이지를 사용 하 여 응용 프로그램을 게시 하 고 응용 프로그램 및 배포 매니페스트 파일을 생성 합니다. 자세한 내용은 [방법: 게시 마법사를 사용 하 여 ClickOnce 응용 프로그램 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) 또는 [프로젝트 디자이너, 게시 페이지를](../ide/reference/publish-page-project-designer.md)참조 하세요.  
  
### <a name="to-change-the-deployment-manifest-to-list-the-multiple-net-framework-versions"></a>여러 .NET Framework 버전을 나열 하도록 배포 매니페스트를 변경 하려면  
  
1. 게시 디렉터리에서 Visual Studio의 XML 편집기를 사용 하 여 배포 매니페스트를 엽니다. 배포 매니페스트에는. 응용 프로그램 파일 이름 확장명이 있습니다.  
  
2. XML 코드를 `<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">` 및 요소 사이에서 `</compatibleFrameworks>` 응용 프로그램에 대해 지원 되는 .NET Framework 버전을 나열 하는 xml로 바꿉니다.  
  
     다음 표에서는 사용할 수 있는 일부 .NET Framework 버전 및 배포 매니페스트에 추가할 수 있는 해당 XML을 보여 줍니다.  
  
    |.NET Framework 버전|XML|  
    |----------------------------|---------|  
    |4 클라이언트|\<framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />|  
    |4 전체|\<framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />|  
    |3.5 클라이언트|\<framework targetVersion="3.5" profile="Client" supportedRuntime="2.0.50727" />|  
    |3.5 전체|\<framework targetVersion="3.5" profile="Full" supportedRuntime="2.0.50727" />|  
    |3.0|\<framework targetVersion="3.0" supportedRuntime="2.0.50727" />|  
  
### <a name="to-change-the-appconfig-file-to-list-the-compatible-net-framework-runtime-versions"></a>호환 되는 .NET Framework 런타임 버전을 나열 하도록 app.config 파일을 변경 하려면  
  
1. 솔루션 탐색기에서 Visual Studio의 XML 편집기를 사용 하 여 App.config 파일을 엽니다.  
  
2. `<startup>` `</startup>` 응용 프로그램에 대해 지원 되는 .NET Framework 런타임을 나열 하는 xml을 사용 하 여 및 요소 사이에 xml 코드를 바꾸거나 추가 합니다.  
  
     다음 표에서는 사용할 수 있는 일부 .NET Framework 버전 및 배포 매니페스트에 추가할 수 있는 해당 XML을 보여 줍니다.  
  
    |.NET Framework 런타임 버전|XML|  
    |------------------------------------|---------|  
    |4 클라이언트|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0,Profile=Client" />|  
    |4 전체|\<supportedRuntime version="v4.0.30319" sku=".NETFramework,Version=v4.0" />|  
    |3.5 전체|\<supportedRuntime version="v2.0.50727"/>|  
    |3.5 클라이언트|\<supportedRuntime version="v2.0.50727" sku="Client"/>|  
  
### <a name="to-change-the-application-manifest-to-mark-dependent-assemblies-as-net-framework-assemblies"></a>종속 어셈블리를 .NET Framework 어셈블리로 표시 하도록 응용 프로그램 매니페스트를 변경 하려면  
  
1. 게시 디렉터리에서 Visual Studio의 XML 편집기를 사용 하 여 응용 프로그램 매니페스트를 엽니다. 배포 매니페스트에는 .manifest 파일 이름 확장명이 있습니다.  
  
2. `group="framework"`센티널 어셈블리 ( `System.Core` ,, `WindowsBase` `Sentinel.v3.5Client` 및 `System.Data.Entity` )에 대 한 종속성 XML에를 추가 합니다. 예를 들어 XML은 다음과 같습니다.  
  
    ```  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" group="framework">  
    ```  
  
3. `<assemblyIdentity>`CommonLanguageRuntime에 대 한 요소의 버전 번호를 가장 낮은 공통 분모 인 .NET Framework의 버전 번호로 업데이트 합니다. 예를 들어 응용 프로그램이 .NET Framework 3.5를 대상으로 하는 경우 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 2.0.50727.0 버전 번호를 사용 하면 XML은 다음과 같이 표시 됩니다.  
  
    ```  
    <dependency>  
      <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
        <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50727.0" />  
      </dependentAssembly>  
    </dependency>  
    ```  
  
### <a name="to-update-and-re-sign-the-application-and-deployment-manifests"></a>응용 프로그램 및 배포 매니페스트를 업데이트 하 고 다시 서명 하려면  
  
- 응용 프로그램 및 배포 매니페스트를 업데이트 하 고 다시 서명 합니다. 자세한 내용은 [How to: Re-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)   
 [\<compatibleFrameworks> 요소인](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [\<dependency> 요소인](../deployment/dependency-element-clickonce-application.md)   
 [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)   
 [구성 파일 스키마](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)
