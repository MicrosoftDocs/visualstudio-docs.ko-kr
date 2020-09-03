---
title: '방법: 문서에 관리 코드 확장명 연결'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f44b153ac7d55704ba649a7dc09860518a5e76b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547526"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>방법: 문서에 관리 코드 확장명 연결
  기존 Microsoft Office Word 문서 또는 Microsoft Office Excel 통합 문서에 사용자 지정 어셈블리를 연결할 수 있습니다. 문서 또는 통합 문서는 Visual Studio의 Microsoft Office 프로젝트 및 개발 도구에서 지원 되는 모든 파일 형식일 수 있습니다. 자세한 내용은 [문서 수준 사용자 지정의 아키텍처](../vsto/architecture-of-document-level-customizations.md)를 참조 하세요.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Word 또는 Excel 문서에 사용자 지정을 연결 하려면 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 클래스의 메서드를 사용 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 합니다. <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>클래스가 Microsoft Office 설치 되어 있지 않은 컴퓨터에서 실행 되도록 설계 되었기 때문에 Microsoft Office 개발 (예: 콘솔 또는 Windows Forms 응용 프로그램)과 직접적으로 관련 되지 않은 솔루션에서이 방법을 사용할 수 있습니다.

> [!NOTE]
> 코드에 지정 된 문서에 없는 컨트롤이 필요한 경우 사용자 지정을 로드 하지 못합니다.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>문서에 관리 코드 확장을 연결 하려면

1. 콘솔 응용 프로그램 또는 Windows Forms 프로젝트와 같이 Microsoft Office 필요 없는 프로젝트에서 *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* 및 *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* 어셈블리에 대 한 참조를 추가 합니다.

2. 다음 **Imports** 또는 **using** 문을 코드 파일의 맨 위에 추가 합니다.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. 정적 메서드를 호출 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 합니다.

     다음 코드 예제에서는 오버 로드를 사용 합니다 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> . 이 오버 로드는 문서의 전체 경로와 <xref:System.Uri> 문서에 첨부할 사용자 지정에 대 한 배포 매니페스트의 위치를 지정 하는를 사용 합니다. 이 예에서는 **WordDocument1.docx** 이라는 Word 문서가 바탕 화면에 있고 배포 매니페스트가 바탕 화면에도 있는 **Publish** 라는 폴더에 있는 것으로 가정 합니다.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. 프로젝트를 빌드하고 사용자 지정을 연결 하려는 컴퓨터에서 응용 프로그램을 실행 합니다. 컴퓨터에 Visual Studio 2010 Tools for Office Runtime이 설치 되어 있어야 합니다.

## <a name="see-also"></a>참조
- [ServerDocument 클래스를 사용 하 여 서버에서 문서 관리](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [방법: 문서에서 관리 코드 확장명 제거](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Office 솔루션의 응용 프로그램 및 배포 매니페스트](../vsto/application-and-deployment-manifests-in-office-solutions.md)
