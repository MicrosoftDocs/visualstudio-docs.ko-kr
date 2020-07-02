---
title: '방법: Office 솔루션에 서명'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 23afc171fd97620b3e6801b8d199da6890198d8b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545758"
---
# <a name="how-to-sign-office-solutions"></a>방법: Office 솔루션에 서명
  솔루션에 서명 하는 경우 인증서를 증명 정보로 사용 하 여 솔루션에 신뢰를 부여할 수 있습니다. 여러 솔루션에 동일한 인증서를 사용할 수 있으며, 모든 솔루션은 추가 보안 정책 업데이트 없이 신뢰 됩니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 매니페스트 생성 및 편집 도구 (*mage.exe* 및 *mageui.exe*)를 사용 하 여 응용 프로그램 및 배포 매니페스트를 수동으로 편집 하는 경우에는 매니페스트를 사용 하기 전에 다시 서명 해야 합니다. 자세한 내용은 [방법: 응용 프로그램 및 배포 매니페스트 다시 서명](../deployment/how-to-re-sign-application-and-deployment-manifests.md)을 참조 하세요.

## <a name="sign-by-using-a-certificate"></a>인증서를 사용 하 여 서명
 인증서는 솔루션 게시자의 고유 키와 id를 포함 하는 파일입니다. 인증 기관에서 인증서를 구입 하거나 자체 인증서를 만들고 인증 기관에서 해당 인증서를 서명할 수 있습니다.

 Visual Studio는 디버깅을 사용 하도록 설정 하기 위해 임시 인증서를 사용 하 여 Office 솔루션에 서명 합니다. 배포 된 솔루션에서 임시 인증서를 증거로 사용 하면 안 됩니다.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>인증서를 사용 하 여 Office 솔루션에 서명 하려면

1. **프로젝트** 메뉴에서 _SolutionName_**속성**을 클릭 합니다.

2. **시그니처** 탭을 클릭합니다.

3. **ClickOnce 매니페스트 서명을**선택 합니다.

4. **저장소에서 선택** 을 클릭 하거나 **파일에서를 선택** 하 고 인증서로 이동 하 여 인증서를 찾습니다.

5. 올바른 인증서가 사용 되 고 있는지 확인 하려면 **자세한 정보** 를 클릭 하 여 인증서 정보를 확인 합니다.

## <a name="see-also"></a>참고 항목

- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [Office 솔루션에 신뢰 부여](../vsto/granting-trust-to-office-solutions.md)
- [프로젝트 디자이너, 서명 페이지](../ide/reference/signing-page-project-designer.md)
