---
title: 포함 목록을 사용 하 여 Office 솔루션 신뢰
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- inclusion lists [Office development in Visual Studio], about inclusion lists
- security [Office development in Visual Studio], inclusion lists
- inclusion lists [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a4787831be31e2f91d668d4e3e7ca91496d7595a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985543"
---
# <a name="trust-office-solutions-by-using-inclusion-lists"></a>포함 목록을 사용 하 여 Office 솔루션 신뢰
  포함 목록을 사용하면 사용자가 게시자를 식별하는 인증서로 서명된 Office 솔루션에 신뢰를 부여할 수 있습니다. 포함 목록은 사용자마다 고유하며 문서 수준 사용자 지정 및 VSTO 추가 기능에 대해 사용할 수 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 사용자가 자신에게 신뢰가 부여되지 않은 Office 솔루션을 시작하면 Microsoft Office 솔루션에서 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 신뢰 프롬프트와 함께 보안 결정에 대한 메시지를 표시합니다. 사용자가 솔루션을 신뢰하도록 결정한 경우 사용자 지정이 실행되고 다음에 사용자에게 메시지를 표시하지 않습니다.

## <a name="inclusion-list-and-windows-installer"></a>포함 목록 및 Windows Installer
 Windows Installer를 사용 하 여 *Program Files* 디렉터리에 Office 솔루션을 설치 하려면 관리자 권한이 필요 합니다. *Program Files* 디렉터리의 office 솔루션의 경우 office 솔루션에 이미 FullTrust 권한이 부여 되어 있으므로 Visual Studio Tools for Office 런타임은 더 이상 포함 목록을 확인 하지 않습니다.

## <a name="clickonce-trust-prompt"></a>ClickOnce 신뢰 프롬프트
 관리자는 Office 솔루션에 대해 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 구현을 사용하여 프롬프트 허용, 프롬프트 사용 안 함 또는 신뢰할 수 있는 인증서 필요 등 신뢰 프롬프트 수준을 구성할 수 있습니다. 이 구성은 포함 목록에 대한 액세스를 제어하는 레지스트리 키를 사용하여 수행합니다.

 프롬프트를 사용하지 않는 경우 신뢰할 수 있고 알려진 인증서가 있는 솔루션만 설치할 수 있습니다. Authenticode가 필요한 것으로 프롬프트 수준이 설정된 경우 솔루션이 알려진 인증 기관의 인증서로 서명되어야 하지만, 신뢰할 수 있는 루트 인증 기관에 연결된 인증서(신뢰할 수 있는 인증서)는 필요하지 않습니다. 프롬프트가 허용되는 경우 솔루션을 알 수 없는 ID를 가진 인증서로 서명할 수 있습니다. 이 시나리오에서는 신뢰 결정이 최종 사용자 단계까지 연기되고 임시 인증서로 솔루션을 설치할 수 있습니다.

 자세한 내용은 [How to: configure 포함 목록 보안](../vsto/how-to-configure-inclusion-list-security.md) 및 표 2 (참조 수준 레지스트리 키 값 시작 효과를 참조 하십시오.) [ClickOnce 신뢰할 수 있는 게시자 구성](/previous-versions/dotnet/articles/ms996418(v=msdn.10))

## <a name="structure-of-the-inclusion-list"></a>포함 목록의 구조
 올바른 포함 목록 항목에는 두 부분이 포함됩니다. 배포 매니페스트에 대한 경로와 솔루션 서명에 사용되는 공개 키입니다. 포함 목록에 추가된 솔루션은 신뢰할 수 있는 것으로 간주됩니다. Office 솔루션이 실행될 때 Office 애플리케이션은 포함 목록의 공개 키를 배포 매니페스트의 서명 키와 비교하여 현재 실행 중인 솔루션이 원래 신뢰된 버전과 동일한지 확인합니다.

## <a name="see-also"></a>추가 정보
- [Office 솔루션에 신뢰 부여](../vsto/granting-trust-to-office-solutions.md)
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
