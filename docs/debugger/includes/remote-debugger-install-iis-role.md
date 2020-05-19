---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 13ca035b01ec8af1277d70b3c792293a1af4687a
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149235"
---
이러한 단계는 IIS의 기본 구성만 보여 줍니다. 자세한 정보를 확인하거나 Windows Desktop 머신에 설치하려면 [IIS에 게시](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration) 또는 [ASP.NET 3.5 및 ASP.NET 4.5를 사용하는 IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)을 참조하세요.

Windows Server 운영 체제의 경우 **서버 관리자**의 **관리** 링크 또는 **대시보드** 링크를 통해 **역할 및 기능 추가** 마법사를 사용합니다. **서버 역할** 단계에서 **웹 서버(IIS)** 확인란을 선택합니다.

![서버 역할 선택 단계에서 선택된 웹 서버 IIS 역할](../media/remotedbg-server-roles-ws2012.png)

**역할 서비스** 단계에서 원하는 IIS 역할 서비스를 선택하거나 제공된 기본 역할 서비스를 받아들입니다. 게시 설정 및 웹 배포를 사용하여 배포를 사용 설정하려면 **IIS 관리 스크립트 및 도구**가 선택되어 있는지 확인합니다.

확인 단계를 진행하여 웹 서버 역할 및 서비스를 설치합니다. 웹 서버(IIS) 역할을 설치한 후에 서버/IIS를 다시 시작할 필요가 없습니다.