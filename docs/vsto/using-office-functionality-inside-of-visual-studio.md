---
title: Visual Studio 내에서 Office 기능 사용
description: 문서 수준 프로젝트의 문서 및 연결 된 응용 프로그램을 Visual Studio 내에서 호스트 하 여 문서와 직접 작업할 수 있는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 258ea4529a558c91eb115b82b35def4ca4ab6561
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838245"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Visual Studio 내에서 Office 기능 사용
  문서 수준 프로젝트를 만들 때 문서와 연결 된 응용 프로그램은 Visual Studio 내에서 호스팅되므로 문서를 직접 디자인 하 고 작업할 수 있습니다. Microsoft Office 응용 프로그램이 Visual Studio에서 열려 있는 경우 일반적으로 정상적으로 작동 합니다. 그러나 응용 프로그램의 기능 중 일부는 다르거나 액세스할 수 없습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>문서 보호
 Word 및 Microsoft Office Excel Microsoft Office 프로젝트에서 사용할 수 있는 문서 보호 기능을 제공 합니다. 그러나 문서가 Visual Studio에서 열려 있는 동안 문서 보호가 사용 되도록 설정 된 경우에는 일부 디자인을 변경 하지 못할 수 있습니다. 자세한 내용은 [문서 수준 솔루션의 문서 보호](../vsto/document-protection-in-document-level-solutions.md)를 참조 하세요.

## <a name="information-rights-management"></a>정보 권한 관리
 IRM (정보 Rights Management)은 Microsoft Office Word 및 Microsoft Office Excel에서 사용할 수 있습니다. IRM을 통해 권한이 없는 사용자가 중요 한 정보를 보거나 변경할 수 없도록 방지할 수 있습니다. 그러나 IRM은 코드가 실행 되지 않도록 할 수도 있습니다. 자세한 내용은 [정보 권한 관리 및 관리 코드 확장 개요](../vsto/information-rights-management-and-managed-code-extensions-overview.md)를 참조 하세요.

## <a name="password-protection"></a>암호 보호
 Word 문서 및 Microsoft Office Excel 통합 문서를 Microsoft Office 암호를 모르는 사람이 열 수 없도록 설정할 수 있습니다. 암호 보호는 Word와 Excel에서 다르게 처리 되며 개발 프로세스에 영향을 줄 수 있습니다. 자세한 내용은 [Office 문서의 암호 보호](../vsto/password-protection-on-office-documents.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [문서 수준 솔루션의 문서 보호](../vsto/document-protection-in-document-level-solutions.md)
- [정보 권한 관리 및 관리 코드 확장 개요](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office 문서에 대 한 암호 보호](../vsto/password-protection-on-office-documents.md)
- [방법: 코드를 실행 하지 않고 Office 솔루션 열기](../vsto/how-to-open-office-solutions-without-running-code.md)
