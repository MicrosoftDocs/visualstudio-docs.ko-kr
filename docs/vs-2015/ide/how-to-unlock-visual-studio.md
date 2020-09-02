---
title: Visual Studio 2015 잠금 해제 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ffb580a1-8b5d-48f5-b811-87f8036f50ea
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a71a045661c48fd36733ecd8d2266470667a5c35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670588"
---
# <a name="how-to-unlock-visual-studio"></a>Visual Studio 잠금을 해제하는 방법
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

최대 30일 동안 무료로 Visual Studio 평가판을 사용할 수 있습니다. IDE에 로그인하면 90일 평가판 사용 기간을 연장할 수 있습니다. Visual Studio를 계속 사용하려면 다음과 같은 방법으로 IDE를 잠금 해제할 수 있습니다.

1. 온라인 구독 사용

2. 제품 키 입력

## <a name="to-unlock-visual-studio-using-an-online-subscription"></a>온라인 구독을 사용하여 Visual Studio의 잠금을 해제하려면
 Microsoft 계정이나 회사 또는 학교 계정과 연결된 MSDN 또는 Visual Studio 온라인 구독을 사용하여 Visual Studio를 잠금 해제하려면:

1. IDE 오른쪽 위의 “로그인” 단추를 클릭하거나 파일 > 계정 설정을 선택하여 계정 설정 대화 상자를 열고 “로그인" 단추를 클릭합니다.

2. Microsoft 계정이나 회사 또는 학교 계정에 대한 자격 증명을 입력합니다. Visual Studio에서 해당 계정과 연결된 MSDN 구독 또는 Visual Studio Team Services 구독을 찾습니다.

> [!IMPORTANT]
> 팀 탐색기 도구 창에서 Visual Studio Team Services 계정에 연결하면 Visual Studio에서 연결된 온라인 구독을 자동으로 찾습니다. Visual Studio Team Services 계정에 연결하면 Microsoft와 회사 또는 학교 계정을 사용하여 로그인할 수 있습니다. 해당 사용자 계정에 대한 온라인 구독이 있으면 Visual Studio에서 IDE를 자동으로 잠금 해제합니다.

## <a name="to-unlock-visual-studio-with-a-product-key"></a>제품 키를 사용하여 Visual Studio의 잠금을 해제하려면

1. **파일 > 계정 설정**을 선택하여 계정 설정 대화 상자를 열고 "**제품 키가 있는 라이선스**" 링크를 클릭합니다.

2. 제공된 입력란에 제품 키를 입력합니다.

> [!TIP]
> 시험판 버전의 Visual Studio에는 제품 키가 없습니다. 시험판 버전을 사용하려면 IDE에 로그인해야 합니다.

## <a name="addressing-license-problem-states"></a>라이선스 문제 상태 해결

### <a name="updating-stale-licenses"></a>부실 라이선스 업데이트
 라이선스가 Visual Studio에서 부실하게 된다는 아래 메시지가 표시됩니다.

 ![Visual Studio 사용자 정보 대화 상자](../ide/media/vs2013-userinfo.png "VS2013_UserInfo")

 이 메시지는 구독이 여전히 유효할 수 있지만 Visual Studio에서 구독을 최신으로 유지하는 데 사용하는 라이선스 토큰이 새로 고쳐지지 않았으므로 다음 이유 중 하나로 인해 부실해졌음을 나타냅니다.

1. Visual Studio를 사용한 적이 없거나 오랫동안 인터넷에 연결되지 않았습니다.

2. Visual Studio에서 로그아웃했습니다.

   라이선스 토큰이 부실해지기 전에 Visual Studio에서 먼저 자격 증명을 다시 입력하라는 경고 메시지를 표시합니다.

   자격 증명을 다시 입력하지 않으면 토큰이 부실해집니다. 이 경우 계정 설정 대화 상자에서 토큰이 완전히 만료될 때까지 남은 기간(일)을 표시합니다. 토큰이 만료된 후 위의 다른 방법으로 이 계정 또는 라이선스에 대한 자격 증명을 다시 입력해야 Visual Studio를 계속 사용할 수 있습니다.

> [!IMPORTANT]
> 인터넷 연결이 제한되거나 인터넷에 연결되지 않는 환경에서 오랫동안 Visual Studio를 사용하는 경우 작업이 중단되지 않도록 제품 키를 사용하여 Visual Studio의 잠금을 해제해야 합니다.

### <a name="updating-expired-licenses"></a>만료된 라이선스 업데이트
 구독이 완전히 만료되어 Visual Studio 액세스 권한이 더 이상 없으면 다음을 수행해야 합니다.

1. 구독을 갱신합니다. 사용 중인 라이선스에 대한 자세한 정보를 보려면 파일 > 계정 설정 대화 상자로 이동하고 대화 상자의 오른쪽에 있는 라이선스 정보를 살펴봅니다.

2. 다른 계정에 연결된 다른 구독이 있는 경우 "계정 추가..." 링크를 클릭하여 파일 > 계정 설정 대화 상자의 왼쪽에 있는 모든 계정 목록에 해당 계정을 링크를 사용하여 비용 없이 계정을 만들 수 있습니다.

## <a name="see-also"></a>관련 항목
 [Visual Studio에 로그인](../ide/signing-in-to-visual-studio.md)
