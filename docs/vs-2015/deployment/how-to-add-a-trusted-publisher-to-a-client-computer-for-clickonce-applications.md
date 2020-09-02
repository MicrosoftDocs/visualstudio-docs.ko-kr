---
title: '방법: ClickOnce 응용 프로그램의 클라이언트 컴퓨터에 신뢰할 수 있는 게시자 추가 | Microsoft Docs'
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
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 296aec3b2b5cd307400b230375a7171f158fee60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847691"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>방법: ClickOnce 애플리케이션의 클라이언트 컴퓨터에 신뢰할 수 있는 게시자 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

신뢰할 수 있는 애플리케이션 배포를 사용하면 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션이 사용자 프롬프트 없이 더 높은 신뢰 수준으로 실행되도록 클라이언트 컴퓨터를 구성할 수 있습니다. 다음 절차에서는 명령줄 도구 CertMgr.exe를 사용하여, 클라이언트 컴퓨터의 신뢰할 수 있는 게시자 저장소에 게시자의 인증서를 추가하는 방법을 보여 줍니다.  
  
 인증서를 발급한 CA(인증 기관)가 클라이언트의 신뢰할 수 있는 루트의 일부인지 여부에 따라 사용하는 명령이 약간 달라집니다. Windows 클라이언트 컴퓨터가 도메인의 일부이면 신뢰할 수 있는 루트로 간주되는 CA가 목록에 포함됩니다. 이 목록은 일반적으로 시스템 관리자가 구성합니다. 인증서가 이러한 신뢰할 수 있는 루트 중 하나에서 또는 이와 연결된 CA에서 발급된 경우, 클라이언트의 신뢰할 수 있는 루트 저장소에 인증서를 추가할 수 있습니다. 반면, 인증서가 이러한 신뢰할 수 있는 루트 중 하나에서 발급되지 않은 경우 클라이언트의 신뢰할 수 있는 루트 저장소 및 신뢰할 수 있는 게시자 저장소에 모두 인증서를 추가해야 합니다.  
  
> [!NOTE]
> 높은 권한이 필요한 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션을 배포하려는 모든 클라이언트 컴퓨터에서 이 방식으로 인증서를 추가해야 합니다. 수동으로 또는 클라이언트에 배포하는 애플리케이션을 통해 인증서를 추가합니다. 이러한 컴퓨터를 한 번만 구성하면 됩니다. 그 후에는 동일한 인증서로 서명된 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 애플리케이션을 원하는 만큼 배포할 수 있습니다.  
  
 <xref:System.Security.Cryptography.X509Certificates.X509Store> 클래스를 사용하여 프로그래밍 방식으로 저장소에 인증서를 추가할 수도 있습니다.  
  
 신뢰할 수 있는 응용 프로그램 배포에 대 한 개요는 [신뢰할 수 있는 응용 프로그램 배포 개요](../deployment/trusted-application-deployment-overview.md)를 참조 하세요.  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>신뢰할 수 있는 루트 아래의 신뢰할 수 있는 게시자 저장소에 인증서를 추가하려면  
  
1. CA에서 디지털 인증서를 가져옵니다.  
  
2. Base64 X.509(.cer) 형식으로 인증서를 내보냅니다. 인증서 형식에 대 한 자세한 내용은 [인증서 내보내기](https://technet.microsoft.com/library/cc730988(WS.10).aspx)를 참조 하세요.  
  
3. 클라이언트 컴퓨터의 명령 프롬프트에서 다음 명령을 실행합니다.  
  
     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>다른 루트 아래의 신뢰할 수 있는 게시자 저장소에 인증서를 추가하려면  
  
1. CA에서 디지털 인증서를 가져옵니다.  
  
2. Base64 X.509(.cer) 형식으로 인증서를 내보냅니다. 인증서 형식에 대 한 자세한 내용은 [인증서 내보내기](https://technet.microsoft.com/library/cc730988(WS.10).aspx)를 참조 하세요.  
  
3. 클라이언트 컴퓨터의 명령 프롬프트에서 다음 명령을 실행합니다.  
  
     **certmgr.exe -add good.cer -c -s -r localMachine Root**  
  
     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>관련 항목  
 [연습: ClickOnce 응용 프로그램 수동 배포](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)   
 [ClickOnce 응용 프로그램에 대 한 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce 및 Authenticode](../deployment/clickonce-and-authenticode.md)   
 [신뢰할 수 있는 응용 프로그램 배포 개요](../deployment/trusted-application-deployment-overview.md)   
 [방법: ClickOnce 보안 설정 사용](../deployment/how-to-enable-clickonce-security-settings.md)   
 [방법: ClickOnce 응용 프로그램의 보안 영역 설정](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [방법: ClickOnce 응용 프로그램에 대 한 사용자 지정 권한 설정](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [방법: 제한 된 권한으로 ClickOnce 응용 프로그램 디버깅](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [방법: ClickOnce 응용 프로그램의 클라이언트 컴퓨터에 신뢰할 수 있는 게시자 추가](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [방법: 응용 프로그램 및 배포 매니페스트 다시 서명](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [방법: ClickOnce 신뢰 프롬프트 동작 구성](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
