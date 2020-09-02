---
title: Office 솔루션에 신뢰 부여
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315241"
---
# <a name="grant-trust-to-office-solutions"></a>Office 솔루션에 신뢰 부여
  Office 솔루션에 신뢰 부여는 솔루션 어셈블리, 응용 프로그램 매니페스트, 배포 매니페스트 및 문서를 신뢰 하도록 각 대상 컴퓨터의 보안 정책을 수정 하는 것을 의미 합니다. 사용자 또는 최종 사용자가 Office 솔루션에 신뢰를 부여할 수 있습니다.

 응용 프로그램 및 배포 매니페스트에 서명 하 여 Office 솔루션에 대 한 완전 신뢰를 부여할 수 있습니다.

 최종 사용자는 신뢰 프롬프트에서 신뢰 사항을 결정 하 여 Office 솔루션에 신뢰를 부여할 수 있습니다 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] .

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trust-the-solution-by-signing-the-application-and-deployment-manifests"></a><a name="Signing"></a> 응용 프로그램 및 배포 매니페스트에 서명 하 여 솔루션 신뢰
 Office 솔루션에 대 한 모든 응용 프로그램 및 배포 매니페스트는 게시자를 식별 하는 인증서를 사용 하 여 서명 되어야 합니다. 인증서는 신뢰 결정을 위한 기초를 제공 합니다.

 임시 인증서는 사용자를 위해 만들어지며 빌드 시 신뢰를 부여 하므로 디버그 하는 동안 솔루션이 실행 됩니다. 임시 인증서로 서명 된 솔루션을 게시 하면 최종 사용자에 게 신뢰를 결정 하 라는 메시지가 표시 됩니다.

 알려진 신뢰할 수 있는 인증서를 사용 하 여 솔루션에 서명 하는 경우 최종 사용자에 게 트러스트 결정을 요구 하지 않고 솔루션이 자동으로 설치 됩니다. 서명할 인증서를 가져오는 방법에 대 한 자세한 내용은 [ClickOnce 및 Authenticode](../deployment/clickonce-and-authenticode.md)를 참조 하세요. 인증서를 가져온 후에는 신뢰할 수 있는 게시자 목록에 인증서를 추가 하 여 인증서를 명시적으로 신뢰 해야 합니다. 자세한 내용은 [방법: ClickOnce 응용 프로그램의 클라이언트 컴퓨터에 신뢰할 수 있는 게시자 추가](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)를 참조 하세요.

 개발자가 임시 인증서를 사용 하 여 솔루션에 서명 하는 경우 관리자는 Microsoft .NET Framework 도구 중 하나인 매니페스트 생성 및 편집 도구 (*mage.exe*)를 사용 하 여 알려진 신뢰할 수 있는 인증서로 사용자 지정을 다시 서명할 수 있습니다. 솔루션에 서명 하는 방법에 대 한 자세한 내용은 [방법: Office 솔루션에 서명](../vsto/how-to-sign-office-solutions.md) 및 [방법: 응용 프로그램 및 배포 매니페스트 서명](../ide/how-to-sign-application-and-deployment-manifests.md)을 참조 하세요.

## <a name="trust-the-solution-by-using-the-clickonce-trust-prompt"></a><a name="TrustPrompt"></a>ClickOnce 신뢰 프롬프트를 사용 하 여 솔루션 신뢰
 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 최종 사용자에 게 솔루션의 인증서를 신뢰 하는 조직 차원의 정책이 없는 경우 신뢰 결정을 내리는 메시지를 표시 합니다. 최종 사용자가 솔루션에 신뢰를 부여 하는 경우이 신뢰 결정을 저장할 URL과 공개 키를 포함 하는 포함 목록 항목이 생성 됩니다. 신뢰할 수 있는 사용자 지정을 나중에 실행 하는 경우 최종 사용자에 게 다시 메시지가 표시 되지 않습니다.

 관리자는 신뢰 프롬프트를 사용 하지 않도록 설정 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 하거나 Authenticode 인증서로 서명 된 솔루션에 대해서만 메시지가 표시 되도록 요구할 수 있습니다. 이러한 설정을 변경 하는 방법에 대 한 자세한 내용은 MyComputer, LocalIntranet, 인터넷, 신뢰할 수 있는 사이트 및 un Sites 영역에 대 한 자세한 내용은 [방법: ClickOnce 신뢰 프롬프트 동작 구성](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [문서에 신뢰 부여](../vsto/granting-trust-to-documents.md)
- [Office 솔루션 보안 문제 해결](../vsto/troubleshooting-office-solution-security.md)
- [Office 솔루션에 대 한 특정 보안 고려 사항](../vsto/specific-security-considerations-for-office-solutions.md)