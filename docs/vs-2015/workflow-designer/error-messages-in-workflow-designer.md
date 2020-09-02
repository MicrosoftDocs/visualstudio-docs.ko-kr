---
title: 워크플로 디자이너의 오류 메시지 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d89c0dcad23a91ec6057311b9afde7d6d4702772
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656764"
---
# <a name="error-messages-in-workflow-designer"></a>Workflow Designer의 오류 메시지
이 항목은 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 작업 시 발생할 수 있는 오류 메시지 유형을 설명합니다.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>워크플로 디자이너에서 오류가 발생하는 경우
 [!INCLUDE[wfd2](../includes/wfd2-md.md)]의 오류는 다음 경우에 발생합니다.

1. 식에 오류가 있습니다.

2. 활동의 유효성 검사 제약 조건이 충족되지 않았습니다.

3. XAML 파일에 오류가 있어서 활동을 로드할 수 없습니다.

4. XAML 파일에 오류가 있어서 워크플로를 로드할 수 없습니다.

   잘못된 식과 충족되지 않은 유효성 검사 제약 조건으로도 워크플로가 작성됩니다. 워크플로는 작성되지만 런타임 시 <xref:System.Activities.InvalidWorkflowException>이 throw됩니다. XAML 파일에 오류가 있으면 빌드가 수행되지 않습니다.

   내에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 워크플로가 로드 되 면 해당 오류가 **오류 목록**표시 됩니다. 오류의 원본인 활동으로 이동 하려면 **오류 목록**에서 오류를 두 번 클릭 합니다.

### <a name="expression-errors"></a>식 오류
 잘못된 식에는 식 앞에 빨간색 원과 흰색 느낌표가 표시됩니다. 하지만 이 아이콘 위로 마우스를 가져가면 오류의 원인을 설명하는 도구 설명이 표시됩니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 내부에서 식을 클릭하면 오류 원인을 나타내는 줄(밑줄로 표시됨)을 볼 수 있습니다. 밑줄이 그어진 텍스트 위로 마우스를 가져가면 오류의 원인을 설명하는 도구 설명이 표시됩니다.

### <a name="activity-validation-errors"></a>활동 유효성 검사 오류
 활동의 유효성 검사 제약 조건이 충족되지 않은 경우 빨간색 원과 흰색 느낌표가 활동의 오른쪽 위 모서리에 나타납니다. 하지만 이 아이콘 위로 마우스를 가져가면 오류의 원인을 설명하는 도구 설명이 표시됩니다.

### <a name="xaml-load-errors"></a>XAML 로드 오류
 활동이 로드되지 못하면 "XAML에 오류가 발생하여 활동을 로드할 수 없습니다."라는 텍스트가 빨간색 상자에 나타납니다. 일반적으로 이 오류는 활동 형식을 확인할 수 없는 경우에 발생합니다. 빨간색 상자를 선택한 후 삭제하여 디자이너에서 잘못된 활동을 삭제할 수 있습니다.

### <a name="workflow-load-errors"></a>워크플로 로드 오류
 워크플로를 로드하지 못하는 경우 워크플로 로드 실패의 원인이 된 예외 정보와 함께 "워크플로 디자이너에서 문서에 문제가 발생했습니다."라는 텍스트가 디자이너 화면에 나타납니다. 일반적으로 이 오류는 XAML 파일의 구문을 분석할 수 없는 경우에 발생합니다.