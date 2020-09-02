---
title: '&lt;dependency &gt; 요소 (ClickOnce 응용 프로그램) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e79fadcab1a4f00c084d675c3267b5886772fe2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199875"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;dependency &gt; 요소 (ClickOnce 응용 프로그램)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

응용 프로그램에 필요한 플랫폼 또는 어셈블리 종속성을 식별 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <dependency>  
   <dependentOS  
      supportURL  
      description  
   >  
      <osVersionInfo>  
         <os  
            majorVersion  
            minorVersion  
            buildNumber  
            servicePackMajor  
            servicePackMinor  
            productType  
            suiteType  
         />   
      </osVersionInfo>  
   </dependentOS>  
   <dependentAssembly  
      dependencyType  
      allowDelayedBinding  
      group  
      codeBase  
      size  
   >  
      <assemblyIdentity  
         name  
         version  
         processorArchitecture  
         language  
      >  
         <hash>  
            <dsig:Transforms>  
               <dsig:Transform  
                  Algorithm  
            />  
            </dsig:Transforms>  
            <dsig:DigestMethod />  
            <dsig:DigestValue>  
            </dsig:DigestValue>  
    </hash>  
  
      </assemblyIdentity>  
   </dependentAssembly>  
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 `dependency`요소가 필요 합니다. 동일한 응용 프로그램 매니페스트에 인스턴스가 여러 개 있을 수 있습니다 `dependency` .  
  
 `dependency`요소는 특성이 없으며 다음과 같은 자식 요소를 포함 합니다.  
  
### <a name="dependentos"></a>dependentOS  
 선택 사항입니다. 요소를 포함 `osVersionInfo` 합니다. `dependentOS`및 `dependentAssembly` 요소는 함께 사용할 수 없습니다. 둘 중 하나는 요소에 대해 존재 해야 합니다 `dependency` .  
  
 `dependentOS` 는 다음 특성을 지원 합니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`supportUrl`|선택 사항입니다. 종속 플랫폼에 대 한 지원 URL을 지정 합니다. 이 URL은 필요한 플랫폼이 있는 경우 사용자에 게 표시 됩니다.|  
|`description`|선택 사항입니다. 요소에 설명 된 운영 체제를 사람이 읽을 수 있는 형식으로 설명 합니다 `dependentOS` .|  
  
### <a name="osversioninfo"></a>osVersionInfo  
 필수 요소. 이 요소는 `dependentOS` 요소의 자식이며 `os` 요소를 포함합니다. 이 요소에는 특성이 없습니다.  
  
### <a name="os"></a>os  
 필수 요소. 이 요소는 `osVersionInfo` 요소의 자식입니다. 이 요소에는 다음 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`majorVersion`|필수 요소. OS의 주 버전 번호를 지정 합니다.|  
|`minorVersion`|필수 요소. 운영 체제의 부 버전 번호를 지정 합니다.|  
|`buildNumber`|필수 요소. OS의 빌드 번호를 지정 합니다.|  
|`servicePackMajor`|필수 요소. OS의 Service Pack 주 번호를 지정 합니다.|  
|`servicePackMinor`|선택 사항입니다. OS의 Service Pack 부 번호를 지정 합니다.|  
|`productType`|선택 사항입니다. 제품 유형 값을 식별 합니다. 유효한 값은 `server`, `workstation` 및 `domainController`입니다. 예를 들어 Windows 2000 Professional의 경우이 특성 값은 `workstation` 입니다.|  
|`suiteType`|선택 사항입니다. 시스템에서 사용할 수 있는 제품군 또는 시스템의 구성 유형을 식별 합니다. 유효한 값은 `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` 및 `terminal`입니다. 예를 들어 Windows 2000 Professional의 경우이 특성 값은 `professional` 입니다.|  
  
### <a name="dependentassembly"></a>dependentAssembly  
 선택 사항입니다. 요소를 포함 `assemblyIdentity` 합니다. `dependentOS`및 `dependentAssembly` 요소는 함께 사용할 수 없습니다. 둘 중 하나는 요소에 대해 존재 해야 합니다 `dependency` .  
  
 `dependentAssembly` 에는 다음과 같은 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`dependencyType`|필수 요소. 종속성 유형을 지정 합니다. 유효한 값은 `preprequisite` 및 `install`입니다. `install`어셈블리는 응용 프로그램의 일부로 설치 됩니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . `prerequisite`어셈블리가 GAC (전역 어셈블리 캐시)에 있어야 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 설치할 수 있습니다.|  
