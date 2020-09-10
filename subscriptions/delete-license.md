---
title: Visual Studio 구독 관리 포털에서 구독 할당 삭제 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 06/16/2020
ms.topic: how-to
description: 관리자가 구독 할당을 삭제하는 방법에 대해 알아봅니다.
ms.openlocfilehash: 4f952f574132afbd405c82c75fcddfc952bffb48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87434272"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Visual Studio 구독에서 할당 삭제
회사를 떠나거나, 프로젝트가 완료되거나, 새로운 작업 역할로 전환되는 경우처럼 구독자에게 더 이상 Visual Studio 구독이 필요하지 않은 경우 해당 구독을 제거하고 다른 사람에게 할당할 수 있습니다. 구독을 다시 할당하면 일부 구독자 혜택은 재설정되지 않습니다.  새 사용자는 요청되지 않은 키를 요청하고, 이전에 요청된 키를 볼 수 있지만 클레임 제한은 재설정되지 **않습니다**.  EA(기업 계약)가 있는 조직의 경우 원래 사용자가 사용한 모든 혜택(예: Pluralsight 교육)은 다시 설정됩니다. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>구독 할당 삭제
1. 제거하려는 구독자의 이름을 클릭합니다. 제거할 구독자를 여럿 선택하려면 구독자 이름 왼쪽에 있는 원을 클릭하여 각 구독자를 선택하면 됩니다.  또는 **CTRL** 키를 누른 채로 제거할 각 구독자를 클릭하면 됩니다. 구독자의 범위를 제거하려면 첫 번째 구독자를 클릭하고 **Shift** 키를 누른 상태에서 마지막 구독자를 클릭합니다.  모든 구독자를 선택하고 제거하려면 **CTRL + A**를 누릅니다. 
2. 선택한 구독자를 삭제하려면 **삭제**를 클릭합니다.
3. 삭제를 확인하는 메시지가 나타나면 **확인**을 클릭합니다.
   > [!div class="mx-imgBorder"]
   > ![구독자 삭제](_img/delete-license/delete-subscribers.png "삭제하려는 사용자를 선택하고 삭제를 클릭합니다. Ctrl 및 Shift 키를 사용하여 여러 구독자를 선택할 수 있습니다.")

   > [!NOTE]
   > 템플릿을 사용한 대량 삭제는 사용할 수 없습니다. Azure Active Directory 보안 그룹을 통해 구독 할당을 관리하는 조직에서 삭제를 수행하는 방법에 대한 자세한 내용은 [Microsoft 문서](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions)를 참조하세요.  

## <a name="see-also"></a>참조
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>다음 단계
- 구독을 삭제하지 않고 변경해야 하나요?  [구독을 편집](edit-license.md)하는 방법 알아보기
- 특정 구독을 찾는 데 도움이 필요하면 [구독 검색](search-license.md)을 체크 아웃하세요.
- 모든 구독 목록을 만들어야 하나요?  [구독 내보내기](exporting-subscriptions.md)를 참조하세요.


