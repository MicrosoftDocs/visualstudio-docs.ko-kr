---
title: Office 솔루션 보안 문제 해결
ms.date: 02/02/2017
ms.topic: troubleshooting
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8825f1f4393d93df6a621fd71b6782c6652a9c0c
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234811"
---
# <a name="troubleshoot-office-solution-security"></a>Office 솔루션 보안 문제 해결
  이 항목에는 Office 솔루션 보안으로 작업할 때 발생할 수 있는 일반적인 문제를 해결 하기 위한 팁이 포함 되어 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-solutions-cannot-be-installed-from-restricted-sites"></a>제한 된 사이트에서는 신뢰할 수 있는 솔루션을 설치할 수 없습니다.
 웹 사이트가 Internet Explorer 제한 된 사이트 영역에 표시 되는 경우 사용자는 웹 위치에서 솔루션을 설치할 수 없습니다. 솔루션이 신뢰할 수 있는 인증서로 서명 된 경우에도 마찬가지입니다.

 배포 매니페스트의 URL은 5 개 영역 중 하나로 분류 될 수 있습니다.

- 내 컴퓨터

- 인터넷

- 로컬 인트라넷

- 신뢰할 수 있는 사이트

- 제한 된 사이트

  배포 매니페스트의 위치가 제한 된 사이트 영역에 할당 된 경우는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 솔루션을 설치 하지 않습니다. 위치가 알려져 있고 신뢰할 수 있는 경우 사용자는 제한 된 사이트 영역에서 위치를 제거 하 고 솔루션을 설치할 수 있습니다. 영역을 관리 하는 방법에 대 한 자세한 내용은 [ClickOnce의 신뢰할 수 있는 게시자 구성](/previous-versions/dotnet/articles/ms996418(v=msdn.10))을 참조 하세요.

## <a name="solutions-cannot-be-installed-from-network-file-shares-or-web-locations-when-internet-explorer-enhanced-security-configuration-or-internet-explorer-7-is-installed"></a>Internet Explorer 보안 강화 구성 또는 Internet Explorer 7이 설치 된 경우 네트워크 파일 공유 또는 웹 위치에서 솔루션을 설치할 수 없습니다.
 Internet Explorer (internet Explorer 보안 강화 구성)는 Windows Server 2003 이상 및 Internet Explorer 7 이상에서 사용자의 인터넷 검색 기능을 크게 제한 합니다. 사용자가 네트워크 파일 공유 또는 웹 위치에서 Office 솔루션을 설치 하려고 하면 다음과 같은 오류 메시지가 표시 될 수 있습니다. " *SolutionName* 에 대 한 배포 매니페스트에 서명 하는 데 사용 되는 인증서를 신뢰할 수 없으므로이 응용 프로그램의 사용자 지정 기능이 작동 하지 않습니다. 자세한 내용은 관리자에 게 문의 하세요. "

 IEESC 및 Internet Explorer 7 이상에서 배포 매니페스트의 URL이 인터넷 영역에 분류 되어 있으면 매니페스트에 신뢰할 수 있는 게시자의 인증서가 있어야 합니다. 그렇지 않으면 솔루션을 설치할 수 없습니다. IEESC를 사용 하지 않으면 기본 동작은 최종 사용자에 게 신뢰 결정을 내리는 것입니다.

 IEESC 및 Internet Explorer 7 이상 효과를 관리 하려면 신뢰 하는 웹 사이트와 UNC (범용 명명 규칙) 경로를 확인 하 고 신뢰할 수 있는 보안 영역 (로컬 인트라넷 또는 신뢰할 수 있는 사이트) 중 하나에 추가 합니다. 영역을 관리 하는 방법에 대 한 자세한 내용은 [ClickOnce의 신뢰할 수 있는 게시자 구성](/previous-versions/dotnet/articles/ms996418(v=msdn.10))을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [Visual Studio 문제 해결](/troubleshoot/visualstudio/welcome-visual-studio/)
