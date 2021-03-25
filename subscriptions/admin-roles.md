---
title: Visual Studio 구독의 슈퍼 관리자 및 관리자 역할
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 03/19/2021
ms.topic: conceptual
description: 슈퍼 관리자 및 관리자 역할과 관리자를 할당하는 방법에 대해 알아봅니다.
ms.openlocfilehash: eca87026c681454925974f2e394737092c3e226d
ms.sourcegitcommit: d8d230791890cda532c263d04288dc13d2261c7f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104757596"
---
# <a name="super-admins-and-admins-for-visual-studio-subscription-agreements"></a>Visual Studio 정기가입 계약의 슈퍼 관리자 및 관리자

볼륨 라이선스 고객을 위한 새로운 Visual Studio 구독 관리 포털에는 서로 다른 두 가지 역할이 있습니다. 이 역할은 현재 VLSC에서 존재하는 데 사용되는 기본/통지 연락처 담당자 역할 및 구독 관리자 역할과 같습니다.

**슈퍼 관리자:** 조직이 처음 설정되면 기본적으로 기본 또는 통지 연락처 담당자가 슈퍼 관리자가 됩니다. 기본 또는 통지 연락처 담당자는 슈퍼 관리자 또는 관리자를 추가로 할당하도록 선택할 수 있습니다. 슈퍼 관리자는 구독자뿐만 아니라 다른 관리자도 추가하거나 제거할 수 있습니다. 시스템에 둘 이상의 슈퍼 관리자가 있는 경우 슈퍼 관리자는 보안을 위해 마지막 두 개를 제외하고 모두 삭제할 수 있습니다.

**관리자:** 슈퍼 관리자만 관리자를 할당할 수 있습니다. 관리자는 슈퍼 관리자가 계약에서 할당한 구독자만 관리할 수 있습니다.

관리자 관리 방법에 대한 데모를 시청하세요. 
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-admins"></a>관리자 할당
새 관리자를 할당하려면 다음을 수행합니다.
1. 구독을 구매한 계약의 슈퍼 관리자로 할당된 전자 메일 주소를 사용하여 https://manage.visualstudio.com 에 로그인합니다.
2. **관리자 관리** 탭을 클릭합니다.
3. **추가** 를 클릭합니다.
   > [!div class="mx-imgBorder"]
   > ![관리자 추가](_img/admin-roles/add-admins.png "관리자 관리 블레이드를 클릭한 다음 추가를 클릭하여 새 관리자를 할당합니다.")
4. 새 관리자의 정보로 양식을 완성합니다.  
   > [!div class="mx-imgBorder"]
   > ![관리자 추가 양식](_img/admin-roles/add-form.png "새 관리자의 로그인 정보를 입력하고 이 관리자를 슈퍼 관리자로 지정할지 여부를 선택합니다.  그런 다음 추가를 클릭합니다.")

   > [!NOTE]
   > 이 관리자가 추가 관리자를 할당할 수 있도록 하려면 **슈퍼 관리자** 상자를 선택해야 합니다.

5. **추가** 를 클릭하여 새 관리자를 할당한 후에는 포털에 로그인하도록 초대하는 전자 메일이 수신됩니다.  

## <a name="resources"></a>리소스
- [Visual Studio 관리 및 구독 지원](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>참고 항목
- [Visual Studio 설명서](/visualstudio/)
- [Azure DevOps 설명서](/azure/devops/)
- [Azure 설명서](/azure/)
- [Microsoft 365 설명서](/microsoft-365/)



## <a name="next-steps"></a>다음 단계
- [구독을 할당](assign-license.md)하는 방법 알아보기
- [구독 혜택](https://visualstudio.microsoft.com/vs/benefits/)의 전체 범위에 대한 자세한 정보
- [계약 기본 설정 지정](admin-prefs.md)