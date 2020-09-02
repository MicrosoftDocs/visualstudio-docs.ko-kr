---
title: Office 문서에 대 한 암호 보호
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e3c9521389ce348a482f35ec95c9766edea49f5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62977902"
---
# <a name="password-protection-on-office-documents"></a>Office 문서에 대 한 암호 보호
  암호를 모르는 사람이 열 수 없도록 Microsoft Office Word 문서와 Microsoft Office Excel 통합 문서에 대 한 암호를 설정할 수 있습니다. 이 옵션을 **열기 암호**라고 합니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 **열려 있는 암호** 를 사용할 수 있는 기존 문서 및 통합 문서를 사용 하 여 문서 수준 프로젝트를 만들 수 있습니다. Visual Studio의 동작은 **열려 있는 암호** 를 사용할 수 있는 Word 및 Excel 문서에 대해 다릅니다.

 **Open에서 암호**를 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 Word 또는 Excel의 도움말을 참조 하세요.

## <a name="behavior-of-excel-and-word"></a>Excel 및 Word의 동작
 **열려 있는 암호** 를 사용 하 여 Visual Studio에서 excel 통합 문서를 열 때마다 excel에서 암호를 묻는 메시지를 표시 합니다. 솔루션을 빌드하면 빌드 중에 문서가 열리기 때문에 암호를 다시 입력 하 라는 메시지가 표시 됩니다.

 처음으로 사용 하도록 설정 된 **암호** 를 사용 하 여 Visual Studio에서 word 문서를 처음 열 때 암호를 묻는 메시지가 표시 됩니다. 암호를 입력 하 고 나 서 **열기의 암호가** 문서에서 제거 되 고 문서를 열 때 암호가 더 이상 필요 하지 않습니다. 솔루션의 문서를 열기 전에 암호를 요구 하도록 하려면 최종 빌드 후와 솔루션을 배포 하기 전에 **암호** 를 사용 하도록 설정 해야 합니다.

## <a name="see-also"></a>추가 정보
- [문서 수준 솔루션의 문서 보호](../vsto/document-protection-in-document-level-solutions.md)
- [정보 권한 관리 및 관리 코드 확장 개요](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [방법: 제한 된 권한으로 문서 뒤에 코드를 실행할 수 있도록 허용](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
