---
title: ClickOnce 및 Authenticode | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8f7fd108250a406339d5be08b5a6e9aaf67d039
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917560"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce 및 Authenticode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Authenticode *는 업계 표준 암호화를 사용 하 여 응용 프로그램 게시자의 신뢰성을 확인 하는 디지털 인증서로 응용 프로그램 코드에 서명 하는 Microsoft 기술입니다. 애플리케이션 배포에 Authenticode를 사용하여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 는 트로이 목마의 위험을 줄입니다. 트로이 목마는 악의적인 제3자가 신뢰할 수 있는 기존의 소스에서 온 적법한 프로그램처럼 속여 표시하는 바이러스 또는 기타 유해 프로그램입니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포에 디지털 인증서로 서명하는 것은 어셈블리와 파일이 손상되지 않았음을 확인하기 위한 선택적인 단계입니다.  
  
 다음 섹션에서는 Authenticode에 사용되는 서로 다른 유형의 디지털 인증서, CA(인증 기관)를 사용하여 인증서를 검증하는 방법, 인증서에서 타임스탬프의 역할, 인증서에 사용할 수 있는 스토리지의 메서드에 대해 설명합니다.  
  
## <a name="authenticode-and-code-signing"></a>Authenticode 및 코드 서명  
 *디지털 인증서* 란 인증서가 발급된 게시자 및 인증서를 발급한 기관에 대해 설명하는 메타데이터와 함께 퍼블릭/퍼블릭 암호화 키 쌍을 포함하는 파일입니다.  
  
 다양한 유형의 Authenticode 인증서가 있습니다. 각 인증서는 서로 다른 서명 유형에 맞게 구성되어 있습니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션의 경우 코드 서명을 위한 유효한 Authenticode 인증서가 반드시 필요합니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션에 다른 유형의 인증서(예: 디지털 전자 메일 인증서)로 서명하려고 시도하면 작동하지 않습니다. 자세한 내용은 [코드 서명 소개](https://msdn.microsoft.com/library/ms537361.aspx)를 참조하세요.  
  
 세 가지 방법 중 하나로 코드 서명을 위한 인증서를 가져올 수 있습니다.  
  
- 인증서 공급업체에서 인증서를 구매합니다.  
  
- 디지털 인증서를 만드는 조직의 담당 그룹에서 인증서를 받습니다.  
  
- [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]에 포함된 MakeCert.exe로 자체 인증서를 생성합니다.  
  
### <a name="how-using-certificate-authorities-helps-users"></a>인증 기관 사용이 사용자에게 도움이 되는 방법  
 MakeCert.exe 유틸리티를 사용 하 여 생성 된 인증서를 일반적으로 *자체 인증서* 또는 *테스트 인증서*라고 합니다. 이러한 종류의 인증서는 .NET Framework에서 .snk 파일이 작동 하는 것과 거의 동일한 방식으로 작동 합니다. 퍼블릭/퍼블릭 암호화 키 쌍으로만 구성되어 있으며 게시자에 대한 확인 가능한 정보가 포함되어 있지 않습니다. 신뢰 수준이 높은 인트라넷에서 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션을 배포하는 경우 자체 서명 인증서를 사용할 수 있습니다. 그러나 이러한 애플리케이션을 클라이언트 컴퓨터에서 실행하면 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 는 이를 알 수 없는 게시자에서 온 것으로 식별합니다. 기본적으로 자체 인증서로 서명되고 인터넷을 통해 배포된 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션은 신뢰할 수 있는 애플리케이션 배포를 사용할 수 없습니다.  
  
 반면, 인증서 공급업체와 같은 CA 또는 기업 내 부서로부터 인증서를 받아 사용하면 사용자에게 더 나은 보안을 제공할 수 있습니다. 이러한 인증서는 서명된 소프트웨어의 게시자를 식별하는 것은 물론 서명한 CA를 통해 해당 ID의 유효성을 확인합니다. CA가 루트 인증 기관이 아닌 경우 Authenticode는 루트 인증 기관에 다시 "연결"하여, 해당 CA가 인증서를 발급할 권한이 있는 곳인지를 확인합니다. 보안을 강화하려면 가능한 경우에는 언제든 CA에서 발급한 인증서를 사용해야 합니다.  
  
 자체 인증서를 생성 하는 방법에 대 한 자세한 내용은 [Makecert.exe (인증서 생성 도구)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)를 참조 하세요.  
  
### <a name="timestamps"></a>타임스탬프  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션 서명에 사용된 인증서는 특정 기간(대개 12개월) 이후 만료됩니다. 계속해서 새 인증서로 애플리케이션에 다시 서명해야 하는 불편을 없애기 위해 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 는 타임스탬프를 지원합니다. 애플리케이션을 타임스탬프로 서명하면, 타임스탬프가 유효한 경우 해당 인증서는 심지어 만료 이후에도 계속 허용됩니다. 따라서 인증서는 만료되었지만 타임스탬프는 유효한 경우 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션을 다운로드하여 실행할 수 있습니다. 또한 만료된 인증서가 있는 설치된 애플리케이션이 계속해서 업데이트를 다운로드하고 설치할 수 있습니다.  
  
 애플리케이션 서버에 타임스탬프를 포함하려면 타임스탬프 서버를 사용할 수 있어야 합니다. 타임스탬프 서버를 선택하는 방법에 대한 자세한 내용은 [How to: Sign Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md)를 참조하세요.  
  
### <a name="updating-expired-certificates"></a>만료된 인증서 업데이트  
 .NET Framework의 이전 버전에서 인증서가 만료된 애플리케이션을 업데이트하면 해당 애플리케이션의 작동이 중지될 수 있습니다. 이 문제를 해결하려면 다음 방법 중 하나를 사용합니다.  
  
- .NET Framework를 Windows XP에서는 버전 2.0 SP1 이상으로, Windows Vista에서 버전 3.5 이상으로 업데이트합니다.  
  
- 애플리케이션을 제거하고 유효한 인증서로 새 버전을 다시 설치합니다.  
  
- 인증서를 업데이트하는 명령줄 어셈블리를 만듭니다.  
  
### <a name="storing-certificates"></a>인증서 저장  
  
- 인증서를 .pfx 파일로 파일 시스템에 저장하거나 키 컨테이너 내부에 저장할 수 있습니다. Windows 도메인의 사용자는 여러 키 컨테이너를 가질 수 있습니다. 사용자가 .pfx에 저장해야 한다고 지정하지 않는 한, 기본적으로 MakeCert.exe는 인증서를 개인 키 컨테이너에 저장합니다. [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] 배포를 만들기 위한 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 도구인 Mage.exe 및 MageUI.exe에서는 어떤 방식으로 저장된 인증서든 사용할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)   
 [신뢰할 수 있는 응용 프로그램 배포 개요](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe(매니페스트 생성 및 편집 도구)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
