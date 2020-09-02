---
title: 신뢰할 수 있는 응용 프로그램 배포 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- ClickOnce deployment, security
- trusted application deployment
ms.assetid: b24a1702-8fbe-45b1-87a0-9618a0708f1d
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 673cc3d9b936131e6423a015af5c78486846fbe7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847713"
---
# <a name="trusted-application-deployment-overview"></a>Trusted Application Deployment Overview
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 신뢰할 수 있는 애플리케이션 배포 기술을 사용하여, 관리자 권한이 있는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션을 배포하는 방법에 대한 개요를 제공합니다.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 기술에 포함된 신뢰할 수 있는 배포를 사용하면 규모에 관계없이 모든 조직이 사용자에게 메시지를 표시하지 않고 더 안전하고 더 보호된 방식으로 관리되는 애플리케이션에 대한 추가적인 권한을 더 쉽게 부여할 수 있습니다. 신뢰할 수 있는 애플리케이션 배포를 통해 조직은 Authenticode 인증서를 사용하여 식별된 신뢰할 수 있는 게시자 목록이 클라이언트 컴퓨터에 포함되도록 구성할 수 있습니다. 따라서 이들 신뢰할 수 있는 게시자의 하나가 서명한 모든 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션은 더 높은 수준의 신뢰를 받습니다.  
  
> [!NOTE]
> 신뢰할 수 있는 애플리케이션 배포에는 사용자 컴퓨터에 대한 일회성 구성이 필요합니다. 관리되는 데스크톱 환경에서는 전역 정책을 사용하여 이 구성을 수행할 수 있습니다. 애플리케이션에 대해 이 구성을 수행하지 않으려면 권한 상승을 사용하세요. 자세한 내용은 [ClickOnce 애플리케이션 게시](../deployment/securing-clickonce-applications.md)를 참조하세요.  
  
## <a name="trusted-application-deployment-basics"></a>신뢰할 수 있는 애플리케이션 배포 기본 사항  
 다음 표에서는 신뢰할 수 있는 애플리케이션 배포에 포함된 개체 및 역할을 보여 줍니다.  
  
|개체 또는 역할|설명|  
|--------------------|-----------------|  
|관리자 역할|클라이언트 컴퓨터를 업데이트 및 유지 관리하는 조직 엔터티입니다.|  
|신뢰 관리자|클라이언트 애플리케이션 보안을 적용하는 CLR(공용 언어 런타임) 내의 하위 시스템입니다.|  
|게시자|애플리케이션을 쓰고 유지 관리하는 엔터티입니다.|  
|배포자|애플리케이션 패키지하고 사용자에게 배포하는 엔터티입니다.|  
|인증서(certificate)|public 및 private 키로 구성된 암호화 서명으로, 일반적으로 신뢰성을 보장할 수 있는 CA(인증 기관)에서 발급됩니다.|  
|Authenticode 인증서|무엇보다 인증서를 채택할 수 있는 용도에 대해 설명하는 포함된 메타데이터가 있는 인증서입니다.|  
|인증 기관|게시자 ID를 확인하고 게시자에게 게시자 메타데이터와 함께 포함된 인증서를 발급하는 조직입니다.|  
|루트 기관|인증서를 발급하는 다른 인증 기관을 인증하는 인증 기관입니다.|  
|키 컨테이너|인증서를 저장하기 위한 Microsoft Windows의 논리적 스토리지 공간입니다.|  
|신뢰할 수 있는 게시자|Authenticode 인증서가 클라이언트 컴퓨터의 CTL(인증서 신뢰 목록)에 추가된 게시자입니다.|  
  
 더 큰 조직에서는 게시자와 배포자가 두 개의 개별 엔터티인 경우가 많습니다.  
  
- 게시자는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션을 만드는 그룹입니다.  
  
- 배포자는 일반적으로 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션을 회사의 엔터프라이즈 데스크톱 컴퓨터에 배포하는 IT(정보 기술) 부서인 그룹입니다.  
  
  신뢰할 수 있는 애플리케이션 배포를 활용하려면 다음 단계에 따라야 합니다.  
  
1. 게시자에 대한 인증서를 가져옵니다.  
  
2. 모든 클라이언트의 신뢰할 수 있는 게시자 저장소에 게시자를 추가합니다.  
  
3. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션을 만듭니다.  
  
4. 게시자의 인증서를 사용하여 배포 매니페스트에 서명합니다.  
  
5. 클라이언트 컴퓨터에 애플리케이션 배포를 게시합니다.  
  
### <a name="obtain-a-certificate-for-the-publisher"></a>게시자에 대한 인증서 가져오기  
 디지털 인증서는 Microsoft Authenticode 인증 및 보안 시스템의 핵심 구성 요소입니다. Authenticode는 Windows 운영 체제의 표준 파트입니다. 모든 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션은 신뢰할 수 있는 애플리케이션 배포에 참여하는지와 관계없이 디지털 인증서로 서명되어야 합니다. 에서 Authenticode가 작동 하는 방식에 대 한 자세한 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 내용은 [ClickOnce 및 Authenticode](../deployment/clickonce-and-authenticode.md)를 참조 하세요.  
  
