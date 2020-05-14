---
title: 관리자 포털에서 구독 편집 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/03/2020
ms.topic: conceptual
description: 관리자가 구독 할당을 편집하는 방법을 알아봅니다.
ms.openlocfilehash: a0f72bf6a6561060fd4eddcf2fc11f0f4cf97f15
ms.sourcegitcommit: 1b7412f1a5b039b2b294c6001013f399ea7aa5bc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82564227"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Visual Studio 구독 할당 편집
구독 관리자는 조직 내에서 개인에게 할당된 구독을 변경할 수 있습니다.  이 문서에서는 관리자가 변경할 수 있는 유형에 대해 설명하고 필요한 단계를 제공합니다.

   > [!NOTE]
   > Azure Active Directory 그룹을 통해 할당된 구독자의 구독 세부 정보를 변경해야 하는 경우 그룹에서 구독자를 제거하고 관리 포털에 개별적으로 추가해야 합니다.  

## <a name="change-subscriber-information"></a>구독자 정보 변경
구독자 정보를 편집하여 오류를 수정하거나 정보를 업데이트할 수 있습니다.

구독자를 편집하려면 마우스로 위를 가리킬 때 구독자의 이메일 주소 옆에 나타나는 줄임표(...)를 선택합니다. 드롭다운이 표시됩니다.  **편집**을 선택하여 구독자 세부 정보를 수정합니다. 
> [!div class="mx-imgBorder"]
> ![편집할 구독자 선택](_img/edit-license/select-subscriber.png)

구독자의 이름, 성, 구독 수준, 이메일 주소, 국가, 언어, 다운로드 및 참조 필드를 업데이트할 수 있습니다. 구독자 정보를 편집하고 **저장**을 클릭합니다.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>대량 편집을 사용하여 여러 구독자 편집


대량 편집 프로세스를 사용하여 여러 구독자를 한 번에 수정할 수 있습니다. 이 기능은 주로 회사 이메일 주소 변경을 수행하는 조직에서 사용되거나 조직에서 다운로드에 대한 액세스를 제한하도록 결정한 경우에 사용됩니다.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vkAF]

   > [!IMPORTANT]
   > 구독 수준(예: Enterprise, Professional 등) 및 구독 GUID는 대량 편집을 사용하여 변경할 수 없습니다.  사용자에게 특정 구독 GUID를 할당해야 하는 경우 구독 ID를 선택하여 사용자를 추가하는 프로세스를 사용하세요. 이러한 항목이 대량 편집 템플릿에서 변경된 상태에서 업로드를 시도하면 업로드가 실패합니다.

1. 여러 구독자를 한 번에 수정하려면 [구독자] 탭으로 이동합니다. 맨 위에 있는 리본에서 **대량 편집**을 클릭합니다.

2. 대량 편집은 Excel 템플릿을 사용하여 구독자 정보를 편집합니다. [대량 편집] 상자에서 **이 Excel 내보내기**를 클릭하여 모든 정보가 포함된 현재 구독자 목록을 다운로드합니다.
   > [!div class="mx-imgBorder"]
   > ![라이선스 편집 - 대량 편집 목록 내보내기](_img/edit-license/edit-license-bulk-edit-export.png)

3. 다음으로 파일을 쉽게 찾을 수 있고 업로드하기 전에 필요한 변경을 수행할 수 있도록 해당 파일을 로컬로 저장합니다. 업로드를 성공적으로 수행하려면 대량 편집 파일에서 **구독 수준 또는 구독 GUID를 편집하지 마세요**. 편집하면 업로드가 실패합니다.

4. Visual Studio 구독 관리 포털로 돌아가고, [대량 편집] 대화 상자에서 **찾아보기**를 클릭합니다. 저장한 Excel 파일을 선택하고 **확인**을 클릭합니다. 업로드 진행률이 화면에 표시됩니다.
   > [!div class="mx-imgBorder"]
   > ![라이선스 편집 - 대량 편집 파일 업로드](_img/edit-license/edit-license-bulk-file-upload1.png)

5. 파일이 업로드되면 성공했음을 알려주는 알림이 표시됩니다. 이 시점에서 편집한 내용이 구독자 정보에 반영됩니다.

## <a name="see-also"></a>참조
- [Visual Studio 설명서](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps 설명서](https://docs.microsoft.com/azure/devops/)
- [Azure 설명서](https://docs.microsoft.com/azure/)
- [Microsoft 365 설명서](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>다음 단계
- 특정 구독 ID를 할당해야 하나요? 구독 ID 할당을 체크 아웃합니다. 
- 특정 구독을 찾는 데 도움이 필요하면 [구독 검색](search-license.md)을 체크 아웃하세요.
- 모든 구독 목록을 만들어야 하나요?  [구독 내보내기](exporting-subscriptions.md)를 체크 아웃하세요.


