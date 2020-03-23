---
title: Office 솔루션에 대한 신뢰 부여
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf7a68d5d3567305e4f70049d76a1c260ddecf25
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301658"
---
# <a name="grant-trust-to-office-solutions"></a>Office 솔루션에 대한 신뢰 부여
  Office솔루션에 대한 신뢰 부여란 솔루션 어셈블리, 응용 프로그램 매니페스트, 배포 매니페스트 및 문서를 신뢰하도록 각 대상 컴퓨터의 보안 정책을 수정하는 것을 의미합니다. 사용자 또는 최종 사용자가 Office 솔루션에 트러스트를 부여할 수 있습니다.

 응용 프로그램 및 배포 매니페스트에 서명하여 Office 솔루션에 대한 완전 신뢰를 부여할 수 있습니다.

 최종 사용자는 신뢰 프롬프트에서 신뢰 결정을 내도록 하여 Office 솔루션에 대한 신뢰를 부여할 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 수 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a>응용 프로그램 및 배포 매니페스트에 서명하여 솔루션을 신뢰합니다.
 Office 솔루션에 대한 모든 응용 프로그램 및 배포 매니페스트는 게시자를 식별하는 인증서로 서명해야 합니다. 인증서는 신뢰 결정을 내리기 위한 기초를 제공합니다.

 임시 인증서가 만들어지고 빌드 시 신뢰를 부여하므로 디버깅하는 동안 솔루션이 실행됩니다. 임시 인증서로 서명된 솔루션을 게시하면 최종 사용자에게 신뢰 결정을 내리라는 메시지가 표시됩니다.

 알려진 신뢰할 수 있는 인증서로 솔루션에 서명하면 최종 사용자에게 신뢰 결정을 내리라는 메시지가 표시되지 않고 솔루션이 자동으로 설치됩니다. 서명 인증서를 얻는 방법에 대한 자세한 내용은 [ClickOnce 및 Authenticode](../deployment/clickonce-and-authenticode.md)를 참조하십시오. 인증서를 얻은 후에는 인증서를 신뢰할 수 있는 게시자 목록에 추가하여 명시적으로 신뢰할 수 있어야 합니다. 자세한 내용은 [클릭Once 응용 프로그램에 대한 클라이언트 컴퓨터에 신뢰할 수 있는 게시자를 추가하는 방법을](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)참조하십시오.

 개발자가 임시 인증서로 솔루션에 서명하는 경우 관리자는 Microsoft .NET Framework 도구 중 하나인 매니페스트 생성 및 편집*도구(mage.exe)를*사용하여 알려진 신뢰할 수 있는 인증서로 사용자 지정에 다시 서명할 수 있습니다. 솔루션 서명에 대한 자세한 내용은 [Office 솔루션 서명](../vsto/how-to-sign-office-solutions.md) 방법 및 서명 응용 프로그램 및 배포 [매니페스트를](../ide/how-to-sign-application-and-deployment-manifests.md)참조하십시오.

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>ClickOnce 신뢰 프롬프트를 사용하여 솔루션을 신뢰하십시오.
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]솔루션의 인증서를 신뢰하는 조직 전체 정책이 없는 경우 최종 사용자에게 신뢰 결정을 내리도록 메시지를 표시합니다. 최종 사용자가 솔루션에 대한 신뢰를 부여하는 경우 이 신뢰 결정을 저장하는 URL과 공개 키가 포함된 포함 목록 항목이 만들어집니다. 나중에 신뢰할 수 있는 사용자 지정을 실행하면 최종 사용자에게 다시 메시지가 표시되지 않습니다.

 관리자는 신뢰 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 프롬프트를 사용하지 않도록 설정하거나 Authenticode 인증서로 서명된 솔루션에 대해서만 프롬프트가 발생하도록 요구할 수 있습니다. MyComputer, LocalIntranet, 인터넷, 신뢰할 수 있는 사이트 및 신뢰할 수 없는 사이트 영역에 대한 이러한 설정을 변경하는 방법에 대한 자세한 내용은 [클릭Once 신뢰 프롬프트 동작 구성 방법을](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)참조하십시오.

## <a name="see-also"></a>참고 항목

- [안전한 Office 솔루션](../vsto/securing-office-solutions.md)
- [문서에 대한 신뢰 부여](../vsto/granting-trust-to-documents.md)
- [Office 솔루션 보안 문제 해결](../vsto/troubleshooting-office-solution-security.md)
- [Office 솔루션에 대한 특정 보안 고려 사항](../vsto/specific-security-considerations-for-office-solutions.md)