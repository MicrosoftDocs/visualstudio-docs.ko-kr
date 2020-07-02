---
title: '방법: 문서에서 관리 코드 확장명 제거'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b4f5cb3098289463cea7e650332583ec7b12258
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541312"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>방법: 문서에서 관리 코드 확장명 제거
  Microsoft Office Word 또는 Microsoft Office Excel에 대 한 문서 수준 사용자 지정의 일부인 문서 또는 통합 문서에서 프로그래밍 방식으로 사용자 지정 어셈블리를 제거할 수 있습니다. 그러면 사용자가 문서를 열고 내용을 볼 수 있지만 문서에 추가 하는 사용자 지정 UI (사용자 인터페이스)는 표시 되지 않으며 코드가 실행 되지 않습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 에서 제공 하는 메서드 중 하나를 사용 하 여 사용자 지정 어셈블리를 제거할 수 있습니다 `RemoveCustomization` [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . 런타임에 사용자 지정을 제거할지, 즉 Word 문서 또는 Excel 통합 문서가 열려 있는 동안 사용자 지정에서 코드를 실행 하 여 사용자 지정을 제거할지, 아니면 닫혀 있는 문서 또는 Microsoft Office 설치 되지 않은 서버에 있는 문서에서 사용자 지정을 제거할지를 결정 합니다.

## <a name="to-remove-the-customization-assembly-at-run-time"></a>런타임에 사용자 지정 어셈블리를 제거 하려면

1. 사용자 지정 코드에서 <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> 메서드 (Word의 경우) 또는 <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> 메서드 (Excel의 경우)를 호출 합니다. 이 메서드는 사용자 지정이 더 이상 필요 하지 않은 경우에만 호출 해야 합니다.

     코드에서이 메서드를 호출 하는 위치는 사용자 지정이 사용 되는 방식에 따라 달라 집니다. 예를 들어 고객이 사용자 지정 기능을 사용 하는 경우 사용자 지정이 아닌 문서 자체에만 필요한 다른 클라이언트에 문서를 보낼 준비가 될 때까지 사용자 지정 기능을 사용 하는 경우 고객이 해당 기능을 클릭할 때를 호출 하는 UI를 제공할 수 있습니다 `RemoveCustomization` . 또는 사용자 지정이 처음 열 때 데이터로 문서를 채우면 사용자 지정에서 고객이 직접 액세스 하는 다른 기능을 제공 하지 않는 경우 사용자 지정이 문서 초기화를 완료 하는 즉시 RemoveCustomization을 호출할 수 있습니다.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>닫힌 문서 또는 서버의 문서에서 사용자 지정 어셈블리를 제거 하려면

1. 콘솔 응용 프로그램 또는 Windows Forms 프로젝트와 같이 Microsoft Office 필요 없는 프로젝트에서 *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* 어셈블리에 대 한 참조를 추가 합니다.

2. 다음 **Imports** 또는 **using** 문을 코드 파일의 맨 위에 추가 합니다.

     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]

3. <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>클래스의 정적 메서드를 호출 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 하 고 매개 변수에 대 한 솔루션 문서 경로를 지정 합니다.

     다음 코드 예제에서는 데스크톱에 있는 *WordDocument1.docx* 이라는 문서에서 사용자 지정을 제거 하는 것으로 가정 합니다.

     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]

4. 프로젝트를 빌드하고 사용자 지정을 제거 하려는 컴퓨터에서 응용 프로그램을 실행 합니다. 컴퓨터에 Visual Studio 2010 Tools for Office runtime이 설치 되어 있어야 합니다.

## <a name="see-also"></a>참고 항목
- [ServerDocument 클래스를 사용 하 여 서버에서 문서 관리](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [방법: 문서에 관리 코드 확장명 연결](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