|`allowDelayedBinding`|필수 요소. 런타임에 어셈블리를 프로그래밍 방식으로 로드할 수 있는지 여부를 지정 합니다.|  
|`group`|선택 사항입니다. `dependencyType`특성이로 설정 된 경우는 `install` 요청 시에만 설치 되는 어셈블리의 명명 된 그룹을 지정 합니다. 자세한 내용은 [연습: 디자이너를 사용하여 ClickOnce 배포 API에서 요청 시 어셈블리 다운로드](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)를 참조하세요.<br /><br /> 로 설정 `framework` `dependencyType` 되 고 특성이로 설정 된 경우는 `prerequisite` 어셈블리를 .NET Framework의 일부로 지정 합니다. 이상 버전에 설치 하는 경우이 어셈블리에 대해 GAC (global 빌드해야 cache)가 확인 되지 않습니다 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] .|  
|`codeBase`|`dependencyType`특성이로 설정 된 경우 필수 사항 `install` 입니다. 종속 어셈블리의 경로입니다. 는 절대 경로 이거나 매니페스트의 코드 베이스에 상대적인 경로일 수 있습니다. 어셈블리 매니페스트가 유효 하려면이 경로는 유효한 URI 여야 합니다.|  
|`size`|`dependencyType`특성이로 설정 된 경우 필수 사항 `install` 입니다. 종속 어셈블리의 크기 (바이트)입니다.|  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 필수 요소. 이 요소는 `dependentAssembly` 요소의 자식이며 다음과 같은 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`name`|필수 요소. 응용 프로그램의 이름을 식별 합니다.|  
|`version`|필수 요소. 응용 프로그램의 버전 번호를 다음 형식으로 지정 합니다. `major.minor.build.revision`|  
|`publicKeyToken`|선택 사항입니다. `SHA-1`응용 프로그램 또는 어셈블리가 서명 되는 공개 키의 해시 값에 대 한 마지막 8 바이트를 나타내는 16 자 16 진수 문자열을 지정 합니다. 카탈로그에 서명 하는 데 사용 되는 공개 키는 2048 비트 이상 이어야 합니다.|  
|`processorArchitecture`|선택 사항입니다. 프로세서를 지정 합니다. 유효한 값은 `x86` 32 비트 windows 및 64 비트 windows에 대 한 것 `I64` 입니다.|  
|`language`|선택 사항입니다. EN-US와 같이 어셈블리의 두 부분으로 구성 된 언어 코드를 식별 합니다.|  
  
### <a name="hash"></a>hash  
 요소는 `hash` 요소의 선택적 자식 요소입니다 `assemblyIdentity` . `hash` 요소에는 특성이 없습니다.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램의 모든 파일에 대 한 알고리즘 해시를 보안 검사로 사용 하 여 배포 후 파일이 변경 되지 않도록 합니다. `hash`요소가 포함 되지 않은 경우에는이 검사가 수행 되지 않습니다. 따라서 요소를 생략 하는 `hash` 것은 권장 되지 않습니다.  
  
### <a name="dsigtransforms"></a>dsig:Transforms  
 요소는 `dsig:Transforms` 요소의 필수 자식 요소입니다 `hash` . `dsig:Transforms` 요소에는 특성이 없습니다.  
  
### <a name="dsigtransform"></a>dsig:Transform  
 요소는 `dsig:Transform` 요소의 필수 자식 요소입니다 `dsig:Transforms` . `dsig:Transform` 요소에는 다음 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`Algorithm`|이 파일의 다이제스트를 계산 하는 데 사용 되는 알고리즘입니다. 현재에서 사용 되는 유일한 값은 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `urn:schemas-microsoft-com:HashTransforms.Identity` 입니다.|  
  
### <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 요소는 `dsig:DigestMethod` 요소의 필수 자식 요소입니다 `hash` . `dsig:DigestMethod` 요소에는 다음 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`Algorithm`|이 파일의 다이제스트를 계산 하는 데 사용 되는 알고리즘입니다. 현재에서 사용 되는 유일한 값은 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] `http://www.w3.org/2000/09/xmldsig#sha1` 입니다.|  
  
### <a name="dsigdigestvalue"></a>dsig:DigestValue  
 요소는 `dsig:DigestValue` 요소의 필수 자식 요소입니다 `hash` . `dsig:DigestValue` 요소에는 특성이 없습니다. 해당 텍스트 값은 지정 된 파일에 대해 계산 된 해시입니다.  
  
## <a name="remarks"></a>설명  
 응용 프로그램에서 사용 하는 모든 어셈블리에는 해당 요소가 있어야 합니다 `dependency` . 종속 어셈블리는 전역 어셈블리 캐시에 플랫폼 어셈블리로 미리 설치 해야 하는 어셈블리를 포함 하지 않습니다.  
  
## <a name="example"></a>예  
 다음 코드 예제에서는 `dependency` 응용 프로그램 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . 이 코드 예제는 [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md) 항목에 대해 제공 되는 더 큰 예제의 일부입니다.  
  
```  
<dependency>  
  <dependentOS>  
    <osVersionInfo>  
      <os   
        majorVersion="4"   
        minorVersion="10"   
        buildNumber="0"   
        servicePackMajor="0" />  
    </osVersionInfo>  
  </dependentOS>  
</dependency>  
<dependency>  
  <dependentAssembly  
    dependencyType="preRequisite"  
    allowDelayedBinding="true">  
    <assemblyIdentity  
      name="Microsoft.Windows.CommonLanguageRuntime"  
      version="4.0.20506.0" />  
  </dependentAssembly>  
</dependency>  
  
<dependency>  
  <dependentAssembly  
    dependencyType="install"  
    allowDelayedBinding="true"  
    codebase="MyApplication.exe"  
    size="4096">  
    <assemblyIdentity  
      name="MyApplication"  
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="see-also"></a>관련 항목  
 [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)   
 [\<dependency> 요소](../deployment/dependency-element-clickonce-deployment.md)
