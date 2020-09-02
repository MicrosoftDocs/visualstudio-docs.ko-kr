---
title: ClickOnce 배포 매니페스트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a5d1fe2191dadd0972dcde6f38b9697e29f05ab8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190468"
---
# <a name="clickonce-deployment-manifest"></a>ClickOnce 배포 매니페스트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

배포 매니페스트는 배포할 현재 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션 버전의 ID를 포함하여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포를 설명하는 XML 파일입니다.  
  
 배포 매니페스트에는 다음 요소와 특성이 있습니다.  
  
|요소|설명|특성|  
|-------------|-----------------|----------------|  
|[\<assembly> 요소](../deployment/assembly-element-clickonce-deployment.md)|필수 요소. 최상위 요소입니다.|`manifestVersion`|  
|[\<assemblyIdentity> 요소](../deployment/assemblyidentity-element-clickonce-deployment.md)|필수 요소. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션에 대한 애플리케이션 매니페스트를 식별합니다.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture`|  
|[\<description> 요소](../deployment/description-element-clickonce-deployment.md)|필수 요소. 제어판에서 셸 존재 및 **프로그램 추가/제거** 항목을 만드는 데 사용되는 애플리케이션 정보를 식별합니다.|`publisher`<br /><br /> `product`<br /><br /> `supportUrl`|  
|[\<deployment> 요소](../deployment/deployment-element-clickonce-deployment.md)|선택 사항입니다. 업데이트를 배포하고 시스템에 노출하는 데 사용되는 특성을 식별합니다.|`install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters`|  
|[\<compatibleFrameworks> 요소](../deployment/compatibleframeworks-element-clickonce-deployment.md)|필수 요소. 이 애플리케이션이 설치 및 실행할 수 있는 .NET Framework의 버전을 식별합니다.|`SupportUrl`|  
|[\<dependency> 요소](../deployment/dependency-element-clickonce-deployment.md)|필수 요소. 배포를 위해 설치할 애플리케이션 버전 및 애플리케이션 매니페스트 위치를 식별합니다.|`preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size`|  
|[\<publisherIdentity> 요소](../deployment/publisheridentity-element-clickonce-deployment.md)|서명된 매니페스트에 필요합니다. 이 배포 매니페스트에 서명한 게시자에 대한 정보를 포함합니다.|`Name`<br /><br /> `issuerKeyHash`|  
|[\<Signature> 요소](../deployment/signature-element-clickonce-deployment.md)|선택 사항입니다. 이 배포 매니페스트에 디지털 방식으로 서명하는 데 필요한 정보를 포함합니다.|없음|  
|[\<customErrorReporting> 요소](../deployment/customerrorreporting-element-clickonce-deployment.md)|선택 사항입니다. 오류가 발생할 때 표시할 URI를 지정합니다.|URI|  
  
## <a name="remarks"></a>설명  
 배포 매니페스트 파일은 현재 버전 및 기타 배포 설정을 포함하여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션 배포를 식별합니다. 이 파일은 애플리케이션의 현재 버전 및 배포에 포함된 모든 파일을 설명하는 애플리케이션 매니페스트를 참조합니다.  
  
 자세한 내용은 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)을 참조하세요.  
  
## <a name="file-location"></a>파일 위치  
 배포 매니페스트 파일은 현재 애플리케이션 버전에 대한 올바른 애플리케이션 매니페스트를 참조합니다. 애플리케이션 배포의 새 버전을 사용 가능하게 설정할 때 새 애플리케이션 매니페스트를 참조하려면 배포 매니페스트를 업데이트해야 합니다.  
  
 배포 매니페스트 파일은 강력한 이름으로 지정되어야 하며, 게시자 유효성 검사를 위한 인증서도 포함할 수 있습니다.  
  
## <a name="file-name-syntax"></a>파일 이름 구문  
 배포 매니페스트 파일의 이름은 .application 확장명으로 끝나야 합니다.  
  
## <a name="examples"></a>예제  
 다음 코드 예제에서는 배포 매니페스트를 보여 줍니다.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <assemblyIdentity   
    name="My Application Deployment.app"  
    version="1.0.0.0"  
    publicKeyToken="43cb1e8e7a352766"  
    language="neutral"  
    processorArchitecture="x86"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description  
    asmv2:publisher="My Company Name"  
    asmv2:product="My Application"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="0" unit="days" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />  
  </deployment>  
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />  
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />  
  </compatibleFrameworks>  
  <dependency>  
    <dependentAssembly  
      dependencyType="install"  
      codebase="1.0.0.0\My Application Deployment.exe.manifest"  
      size="6756">  
      <assemblyIdentity  
        name="My Application Deployment.exe"  
        version="1.0.0.0"  
        publicKeyToken="43cb1e8e7a352766"  
        language="neutral"  
        processorArchitecture="x86"  
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
…  
</Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>관련 항목  
 [ClickOnce 애플리케이션 게시](../deployment/publishing-clickonce-applications.md)
