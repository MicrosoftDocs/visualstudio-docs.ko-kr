---
title: '방법: 코드를 실행 하지 않고 Office 솔루션 열기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d84515c2c3159b61b96f77555b23eef0df0ae961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543483"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>방법: 코드를 실행 하지 않고 Office 솔루션 열기
  관리 코드 확장을 사용 하 여 만든 Microsoft Office 솔루션은 최종 사용자의 Office 응용 프로그램의 보안 설정이 높음으로 설정 된 경우에도 실행 됩니다. .NET 어셈블리 코드 보안은 Microsoft Office가 아닌 Microsoft .NET 프레임 워크에서 관리 하기 때문입니다.

 그러나 코드를 실행 하지 않고 문서를 열 수 있는 경우가 있습니다. 예를 들어 문서를 열 때 실행 되는 코드는 콘텐츠를 변경할 수 있지만 코드가 변경 되기 전에 문서 모양을 업데이트 하려고 합니다. 또는 특정 정보를 포함 하는 문서를 다른 사람에 게 보낼 수 있으며, 코드를 실행 하 고 콘텐츠를 변경 하는 것을 원하지 않습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 어셈블리 코드를 실행 하지 않고 관리 코드 확장을 포함 하는 문서 또는 통합 문서를 여는 방법에는 여러 가지가 있습니다.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Shift 키를 사용 하 여 어셈블리를 무시 하려면

- 문서를 여는 동안 Word 및 Excel이 초기화 이벤트를 발생 **시 키 지** 않도록 하려면 **파일** 메뉴에서 문서 및 통합 문서를 엽니다.

    > [!NOTE]
    > **시작** 작업 창에서 문서 또는 통합 문서를 여는 경우 **shift 키** 를 누른 채 코드를 무시 하지 않습니다. 또한 SHIFT 키를 누르면 문서가 열린 후 이벤트가 발생 하는 것을 방지할 수 없습니다.

     이 메서드는 코드를 실행 하지 않고 문서를 변경 하 고 문서를 먼저 변경 하기 위해 문서를 열려는 경우에 유용 합니다.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>이름을 바꾸거나 제거 하 여 어셈블리를 무시 하려면

- 어셈블리가 있는 컴퓨터에 필요한 권한이 있는 경우 문서 또는 통합 문서에서 찾을 수 없도록 어셈블리의 이름을 바꾸거나 제거할 수 있습니다. 이로 인해 Office 문서를 열 때마다 오류가 발생 합니다.

     솔루션이 여러 사용자에 의해 사용 되는 경우이 방법을 사용 하면 솔루션을 실행할 수 없습니다. 이는 코드 또는 참조 된 서버에서 문제가 발견 되어 모든 사용자가 실행 하지 못하게 하려는 경우에 유용할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [Office 솔루션 보안](../vsto/securing-office-solutions.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
- [Office 솔루션의 응용 프로그램 및 배포 매니페스트](../vsto/application-and-deployment-manifests-in-office-solutions.md)
