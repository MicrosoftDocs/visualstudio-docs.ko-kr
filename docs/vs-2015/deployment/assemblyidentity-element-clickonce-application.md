---
title: '&lt;assemblyIdentity &gt; 요소 (ClickOnce 응용 프로그램) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bde22809af69071f5484e25717a5aea7d78a603
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428536"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;assemblyIdentity &gt; 요소 (ClickOnce 응용 프로그램)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

배포에 배포 된 응용 프로그램을 식별 합니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assemblyIdentity   
   name  
   version  
   publicKeyToken  
   processorArchitecture  
   language  
/>  
```  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 `assemblyIdentity`요소가 필요 합니다. 자식 요소를 포함 하지 않으며 다음과 같은 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`Name`|필수 요소. 응용 프로그램의 이름을 식별 합니다.<br /><br /> `Name`에 작은따옴표 또는 큰따옴표와 같은 특수 문자가 포함 되어 있으면 응용 프로그램을 활성화 하지 못할 수 있습니다.|  
|`Version`|필수 요소. 응용 프로그램의 버전 번호를 다음 형식으로 지정 합니다. `major.minor.build.revision`|  
|`publicKeyToken`|선택 사항입니다. `SHA-1`응용 프로그램 또는 어셈블리가 서명 되는 공개 키의 해시 값에 대 한 마지막 8 바이트를 나타내는 16 자 16 진수 문자열을 지정 합니다. 카탈로그에 서명 하는 데 사용 되는 공개 키는 2048 비트 이상 이어야 합니다.<br /><br /> 어셈블리에 서명 하는 것이 좋지만 선택적 이지만이 특성이 필요 합니다. 어셈블리가 서명 되지 않은 경우에는 자체 서명 된 어셈블리에서 값을 복사 하거나 모든 0의 "더미" 값을 사용 해야 합니다.|  
|`processorArchitecture`|필수 요소. 프로세서를 지정 합니다. 유효한 값은 `msil` 모든 프로세서, `x86` 32 비트 windows, `IA64` 64 비트 windows 및 `Itanium` Intel 64 비트 Itanium 프로세서에 대 한 것입니다.|  
|`language`|필수 요소. 어셈블리의 두 부분 언어 코드 (예:)를 식별 합니다 `en-US` . 이 요소는 `asmv2` 네임 스페이스에 있습니다. 지정 하지 않으면 기본값은 `neutral` 입니다.|  
  
## <a name="examples"></a>예제  
  
### <a name="description"></a>Description  
 다음 코드 예제에서는 `assemblyIdentity` 응용 프로그램 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . 이 코드 예제는 [ClickOnce 응용 프로그램 매니페스트에](../deployment/clickonce-application-manifest.md)제공 된 더 큰 예제의 일부입니다.  
  
### <a name="code"></a>코드  
  
```  
<asmv1:assemblyIdentity   
  name="My Application Deployment.exe"   
  version="1.0.0.0"   
  publicKeyToken="43cb1e8e7a352766"   
  language="neutral"   
  processorArchitecture="x86"   
  type="win32" />  
```  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)   
 [\<assemblyIdentity> 요소](../deployment/assemblyidentity-element-clickonce-deployment.md)
