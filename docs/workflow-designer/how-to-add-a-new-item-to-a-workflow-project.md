---
title: '워크플로 디자이너: 워크플로 프로젝트에 새 항목 추가'
ms.date: 06/25/2018
ms.topic: how-to
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53737eb421f4194b00354899e373441ff0a97227
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814618"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>방법: 워크플로 프로젝트에 새 항목 추가

워크플로 프로젝트를 만든 후에는 워크플로 활동, 디자이너 및 기타 친숙 한 Visual Studio 항목을 프로젝트에 추가할 수 있습니다.

다음 표에서는 워크플로 프로젝트에 추가할 수 있는 WF (Windows Workflow Foundation) 항목을 보여 줍니다.

| Name | 설명 |
|-| - |
| 활동 | 다른 활동으로 구성할 활동입니다. 이 항목을 선택 하면 새 프로젝트의 **활동 라이브러리** 템플릿을 선택할 때와 동일한 XAML 파일이 프로젝트에 추가 됩니다. 이 절차에 대 한 자세한 내용은 [워크플로 프로젝트 만들기](creating-a-workflow-project.md)를 참조 하세요. |
| 활동 디자이너 | 활동의 디자인 타임 환경을 사용자 지정할 디자이너입니다. 이 항목을 선택 하면 새 프로젝트에 대해 **Activity Designer 라이브러리** 템플릿을 선택할 때와 동일한 파일이 프로젝트에 추가 됩니다. |
| Code 활동 | 코드로 작성된 실행 논리가 포함된 활동입니다. <xref:System.Activities.CodeActivity.Execute%2A> 메서드의 재정의가 포함된 소스 코드 파일이 이미 생성되어 있습니다. |
| WCF 워크플로 서비스 | 워크플로 활동을 사용하여 빌드된 [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] 서비스입니다. 이 항목을 선택 하면 새 프로젝트에 **WCF 워크플로 서비스 응용 프로그램** 템플릿을 선택 하는 경우와 동일한 파일이 프로젝트에 추가 됩니다. 이 절차에 대 한 자세한 내용은 [방법: WCF 워크플로 서비스 응용 프로그램 만들기](creating-a-workflow-project.md)를 참조 하세요. |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>워크플로 프로젝트에 새 항목을 추가하려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 선택합니다.

   **새 항목 추가** 대화 상자가 열립니다.

1. 왼쪽 창에서 **워크플로** 범주를 선택한 후 워크플로 항목 템플릿을 선택 합니다.

   > [!NOTE]
   > **워크플로** 범주가 표시 되지 않으면 먼저 Visual Studio의 **Windows Workflow Foundation** 구성 요소를 설치 합니다. 자세한 지침은 [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)를 참조 하세요.

1. 대화 상자의 맨 아래에 있는 **이름** 상자에 항목의 이름을 입력 합니다.

1. **추가** 를 선택 하 여 프로젝트에 항목을 추가 합니다.

## <a name="see-also"></a>참고 항목

- [워크플로 프로젝트 만들기](../workflow-designer/creating-a-workflow-project.md)
