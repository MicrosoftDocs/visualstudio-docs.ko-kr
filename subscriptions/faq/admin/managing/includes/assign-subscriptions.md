---
title: Visual Studio 구독을 할당하려면 어떻게 해야 하나요?
description: 최종 사용자에게 한 번에 하나씩 구독을 할당하거나, 대량 추가 기능을 사용하여 한 번에 많은...
ms.faqid: group1_3
ms.topic: include
ms.assetid: 59eb35fd-ec94-41ce-b24c-a8a120976bac
author: CaityBuschlen
ms.author: cabuschl
ms.date: 09/30/2020
ms.openlocfilehash: add0bac2a9e7eb053c183d66fcee17c8133bb921
ms.sourcegitcommit: ea3c985a23851b424127f2205f617446b6536578
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91641532"
---
## <a name="how-do-i-assign-visual-studio-subscriptions"></a>Visual Studio 구독을 할당하려면 어떻게 해야 하나요?

최종 사용자에게 한 번에 하나씩 구독을 할당하거나, 대량 추가 기능을 사용하여 한 번에 많은 구독자를 빠르고 쉽게 업로드할 수 있습니다.

구독을 개별적으로 할당하려면 다음을 수행합니다.

1. [manage.visualstudio.com](https://manage.visualstudio.com) 페이지 맨 위에 있는 [구독자 관리 탭](https://manage.visualstudio.com/subscribers)을 선택합니다.
2. 추가를 선택하고 구독을 할당하려는 사용자의 이름과 전자 메일 주소를 입력합니다.
    1. 조직에서 Azure Active Directory를 사용하는 경우 이름 필드는 현재 디렉터리에서 사용자를 검색하여 찾습니다. 검색 결과에서 선택하거나, 특정 사용자를 수동으로 추가할 수 있습니다.
3. 구독자가 [Visual Studio 구독 포털](https://my.visualstudio.com/)에 로그인한 경우 소프트웨어 다운로드에 액세스할 수 있게 하려면, 다운로드 설정 섹션에서 다운로드 토글을 사용하도록 설정된 상태로 둡니다.
4. 구독자 할당 전자 메일을 보낼 때 사용할 언어를 알 수 있도록 통신 기본 설정 섹션을 완료합니다.
5. 할당과 관련된 메모를 추가하려면 참조 선택 항목을 사용하세요.
6. 플라이아웃 패널 맨 아래에 있는 추가를 선택하여 구독 할당을 완료합니다. 구독자는 전자 메일을 받게 되고, 해당 Visual Studio 구독을 즉시 사용할 수 있습니다(구독자 쪽에서 활성화할 필요가 없음).

구독을 대량 할당하려면 다음을 수행합니다.

1. [manage.visualstudio.com](https://manage.visualstudio.com) 페이지 맨 위에 있는 [구독자 관리 탭](https://manage.visualstudio.com/subscribers)을 선택합니다.
2. 대량 추가를 선택하고 Excel 템플릿을 다운로드한 다음, 로컬 복사본을 저장합니다.
3. 참조 필드를 제외한 모든 필드가 필수입니다.
    1. 양식 필드에 쉼표가 없는지 확인합니다.
    2. 양식 필드 앞뒤의 공백을 제거합니다.
    3. 사용자 이름에서 두 부분으로 이루어진 이름이나 성 사이에 공백이 포함되지 않도록 합니다. 예를 들어 사용자 이름이 “Maggie May”와 같이 두 부분으로 이루어진 경우 “MaggieMay”로 입력해야 합니다.
4. [manage.visualstudio.com](https://manage.visualstudio.com)으로 돌아가서 대량 추가를 선택한 다음, 저장된 Excel 템플릿 복사본을 업로드합니다.
5. 업로드가 성공적으로 완료되면 확인 페이지가 표시되고, 구독자 목록이 새 구독자로 채워집니다. 구독자는 전자 메일을 받게 되고, 해당 Visual Studio 구독을 즉시 사용할 수 있습니다(구독자 쪽에서 활성화할 필요가 없음).

Visual Studio 구독 관리자 포털에서 구독 할당에 대한 [자세한 내용을 읽고](https://docs.microsoft.com/visualstudio/subscriptions/assign-license#add-a-single-subscriber) 구독을 빠르고 쉽게 할당하는 방법을 알아봅니다.  GitHub Enterprise 구독이 포함된 Visual Studio를 관리하는 방법에 대해 [자세히 알아봅니다](https://docs.microsoft.com/visualstudio/subscriptions/assign-github). 

## <a name="what-is-the-github-enterprise-setup-process"></a>GitHub Enterprise 설치 프로세스는 무엇인가요? 

GitHub Enterprise는 Visual Studio 구독과 별도로 설정 및 관리됩니다. GitHub Enterprise 구매가 포함된 Visual Studio에 따라 GitHub Enterprise 계정 설정 프로세스는 manage.visualstudio.com에서 계약을 설정하는 것과 병렬(그러나 별도로)로 시작됩니다. 이 GitHub Enterprise 계정을 설정하는 데 다소 시간이 걸릴 수 있습니다.  

회사에서 GitHub Enterprise 계정을 설정한 후 GitHub Enterprise 구독이 있는 Visual Studio가 할당된 구독자는 GitHub에서 Visual Studio 구독이 연결되었음을 알리는 이메일을 받게 됩니다. 구독자는 이 이메일을 받은 후 GitHub 조직 관리자에게 연락하여 해당 조직에 대한 초대를 받을 수 있습니다. 

GitHub Enterprise 구독이 포함된 Visual Studio를 관리하는 방법에 대해 [자세히 알아봅니다](https://docs.microsoft.com/visualstudio/subscriptions/assign-github). GitHub Enterprise 설정 프로세스에 대한 자세한 내용은 [구독자 설명서](https://docs.microsoft.com/visualstudio/subscriptions/access-github)를 참조하세요. 