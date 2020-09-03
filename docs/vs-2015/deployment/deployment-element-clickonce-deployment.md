---
title: '&lt;deployment &gt; 요소 (ClickOnce 배포) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a55b5519d5abb7b40aeca23fed1bc2f8ea2cc33d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194651"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;deployment &gt; 요소 (ClickOnce 배포)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

업데이트를 배포하고 시스템에 노출하는 데 사용되는 특성을 식별합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 `deployment` 요소는 필수이며 `urn:schemas-microsoft-com:asm.v1` 네임스페이스에 있습니다. 요소에는 다음 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`install`|필수 요소. Windows **시작** 메뉴와 제어판의 **프로그램 추가/제거** 응용 프로그램에서이 응용 프로그램이 현재 상태를 정의 하는지 여부를 지정 합니다. 유효한 값은 `true` 및 `false`입니다. 인 `false` 경우 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 는 항상 네트워크에서이 응용 프로그램의 최신 버전을 실행 하며 요소를 인식 하지 못합니다 `subscription` .|  
|`minimumRequiredVersion`|선택 사항입니다. 클라이언트에서 실행할 수 있는이 응용 프로그램의 최소 버전을 지정 합니다. 응용 프로그램의 버전 번호가 배포 매니페스트에 제공 된 버전 번호 보다 적으면 응용 프로그램이 실행 되지 않습니다. 버전 번호는 형식으로 지정 해야 합니다 `N.N.N.N` . 여기서 `N` 는 부호 없는 정수입니다. 특성이 이면 `install` `false` 를 설정 하면 `minimumRequiredVersion` 안 됩니다.|  
|`mapFileExtensions`|선택 사항입니다. 기본값은 `false`입니다. 인 경우 `true` 배포의 모든 파일에 .deploy 확장명이 있어야 합니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 는이 확장을 웹 서버에서 다운로드 하는 즉시 이러한 파일에서 제거 합니다. 를 사용 하 여 응용 프로그램을 게시 하는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 이 확장이 모든 파일에 자동으로 추가 됩니다. 이 매개 변수를 사용 하면 배포 내의 모든 파일 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 을 .exe와 같은 "안전 하지 않은" 확장명으로 끝나는 파일의 전송을 차단 하는 웹 서버에서 다운로드할 수 있습니다.|  
|`disallowUrlActivation`|선택 사항입니다. 기본값은 `false`입니다. 인 경우 `true` url을 클릭 하거나 Internet Explorer에 url을 입력 하 여 설치 된 응용 프로그램이 시작 되지 않도록 합니다. 특성이 없으면 `install` 이 특성은 무시 됩니다.|  
|`trustURLParameters`|선택 사항입니다. 기본값은 `false`입니다. 인 경우 `true` 응용 프로그램에 전달 되는 쿼리 문자열 매개 변수를 URL에 포함할 수 있습니다. 명령줄 인수는 명령줄 응용 프로그램에 전달 됩니다. 자세한 내용은 [방법: 온라인 ClickOnce 응용 프로그램에서 쿼리 문자열 정보 검색](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)을 참조 하세요.<br /><br /> 특성이 이면 `disallowUrlActivation` `true` `trustUrlParameters` 매니페스트에서 제외 되거나 명시적으로로 설정 되어야 합니다 `false` .|  
  
 `deployment`요소에는 다음과 같은 자식 요소도 포함 되어 있습니다.  
  