### <a name="add-the-publisher-to-the-trusted-publishers-store"></a>신뢰할 수 있는 배포자 저장소에 게시자 추가  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션이 더 높은 수준의 신뢰를 받게 하려면 신뢰할 수 있는 게시자로 인증서를 각 클라이언트 애플리케이션이 실행될 컴퓨터에 추가해야 합니다. 이 작업을 수행하는 것은 일회성 구성입니다. 작업이 완료되면 게시자 인증서로 서명된 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션을 원하는 만큼 배포할 수 있고 애플리케이션은 모두 높은 신뢰를 기반으로 실행됩니다.  
  
 Windows 운영 체제를 실행하는 회사 인트라넷과 같은 관리되는 데스크톱 환경에 애플리케이션을 배포하면 그룹 정책을 통해 새 CTL(인증서 신뢰 목록)을 만들어서 클라이언트 저장소에 신뢰할 수 있는 게시자를 추가할 수 있습니다. 자세한 내용은 [그룹 정책 개체의 인증서 신뢰 목록 만들기](https://technet.microsoft.com/library/2c03582f-00b2-43e5-ae1d-493894ad0fd7)를 참조하세요.  
  
 애플리케이션을 관리되는 데스크톱 환경에 배포하지 않으면 다음 옵션을 사용하여 신뢰할 수 있는 게시자 저장소에 인증서를 추가할 수 있습니다.  
  
- <xref:System.Security.Cryptography?displayProperty=fullName> 네임스페이스.  
  
- CertMgr.exe - Internet Explorer의 구성 요소이므로 Windows 98 및 모든 이후 버전에 있습니다. 자세한 내용은 [Certmgr.exe (인증서 관리자 도구)](https://msdn.microsoft.com/library/7e953b43-1374-4bbc-814f-53ca1b6b52bb)를 참조 하세요.  
  
### <a name="create-a-clickonce-application"></a>ClickOnce 애플리케이션 만들기  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션은 애플리케이션을 설명하고 설치 매개 변수를 제공하는 매니페스트 파일과 결합된 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 클라이언트 애플리케이션입니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 에서 **게시** 명령을 사용하여 프로그램을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]애플리케이션으로 전환할 수 있습니다. 또는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 에 포함된 도구를 사용하여 [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]배포에 필요한 모든 파일을 생성할 수 있습니다. 자세한 단계 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 참조 [연습: 수동으로 ClickOnce 애플리케이션 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
 신뢰할 수 있는 애플리케이션 배포는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]에 관련되고 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션에서만 사용할 수 있습니다.  
  
### <a name="sign-the-deployment"></a>배포에 서명  
 인증서를 가져오고 나서 이 인증서를 사용하여 배포에 서명해야 합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 게시 마법사를 사용하여 애플리케이션을 배포할 경우 인증서를 직접 지정하지 않았다면 마법사가 자동으로 테스트 인증서를 생성합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트 디자이너 창을 사용하여 CA가 제공한 인증서를 제공할 수도 있습니다.  [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](https://msdn.microsoft.com/library/31kztyey\(v=vs.110\)) 또는 [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](https://msdn.microsoft.com/library/31kztyey\(v=vs.110\))를 참조하세요.  
  
> [!CAUTION]
> 테스트 인증서를 사용하여 애플리케이션을 배포하는 것은 권장하지 않습니다.  
  
 Mage.exe 또는 MageUI.exe SDK 도구를 사용하여 애플리케이션에 서명할 수도 있습니다. 자세한 내용은 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)를 참조 하세요. 배포 서명과 관련 된 명령줄 옵션의 전체 목록은 [Mage.exe (매니페스트 생성 및 편집 도구)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)를 참조 하세요.  
  
### <a name="publish-the-application"></a>애플리케이션 게시  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 매니페스트에 서명하면 바로 애플리케이션을 설치 위치에 게시할 준비가 됩니다. 설치 위치는 웹 서버, 파일 공유 또는 로컬 디스크일 수 있습니다. 클라이언트가 배포 매니페스트에 처음 액세스하면 신뢰 관리자는 설치된 신뢰할 수 있는 게시자가 더 높은 수준의 신뢰로 실행하도록 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션에 권한이 부여되었는지 여부를 선택해야 합니다. 이를 선택하려면 신뢰 관리자가 배포에 서명하는 데 사용된 인증서를 클라이언트의 신뢰할 수 있는 게시자 저장소에 저장된 인증서와 비교해야 합니다. 신뢰 관리자가 일치 항목을 찾으면 애플리케이션이 높은 신뢰로 실행됩니다.  
  
## <a name="trusted-application-deployment-and-permission-elevation"></a>신뢰할 수 있는 애플리케이션 배포 및 권한 상승  
 현재 게시자가 신뢰할 수 있는 게시자가 아니면 신뢰 관리자는 권한 상승을 사용하여 사용자에게 애플리케이션에 상승한 권한을 부여할지를 쿼리합니다. 그러나 관리자가 권한 상승을 사용하지 않도록 설정하면 애플리케이션이 실행할 권한을 가져올 수 없습니다. 애플리케이션이 실행되지 않고 사용자에게 알림이 표시되지 않습니다. 권한 상승에 대 한 자세한 내용은 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)을 참조 하세요.  
  
## <a name="limitations-of-trusted-application-deployment"></a>신뢰할 수 있는 애플리케이션 배포 제한 사항  
 신뢰할 수 있는 애플리케이션 배포를 사용하여 웹 또는 엔터프라이즈 파일 공유를 통해 배포된 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션에 상승한 신뢰를 부여할 수 있습니다. CD에서 배포된 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션에는 신뢰할 수 있는 애플리케이션 배포를 사용할 필요가 없습니다. 기본적으로 이러한 애플리케이션에는 완전 신뢰가 부여되기 때문입니다.  
  
## <a name="see-also"></a>관련 항목  
 [Mage.exe (매니페스트 생성 및 편집 도구)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [연습: 수동으로 ClickOnce 애플리케이션 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
