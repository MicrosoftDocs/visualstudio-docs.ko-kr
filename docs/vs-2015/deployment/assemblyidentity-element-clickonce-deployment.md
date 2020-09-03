---
title: '&lt;assemblyIdentity &gt; 요소 (ClickOnce 배포) | Microsoft Docs'
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
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bfc2ff97a2eb465fe7306ebe368a20e2a7fd8638
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155721"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;assemblyIdentity &gt; 요소 (ClickOnce 배포)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

응용 프로그램의 주 어셈블리를 식별 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      <assemblyIdentity    
   name   
   version  
   publicKeyToken  
   processorArchitecture  
    type  
/>  
```  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 `assemblyIdentity`요소가 필요 합니다. 자식 요소를 포함 하지 않으며 다음과 같은 특성이 있습니다.  
  
|특성|설명|  
|---------------|-----------------|  
|`name`|필수 요소. 정보를 제공 하기 위해 사용자가 읽을 수 있는 배포 이름을 식별 합니다.<br /><br /> `name`에 작은따옴표 또는 큰따옴표와 같은 특수 문자가 포함 되어 있으면 응용 프로그램을 활성화 하지 못할 수 있습니다.|  
|`version`|필수 요소. 어셈블리의 버전 번호를 다음과 같은 형식으로 지정 `major.minor.build.revision` 합니다.<br /><br /> 응용 프로그램 업데이트를 트리거하기 위해 업데이트 된 매니페스트에서이 값을 증가 시켜야 합니다.|  
|`publicKeyToken`|필수 요소. 배포 매니페스트가 서명 된 공개 키에 대 한 SHA-1 해시 값의 마지막 8 바이트를 나타내는 16 자 16 진수 문자열을 지정 합니다. 서명 하는 데 사용 되는 공개 키는 2048 비트 이상 이어야 합니다.<br /><br /> 어셈블리에 서명 하는 것이 좋지만 선택적 이지만이 특성이 필요 합니다. 어셈블리가 서명 되지 않은 경우에는 자체 서명 된 어셈블리에서 값을 복사 하거나 모든 0의 "더미" 값을 사용 해야 합니다.|  
|`processorArchitecture`|필수 요소. 프로세서를 지정 합니다. 유효한 값은 `msil` 모든 프로세서, `x86` 32 비트 windows, `IA64` 64 비트 windows 및 `Itanium` Intel 64 비트 Itanium 프로세서에 대 한 것입니다.|  
|`type`|필수 요소. Windows side-by-side 설치 기술과의 호환성을 위한 것입니다. 유일 하 게 허용 되는 값은 `win32` 입니다.|  
  
## <a name="remarks"></a>설명  
  
## <a name="example"></a>예  
 다음 코드 예제에서는 `assemblyIdentity` 배포 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . 이 코드 예제는 [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md) 항목에 대해 제공 되는 더 큰 예제의 일부입니다.  
  
```  
<!-- Identify the deployment. -->  
<assemblyIdentity   
  name="My Application Deployment.app"  
  version="1.0.0.0"  
  publicKeyToken="43cb1e8e7a352766"  
  language="neutral"  
  processorArchitecture="x86"  
  xmlns="urn:schemas-microsoft-com:asm.v1" />  
```  
  
## <a name="see-also"></a>관련 항목  
 [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)   
 [\<assemblyIdentity> 요소](../deployment/assemblyidentity-element-clickonce-application.md)
