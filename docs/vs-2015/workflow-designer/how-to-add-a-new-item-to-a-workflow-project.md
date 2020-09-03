---
title: '방법: 워크플로 프로젝트에 새 항목 추가 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 004f079576b792fb76d596ee8ebac3f6f96f316e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656623"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>방법: 워크플로 프로젝트에 새 항목 추가
워크플로 프로젝트를 만든 후에는 워크플로 활동, 디자이너 및 다른 친숙한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 항목을 프로젝트에 추가할 수 있습니다.

 다음 표에서는 워크플로 프로젝트에 추가할 수 있는 [!INCLUDE[wf](../includes/wf-md.md)] 항목을 보여 줍니다.

|Name|설명|
|----------|-----------------|
|활동|다른 활동으로 구성할 활동입니다. 이 항목을 선택 하면 새 프로젝트의 **활동 라이브러리** 템플릿을 선택할 때와 동일한 XAML 파일이 프로젝트에 추가 됩니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 절차 [는 방법: 활동 라이브러리 만들기](../workflow-designer/how-to-create-an-activity-library.md)를 참조 하세요.|
|활동 디자이너|활동의 디자인 타임 환경을 사용자 지정할 디자이너입니다. 이 항목을 선택 하면 새 프로젝트에 대해 **Activity Designer 라이브러리** 템플릿을 선택할 때와 동일한 파일이 프로젝트에 추가 됩니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 절차 [는 방법: 활동 디자이너 라이브러리 만들기](../workflow-designer/how-to-create-an-activity-designer-library.md)를 참조 하세요.|
|Code 활동|코드로 작성된 실행 논리가 포함된 활동입니다. <xref:System.Activities.CodeActivity.Execute%2A> 메서드의 재정의가 포함된 소스 코드 파일이 이미 생성되어 있습니다.|
|WCF 워크플로 서비스|워크플로 활동을 사용하여 빌드된 [!INCLUDE[indigo2](../includes/indigo2-md.md)] 서비스입니다. 이 항목을 선택 하면 새 프로젝트에 **WCF 워크플로 서비스 응용 프로그램** 템플릿을 선택 하는 경우와 동일한 파일이 프로젝트에 추가 됩니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 절차 [는 방법: WCF 워크플로 서비스 응용 프로그램 만들기](../workflow-designer/how-to-create-a-wcf-workflow-service-application.md)를 참조 하세요.|

### <a name="to-add-a-new-item-to-a-workflow-project"></a>워크플로 프로젝트에 새 항목을 추가하려면

1. **프로젝트** 메뉴에서 **새 항목 추가**...를 클릭 합니다.

     **새 항목 추가** 대화 상자가 열립니다.

2. **설치 된 템플릿** 창에서 **워크플로** 그룹을 선택 합니다.

3. 네 항목 중 하나를 선택합니다. 앞의 표에 선택할 수 있는 항목이 나열되어 있습니다.

4. 대화 상자의 맨 아래에 있는 **이름** 상자에 항목에 대 한 적절 한 이름을 입력 합니다.

5. **추가** 를 클릭 하 여 현재 워크플로 프로젝트에 항목을 추가 합니다.

## <a name="see-also"></a>관련 항목
 [워크플로 프로젝트 만들기](../workflow-designer/creating-a-workflow-project.md)