## <a name="subscription"></a>subscription  
 선택 사항입니다. 요소를 포함 `update` 합니다. `subscription` 요소에는 특성이 없습니다. 요소가 없는 경우 `subscription` [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램은 업데이트를 검색 하지 않습니다. `install` `deployment` 요소의 특성이 인 경우 `false` `subscription` [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 네트워크에서 시작 되는 응용 프로그램은 항상 최신 버전을 사용 하기 때문에 요소는 무시 됩니다.  
  
## <a name="update"></a>update  
 필수 요소. 이 요소는 `subscription` 요소의 자식 이며 `beforeApplicationStartup` 또는 요소를 포함 `expiration` 합니다. `beforeApplicationStartup` 및 `expiration` 는 동일한 배포 매니페스트에 지정할 수 없습니다.  
  
 `update` 요소에는 특성이 없습니다.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 선택 사항입니다. 이 요소는 `update` 요소의 자식 이며 특성을 포함 하지 않습니다. 요소가 존재 하는 경우 `beforeApplicationStartup` [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 클라이언트가 온라인 상태 이면 업데이트를 확인할 때 응용 프로그램이 차단 됩니다. 이 요소가 없으면는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 먼저 요소에 대해 지정 된 값을 기준으로 업데이트를 검색 `expiration` 합니다. `beforeApplicationStartup` 및 `expiration` 는 동일한 배포 매니페스트에 지정할 수 없습니다.  
  
## <a name="expiration"></a>expiration  
 선택 사항입니다. 이 요소는 요소의 자식이 며 `update` 자식은 없습니다. `beforeApplicationStartup` 및 `expiration` 는 동일한 배포 매니페스트에 지정할 수 없습니다. 업데이트 확인이 발생 하 고 업데이트 된 버전이 검색 되 면 기존 버전이 실행 되는 동안 새 버전이 캐시 됩니다. 그런 다음 응용 프로그램을 다음에 시작할 때 새 버전이 설치 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 됩니다.  
  
 `expiration`요소는 다음 특성을 지원 합니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`maximumAge`|필수 요소. 응용 프로그램에서 업데이트 확인을 수행 하기 전에 현재 업데이트가 수행 되는 기간을 식별 합니다. 시간 단위는 특성에 따라 결정 됩니다 `unit` .|  
|`unit`|필수 요소. 의 시간 단위를 식별 `maximumAge` 합니다. 유효한 단위는 `hours` , `days` 및 `weeks` 입니다.|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 .NET Framework 2.0의 경우 배포 매니페스트에 섹션이 포함 된 경우이 요소가 필요 합니다 `subscription` . .NET Framework 3.5 이상에서이 요소는 선택 사항이 며 배포 매니페스트가 검색 된 서버 및 파일 경로로 기본 지정 됩니다.  
  
 이 요소는 `deployment` 요소의 자식이며 다음과 같은 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`codebase`|필수 요소. 응용 프로그램을 업데이트 하는 데 사용 되는 배포 매니페스트의 URI (Uniform Resource Identifier)로 위치를 식별 합니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . 이 요소를 사용 하면 CD 기반 설치를 위한 업데이트 위치를 전달할 수도 있습니다. 유효한 URI 여야 합니다.|  
  
## <a name="remarks"></a>설명  
 시작 시 업데이트를 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 검색 하거나, 시작 후 업데이트를 검색 하거나, 업데이트를 확인 하지 않도록 응용 프로그램을 구성할 수 있습니다. 시작 시 업데이트를 검색 하려면 요소가 요소 아래에 있는지 확인 `beforeApplicationStartup` `update` 합니다. 시작 후 업데이트를 검색 하려면 요소가 `expiration` 요소 아래에 있고 `update` 업데이트 간격이 제공 되는지 확인 합니다.  
  
 업데이트 확인을 사용 하지 않도록 설정 하려면 `subscription` 요소를 제거 합니다. 배포 매니페스트에서 업데이트를 검색 하지 않도록 지정 하는 경우에도 메서드를 사용 하 여 수동으로 업데이트를 확인할 수 있습니다 <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> .  
  
 DeploymentProvider가 업데이트와 연결 되는 방법에 대 한 자세한 내용은 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)을 참조 하세요.  
  
## <a name="examples"></a>예제  
 다음 코드 예제에서는 `deployment` 배포 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . 이 예제에서는 요소를 사용 하 여 `deploymentProvider` 기본 업데이트 위치를 지정 합니다.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>관련 항목  
 [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)
