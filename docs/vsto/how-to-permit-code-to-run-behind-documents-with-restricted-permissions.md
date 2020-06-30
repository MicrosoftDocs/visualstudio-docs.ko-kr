---
title: 제한 된 권한으로 문서 뒤에 코드를 실행할 수 있도록 허용
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 15cfb7ebf2f4f71e892820206f0dd1d006639992
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547513"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>방법: 제한 된 권한으로 문서 뒤에 코드를 실행할 수 있도록 허용
  Microsoft Office의 IRM (정보 Rights Management) 기능을 사용 하 여 문서나 통합 문서에 대 한 사용 권한을 제한할 수 있습니다. 기본적으로 제한 된 Microsoft Office Word 문서 또는 Microsoft Office Excel 통합 문서를 실행 하는 코드는 실행할 수 없습니다. 관리 코드 확장에서 개체 모델에 액세스할 수 있고 솔루션이 작동 하도록 기본값을 변경할 수 있습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 권한 설정을 변경 하려면 문서 또는 통합 문서 작성자 이거나 모든 권한이 있어야 합니다.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>제한 된 권한으로 문서 뒤에 코드를 실행 하도록 허용 하려면

1. Word 또는 Excel에서 문서 또는 통합 문서를 엽니다.

2. **파일** 탭을 클릭 하 고 **준비**, **사용 권한 제한**을 차례로 가리킨 다음 제한 된 **액세스**를 클릭 합니다.

   > [!NOTE]
   > 처음 사용 하는 경우 Windows Rights Management 클라이언트를 설치할지 묻는 메시지가 표시 됩니다. 클라이언트를 설치한 후 단계를 반복 해야 할 수 있습니다.

3. **권한** 대화 상자에서 **이 문서에 대 한 사용 권한 제한**을 선택 하 고 **기타 옵션**을 클릭 합니다.

4. **사용자에 대 한 추가 권한**에서 **프로그래밍 방식으로 콘텐츠 액세스**를 선택 합니다.

   Word 또는 Excel에서 개체 모델에 대 한 프로그래밍 방식 액세스를 허용 합니다.

## <a name="see-also"></a>참고 항목
- [정보 권한 관리 및 관리 코드 확장 개요](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [문서 수준 솔루션의 문서 보호](../vsto/document-protection-in-document-level-solutions.md)
- [Office 문서에 대 한 암호 보호](../vsto/password-protection-on-office-documents.md)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
