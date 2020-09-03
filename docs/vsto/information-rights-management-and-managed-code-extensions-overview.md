---
title: 관리 코드 확장 & 정보 권한 관리
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 753f3d2da201c67cd86c697eccf7580596a40d6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68872058"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>정보 권한 관리 및 관리 코드 확장 개요
  Word 및 Microsoft Office Excel Microsoft Office는 권한이 없는 사용자가 중요 한 정보를 보거나 변경할 수 없도록 하는 기능인 IRM (정보 Rights Management)을 제공 합니다. 정보 Rights Management 작동 방법에 대 한 자세한 내용은 특정 Office 응용 프로그램의 도움말을 참조 하세요.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>제한 된 권한으로 문서 뒤에 코드 실행
 솔루션에 IRM을 사용 하는 문서 또는 통합 문서가 포함 되어 있는 경우 기본적으로 Word 및 Excel에서는 코드를 실행할 수 없습니다. 문서 작성자 이거나 모든 권한 액세스 권한이 있는 경우 솔루션의 작동을 위해 기본값을 변경할 수 있습니다. 자세한 내용은 [방법: 제한 된 권한으로 문서 뒤에 코드를 실행 하도록 허용](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)을 참조 하세요.

 IRM에서는를 사용 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 하 여 문서에 캐시 된 데이터를 검색 하거나 조작할 수 없습니다.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>최종 사용자가 관리 코드 확장을 사용 하는 문서에 대 한 사용 권한을 제한 합니다.
 솔루션의 문서 또는 통합 문서에 대 한 모든 권한을 가진 사용자는 IRM을 사용 하 여 사용 권한을 제한할 수 있습니다. 예를 들어, 회계 부서의 최종 사용자가 워크시트를 데이터베이스의 데이터로 자동으로 채우는 솔루션을 사용 하는 경우 해당 사용자는 자신의 학과에 속한 사용자 에게만 변경 액세스를 허용 하 고 다른 사용자에 게는 읽기 액세스 권한을 부여할 수 있습니다. 사용자가 제한 된 권한을 추가 하면 기본적으로 워크시트 뒤의 코드를 실행할 수 없으며 워크시트가 데이터로 채워지지 않습니다.

 문제를 해결 하려면 문서 또는 통합 문서에 대 한 모든 권한을 가진 사용자가 개체 모델에 대 한 프로그래밍 방식 액세스를 허용 하도록 기본 권한 설정을 변경 해야 합니다. 자세한 내용은 [방법: 제한 된 권한으로 문서 뒤에 코드를 실행 하도록 허용](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [문서 수준 솔루션의 문서 보호](../vsto/document-protection-in-document-level-solutions.md)
- [Office 문서에 대 한 암호 보호](../vsto/password-protection-on-office-documents.md)
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
