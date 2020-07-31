---
title: Visual Studio 구독자에게 특정 GUID 할당 | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: 관리자가 구독자에 대해 특정 구독 GUID를 지정할 수 있는 방법 알아보기
ms.openlocfilehash: e6c50239721d810964f2b95e0ec3509999d2f4d5
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235188"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Visual Studio 구독 관리 포털에서 특정 구독 할당

관리자는 이제 Visual Studio 구독 관리 포털을 사용하여 개별 구독자에게 특정 구독을 할당할 수 있습니다.  이 기능은 조직에 단기적으로 구독에 액세스해야 하는 임시 직원 또는 공급업체가 있는 경우에 유용할 수 있습니다.  관리자는 이미 부분적으로 사용된 구독은 할당하고 새로운 구독은 장기적인 사용을 위해 남겨 둘 수 있습니다.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>사용자에게 특정 구독 GUID 할당

특정 구독을 개인에게 할당하는 프로세스는 2개의 기존 관리 프로세스를 활용하여 특정 구독 GUID(Globally Unique Identifier)를 개별 사용자에게 할당합니다.  이는 현재 구독 및 할당의 목록을 내보내고, 이 목록을 사용해 할당할 특정 GUID를 식별하고, 대량 추가 프로세스를 사용해 새로운 할당을 업로드하는 3단계 프로세스입니다.

### <a name="export-your-subscriptions-information"></a>구독 정보 내보내기

내보내기를 수행하려면
1. [관리 포털](https://manage.visualstudio.com)에 로그인합니다.
2. **내보내기** 탭을 선택하면 파일이 로컬 컴퓨터에 다운로드됩니다. 파일에는 내보내기 날짜뿐만 아니라 사용자 구독을 포함하는 계약의 이름이 포함됩니다.
> [!div class="mx-imgBorder"]
> ![구독자 내보내기](_img/exporting-subscriptions/exporting-subscriptions.png "할당된 구독의 목록과 구독자 정보를 저장하려면 내보내기를 클릭합니다.")

### <a name="identify-the-guids-you-want-to-assign"></a>할당할 GUID 식별

이전에 내보내기 도구를 사용한 적이 있다면 생성된 스프레드시트에 새 필드가 추가된 것이 확인될 것입니다.  이 필드는 각 구독의 상태와 사용자에게 할당할 구독을 결정하는 데 도움이 됩니다.  

- **구독 상태**: 이 필드에는 “할당됨” 또는 “할당되지 않음”이 표시됩니다.  구독 상태가 “할당됨”인 경우에는 이름, 전자 메일과 같은 사용자 정보도 구독에 연결되어 있습니다. 
- **사용 상태**: 사용 상태는 구독이 사용자에게 할당된 적이 없음을 의미하는 “신규” 또는 특정 시점에 사용자에 할당되었음을 의미하는 “사용됨”입니다.  

이러한 필드의 값을 스프레드시트의 다른 정보와 함께 사용하여 개별 사용자에게 할당할 구독을 결정할 수 있습니다. Excel에서 필터를 적용하여 상태, 구독 수준, 만료 날짜 등을 기준으로 목록의 범위를 좁힐 수 있습니다. 

### <a name="upload-your-new-assignments"></a>새 할당 업로드

마지막 단계는 **대량 추가** 템플릿을 다운로드하고 할당하려는 구독에 대한 필수 정보를 입력한 후 템플릿을 업로드하는 것입니다.  이 프로세스에 대한 전체 설명은 [여러 사용자 추가](assign-license-bulk.md) 문서를 참조하세요.  

> [!IMPORTANT]
> 성공적으로 업로드하려면 다음을 확인하세요.
> - **일괄 추가**를 선택할 경우 대화 상자에서 연결된 템플릿을 사용해야 합니다.  로컬에 저장된 템플릿 복사본은 필수 필드를 일부 포함하고 있지 않을 수 있으므로 사용하지 마세요.  이전 템플릿을 사용하면 업로드에 실패합니다. 
> - 템플릿에서 **필수**으로 표시된 모든 필드를 완료합니다.
> - **오류 메시지** 열에 나열된 오류가 없습니다.
> - 각 GUID는 템플릿에서 한 번만 사용됩니다. 
> - 템플릿의 구독 수준이 내보낸 목록에 나오는 GUID의 구독과 일치합니다. 
> - GUID가 내보낸 목록에 있는 다른 사용자에게 아직 할당되지 않았습니다. 

## <a name="frequently-asked-questions"></a>질문과 대답
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>Q: 개별 사용자에게 현재 할당된 구독을 변경하려면 어떻게 하나요?
A: 사용자에게 할당된 GUID를 변경하려면 먼저 사용자에 대한 구독을 삭제해야 합니다.  자세한 내용은 [구독 삭제](delete-license.md) 문서를 참조하세요.  사용자에 대한 구독을 삭제한 후에는 위에서 설명하는 프로세스를 사용해 목록을 내보내고 새 구독 정보를 업로드합니다.  

## <a name="see-also"></a>참조
- [Visual Studio 설명서](/visualstudio/)
- [Azure DevOps 설명서](/azure/devops/)
- [Azure 설명서](/azure/)
- [Microsoft 365 설명서](/microsoft-365/)

## <a name="next-steps"></a>다음 단계
이제 사용자에게 구독을 할당했으므로 다른 관리 작업을 수행하는 방법을 알아보세요.
- [개별 구독 할당](assign-license.md)
- [여러 구독 할당](assign-license-bulk.md)
- [구독 편집](edit-license.md)
- [구독 삭제](delete-license.md)
- [최대 사용량 확인](maximum-usage.md)


