---
title: '방법: ClickOnce 배포에서 개별 필수 조건에 대 한 지원 URL 지정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1907b619bcc616c73d9b9e37af30722c02bf100e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679964"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>방법: ClickOnce 배포 시 개별 필수 구성 요소에 대한 지원 URL 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]배포는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 실행 하기 위해 클라이언트 컴퓨터에서 사용할 수 있어야 하는 여러 필수 구성 요소를 테스트할 수 있습니다. 여기에는 필수 최소 버전의 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , 운영 체제 버전, GAC (전역 어셈블리 캐시)에 사전 설치 해야 하는 모든 어셈블리가 포함 됩니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]그러나는 이러한 필수 구성 요소를 설치할 수 없습니다. 필수 구성 요소가 없는 경우 설치를 중단 하 고 설치에 실패 한 이유를 설명 하는 대화 상자를 표시 합니다.  
  
 필수 구성 요소를 설치 하는 방법에는 두 가지가 있습니다. 부트스트래퍼 응용 프로그램을 사용 하 여 설치할 수 있습니다. 또는 필수 구성 요소를 찾을 수 없는 경우 대화 상자에서 사용자에 게 표시 되는 개별 필수 구성 요소에 대 한 지원 URL을 지정할 수 있습니다. 해당 URL에서 참조 하는 페이지에는 필수 구성 요소를 설치 하는 지침에 대 한 링크가 포함 될 수 있습니다. 응용 프로그램에서 개별 필수 구성 요소에 대 한 지원 URL을 지정 하지 않은 경우에는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램의 배포 매니페스트에 지정 된 지원 url이 정의 된 경우 해당 url을 전체로 표시 합니다.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Mage.exe 및 MageUI.exe 모두 배포를 생성 하는 데 사용할 수 있지만 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 이러한 도구는 개별 필수 구성 요소에 대 한 지원 URL 지정을 직접 지원 하지 않습니다. 이 문서에서는 이러한 지원 Url을 포함 하도록 배포의 응용 프로그램 매니페스트 및 배포 매니페스트를 수정 하는 방법을 설명 합니다.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>개별 필수 구성 요소에 대 한 지원 URL 지정  
  
1. 텍스트 편집기에서 응용 프로그램의 응용 프로그램 매니페스트 (.manifest 파일)를 엽니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
2. 운영 체제 필수 구성 요소에 대해 `supportUrl` 특성을 요소에 추가 합니다 `dependentOS` .  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3. 특정 버전의 공용 언어 런타임에 대 한 필수 구성 요소에 대해 `supportUrl` `dependentAssembly` 공용 언어 런타임 종속성을 지정 하는 항목에 특성을 추가 합니다.  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4. 전역 어셈블리 캐시에 사전 설치 해야 하는 어셈블리에 대 한 필수 구성 요소는 `supportUrl` `dependentAssembly` 필요한 어셈블리를 지정 하는 요소에 대해를 설정 합니다.  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5. 선택 사항입니다. .NET Framework 4를 대상으로 하는 응용 프로그램의 경우 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 텍스트 편집기에서 응용 프로그램에 대 한 배포 매니페스트 (응용 프로그램 파일)를 엽니다.  
  
6. .NET Framework 4 필수 구성 요소에 대해 `supportUrl` 특성을 요소에 추가 합니다 `compatibleFrameworks` .  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7. 응용 프로그램 매니페스트를 수동으로 변경한 후에는 디지털 인증서를 사용 하 여 응용 프로그램 매니페스트에 다시 서명 하 고 배포 매니페스트도 업데이트 한 후 다시 서명 해야 합니다. 을 사용 하 여 이러한 파일을 다시 생성 하면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 수동 변경 내용이 지워지므로 Mage.exe 또는 MageUI.exe SDK 도구를 사용 하 여이 작업을 수행 해야 합니다. Mage.exe를 사용 하 여 매니페스트를 다시 서명 하는 방법에 대 한 자세한 내용은 [방법: 응용 프로그램 및 배포 매니페스트 다시 서명](../deployment/how-to-re-sign-application-and-deployment-manifests.md)을 참조 하세요.  
  
## <a name="net-framework-security"></a>.NET Framework 보안  
 응용 프로그램이 부분 신뢰로 실행 되도록 표시 된 경우 지원 URL은 대화 상자에 표시 되지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Mage.exe (매니페스트 생성 및 편집 도구)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks> 요소인](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce 및 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [응용 프로그램 배포 필수 구성 요소](../deployment/application-deployment-prerequisites.md)
