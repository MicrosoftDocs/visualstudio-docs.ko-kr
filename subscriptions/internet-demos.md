---
title: 제품 키를 사용하여 터미널 서비스를 통한 인터넷 데모 지원 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 1c5ede60-cb5a-4d5f-a6a2-a1f536f6c4ad
ms.date: 03/09/2020
ms.topic: conceptual
description: 제품 키를 사용하여 터미널 서비스를 통한 인터넷 데모를 지원하고 RDS 액세스를 활성화하는 방법을 알아봅니다.
ms.openlocfilehash: 2d5f23f0d161ee9f50569e0ff7f8ce585c8c49ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80232435"
---
# <a name="internet-demonstrations-via-terminal-services"></a>터미널 서비스를 통한 인터넷 데모
Visual Studio 구독을 사용하면 최종 사용자가 터미널 서비스(Windows Server 2003 또는 Windows Server 2008) 또는 원격 데스크톱 서비스(Windows Server 2008 R2 이상)를 통해 프로그램의 인터넷 데모에 액세스할 수 있는 권한을 제공할 수 있습니다. 최대 200명의 익명 사용자가 이러한 방법으로 동시에 데모에 액세스할 수 있습니다. 데모에서 프로덕션 데이터를 사용하면 안됩니다. Visual Studio 구독자에게는 자신의 애플리케이션을 최종 사용자에게 시연할 수 있는 라이선스가 부여됩니다. TS(터미널 서비스) 또는 RDS(원격 데스크톱 서비스)를 사용한 이 인터넷 데모는 Visual Studio 구독을 통해 소프트웨어에 라이선스가 부여되었을 때 Visual Studio 구독이 없는 최종 사용자가 데모 애플리케이션과 상호 작용할 수 있는 유일한 시나리오입니다.

이는 Visual Studio 구독자가 필요한 만큼 많은 수의 RDS 또는 TS 연결을 사용할 수 있는 개발/테스트 권한에 추가되는 권한입니다.

## <a name="enabling-rds-access"></a>RDS 액세스 사용
Visual Studio 구독자는 [구독자 포털](https://my.visualstudio.com?wt.mc_id=o~msft~docs)의 [제품 키](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) 탭에서 제공된 제품 키를 입력하여 RDS를 통해 Windows Server에 액세스할 수 있는 사용자 수를 늘릴 수 있습니다. 제품 키를 얻으려면 [제품 키] 페이지에 연결하고 실행 중인 Windows Server 버전까지 스크롤합니다. "Windows Server &lt; 버전 &gt; R2 원격 데스크톱 서비스 &lt; 사용자 또는 디바이스 &gt; 연결 수"를 찾고 **키 요청** 링크를 클릭합니다. 예를 들어 Windows Server 2012 R2에서 RDS를 사용하고 배포에서 사용자 CAL을 사용하는 경우 "Windows Server 2012 원격 데스크톱 서비스 사용자 연결 수(50)"를 선택합니다.
각 유형의 5개 키는 Windows Server 2008 R2에 대해 사용할 수 있으며, 각 키는 20개의 연결을 지원합니다. Windows Server 2012 R2의 경우 각 유형에 대한 4개의 키가 제공되며 각각 50개의 연결을 지원합니다.

## <a name="to-enable-additional-connections-in-windows-server"></a>Windows Server에서 추가 연결을 사용하도록 설정하려면
1. 서버 관리자를 엽니다.
2. 왼쪽 탐색 창에서 [서버] 목록을 엽니다.
3. 라이선스 서버를 마우스 오른쪽 단추로 클릭하고 "라이선스 설치"를 선택합니다.
4. 마법사의 단계별 지침을 따릅니다.  계약 유형을 선택할 때 "라이선스 팩(일반 정품)"을 선택하고 [내] 포털에서 얻은 제품 키를 입력합니다.

다음 조건이 충족되면 최종 사용자가 RDS를 통해 애플리케이션에 액세스할 수 있습니다.
- 사용자는 익명이어야 합니다(인증되지 않은 상태).
- 인터넷을 통한 연결이어야 합니다.
- 애플리케이션 데모를 위해 최대 200명의 동시 사용자 연결을 사용할 수 있습니다.
- Visual Studio 구독자는 사용자 연결을 사용하도록 설정하기 위한 제품 키를 얻어야 합니다.

## <a name="see-also"></a>참조
- [Windows Server 설명서](https://docs.microsoft.com/windows-server/)
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>다음 단계
RDS 배포 관련 지침이 필요하신 경우 https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerf 에서 여러 파트로 구성된 **RDS(원격 데스크톱 서비스) 2012 세션 배포** 관련 블로그 시리즈를 참조하세요. 

의문 사항이 있으면 [Microsoft 원격 데스크톱 서비스 포럼](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS)을 방문하세요.
