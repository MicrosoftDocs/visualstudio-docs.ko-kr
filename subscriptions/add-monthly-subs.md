---
title: 구독 관리 포털에 새 월간 Visual Studio 구독 추가 | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 06/23/2020
ms.topic: how-to
description: 구독 관리 포털에 새로 구매한 월간 Visual Studio 구독을 추가하는 방법을 알아봅니다.
ms.openlocfilehash: 778a3adbc9ca2117b0328a10d52904921bd0b80c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904701"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>구독 관리 포털에 새 월간 Visual Studio 구독 추가
Azure 구독을 사용하여 새 월간 Visual Studio 구독을 구입하는 경우 사용자에게 구독을 할당하려면 해당 구독을 구독 관리 포털에 추가해야 할 수 있습니다.  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>내 구독을 추가해야 하는지 어떻게 확인하나요?
월간 구독을 추가하는 단계는 조직이 이미 보유한 구독의 종류와 사용자가 새 관리자인지 여부에 따라 달라집니다.
- 사용자가 새 관리자인 경우 구독 관리 포털에 처음 로그인할 때 Microsoft는 사용자에게 사용자 액세스 관리자 권한이 있는 Azure 구독을 확인합니다.  사용자에 대한 월간 구독이 확인되면 해당 구독이 자동으로 추가됩니다. 
- 사용자가 이전에 월간 구독을 추가하거나 관리한 적이 있는 경우 로그인할 때마다 Microsoft가 새 월간 구독을 검색합니다. 
- 이미 볼륨 라이선스를 통해 획득한 구독의 관리자이지만 이전에 월간 구독을 추가하거나 관리한 적이 없는 경우 아래 제공된 단계를 사용하여 해당 구독을 추가해야 합니다.

## <a name="how-to-add-monthly-subscriptions"></a>월간 구독을 추가하는 방법
1. <https://manage.visualstudio.com>에서 구독 관리 포털에 로그인합니다.
1. **구독자 관리** 탭에서 **새 계약** 드롭다운을 선택합니다. 
1. 드롭다운에서 **새 월간 구독**을 선택합니다.
   > [!div class="mx-imgBorder"]
   > ![새 월간 구독 추가 드롭다운](_img/add-monthly-subs/add-subs-drop-down.png)
1. 시스템은 사용자에게 사용자 액세스 관리자 권한이 있는 Azure 구독을 검색하고 해당 Azure 구독을 사용하여 구매한 모든 Visual Studio 구독을 가져옵니다.
1. 사용자에게 사용자 액세스 관리자 권한이 있는 Azure 구독을 찾을 수 없거나 적격 Azure 구독이 있지만 Visual Studio 구독을 찾을 수 없는 경우 다음 메시지가 표시됩니다.
   > [!div class="mx-imgBorder"]
   > ![새 월간 구독을 찾을 수 없음](_img/add-monthly-subs/no-subs-found.png)
1. 시스템이 새 월간 구독을 찾으면 사용자에게 확인 메시지를 보냅니다.
   > [!div class="mx-imgBorder"]
   > ![구독 추가 확인 메시지](_img/add-monthly-subs/subs-added-confirmation.png)

## <a name="things-to-keep-in-mind"></a>주의할 사항
- 새 월간 구독을 추가하는 옵션은 처음 구입할 때만 사용할 수 있습니다.  월간 구독이 추가된 후에는 사용자가 포털에 로그인할 때마다 시스템이 새 구독을 검색합니다. 
- 새 구독이 검색될 때 구독자에 이미 할당된 것으로 확인될 수도 있습니다.  이는 Azure 구독에 대한 액세스 권한이 있는 다른 관리자가 새 Visual Studio 구독을 사용자에게 이미 할당했기 때문입니다.  이제 포털에 추가되었으므로 이러한 구독을 관리할 수 있습니다. 

## <a name="next-steps"></a>다음 단계
구독을 추가했으므로 사용자에게 할당할 준비가 되었습니다.  이 작업은 여러 방법으로 수행할 수 있습니다.
- [개별적으로 구독을 할당](assign-license.md)
- [여러 사용자에게 구독을 할당](assign-license-bulk.md)
- [특정 사용자에게 특정 구독을 할당](assign-guid.md)

## <a name="see-also"></a>참조
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)
