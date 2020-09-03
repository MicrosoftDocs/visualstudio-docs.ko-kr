---
title: 문서 수준 솔루션의 문서 보호
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c5f019907495c3cad3fddef501455aedf345bb2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71253801"
---
# <a name="document-protection-in-document-level-solutions"></a>문서 수준 솔루션의 문서 보호
  문서 수준 프로젝트에서 Word Microsoft Office의 보호 기능과 Microsoft Office Excel을 사용할 수 있습니다. 이러한 기능은 권한이 없는 사용자가 문서의 보호 된 부분을 변경할 수 없도록 차단 합니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Excel을 사용 하 여 통합 문서가 디자이너에서 열려 있는 동안 보호 기능을 설정 하거나 해제할 수 있습니다. Word를 사용 하 여 디자이너 외부 에서만 보호를 설정할 수 있습니다. 런타임에 Word와 Excel 모두에 대해 프로그래밍 방식으로 보호를 사용 하거나 사용 하지 않도록 설정할 수 있습니다.

 디자이너에 열려 있는 문서에서 문서 보호를 사용 하는 경우 모든 컨트롤이 **도구 상자** 에서 제거 되거나 사용할 수 없게 되 고 **데이터 소스** 창에서 문서로 항목을 끌 수 없습니다.

## <a name="serverdocument-and-protected-documents"></a>ServerDocument 및 보호 된 문서
 문서가 보호 되는 경우 문서 외부에서 데이터 캐시에 액세스할 수 없습니다. 클래스를 사용 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 하 여 보호 된 문서에 캐시 된 데이터를 검색 또는 조작 하거나 클래스의 다른 메서드를 사용할 수 없습니다 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> .

## <a name="word-document-protection-in-the-designer"></a>디자이너에서 Word 문서 보호
 Visual Studio에 열려 있는 동안 Word 문서 또는 템플릿에 보호를 추가 하는 경우 디자이너에서 보호 적용을 시작할 수 없습니다. 문서는 Visual Studio에서 열려 있는 동안 디자인 모드에 있으며, 보호 적용을 시작 하기 전에 실행 모드에 있어야 합니다.

 그러나 보호를 사용 하는 기존 Word 문서를 사용 하는 프로젝트를 만드는 경우이 문서는 디자이너에서 열 때 보호 됩니다. 문서의 보호 된 부분을 편집할 수는 없지만 코드 편집기에서 코드를 작성 하 여 문서를 자동화할 수 있습니다. 문서가 Visual Studio에서 열려 있는 동안 보호를 사용 하도록 설정한 경우에도 프로젝트를 빌드할 수 없습니다.

 문서를 편집 하 고 프로젝트를 빌드할 수 있도록 문서가 디자이너에서 열려 있는 동안 보호를 해제할 수 있습니다. 디버깅 하는 동안 디자이너에서 복사본에 대 한 보호를 해제할 수 없습니다. 디버깅 하는 동안 열리는 문서는 디자이너에 열려 있는 것과는 별개의 복사본입니다. 출력 복사본은 Visual Basic의 경우 *\bin* 디렉터리에 저장 되 고, c #의 경우 *\bin\debug* 디렉터리에 저장 됩니다.

 Visual Studio에서 프로젝트를 닫고 프로젝트 디렉터리에 있는 문서의 복사본을 열고 보호를 설정 하 여 디자이너에서 열리는 문서의 복사본에 대해 보호를 사용 하도록 설정할 수 있습니다.

## <a name="enforce-word-document-protection-on-build"></a>빌드 시 Word 문서 보호 적용
 Visual Studio는 빌드하는 동안 Word 문서 및 템플릿에 대 한 보호 적용을 시작 하 여 디버깅을 위해 문서를 열 때 보호를 사용 하도록 설정 합니다. 문서가 빈 암호로 보호 됩니다.

 빌드 중에 <xref:Microsoft.Office.Tools.Word.Document.Startup> 예외를 발생 시키거나 응용 프로그램의 동작을 변경할 수 있는 코드가 있을 경우이 코드를 올바르게 디버그할 수 있도록 보호를 사용 하도록 설정 합니다. 문서를 연 후 보호를 사용 하도록 설정 하는 경우 초기화 코드를 디버깅 하거나 테스트할 수 없습니다.

## <a name="setting-the-password"></a>암호 설정
 Visual Studio는 자동으로 보호를 사용 하도록 설정 하지만 기본적으로 암호를 제공 하지 않습니다. 문서 보호에 암호를 포함 하려면 솔루션을 배포 하기 전에 암호를 추가 해야 합니다. 암호를 추가 하면 권한 있는 사용자가 문서에서 보호를 제거할 수 있습니다. 암호가 없으면 보호를 쉽게 제거할 수 없습니다. 암호 설정에 대 한 자세한 내용은 특정 Office 응용 프로그램의 도움말을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: 프로그래밍 방식으로 문서 및 문서 부분 보호](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)
- [정보 권한 관리 및 관리 코드 확장 개요](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office 문서에 대 한 암호 보호](../vsto/password-protection-on-office-documents.md)
- [방법: 제한 된 권한으로 문서 뒤에 코드를 실행할 수 있도록 허용](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
