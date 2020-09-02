---
title: '방법: 워크플로 디자이너에서 워크플로에 주석 추가 Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d775c79cc7abdf6a66b1174ae625ca468f0764fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663459"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>방법: 워크플로 디자이너에서 워크플로에 주석 추가
더 크고 더 복잡한 워크플로를 쉽게 만들기 위해 [!INCLUDE[net_v45](../includes/net-v45-md.md)]를 사용하여 개발자는 디자이너에서 다음 형식의 항목에 주석을 추가할 수 있습니다.

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- <xref:System.Activities.Statements.FlowNode>에서 파생된 클래스

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> 주석 내용은 워크플로와 관련된 XAML 파일에 일반 텍스트로 저장되며 다른 사용자가 읽을 수 있습니다. 민감한 정보를 주석에 입력할 때는 주의하세요.

### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>디자이너의 활동에 주석 추가

1. Workflow designer의 workflow designer에서 항목을 마우스 오른쪽 단추로 클릭 하 고 주석, **주석 추가** **를 선택 합니다**.

2. 제공된 공란에 주석 텍스트를 추가합니다.

3. 항목은 주석 아이콘을 표시합니다. 주석 아이콘을 가리키면 주석 텍스트가 표시됩니다.

     ![주석을 표시하는 Sequence 활동](../workflow-designer/media/annotation.png "주석")

### <a name="displaying-an-annotation-in-an-activitys-designer"></a>활동 디자이너에 주석 표시

1. 활동 외부에 표시 되는 주석이 있는 활동 디자이너를 사용 하 여 주석 표시기의 **고정** 아이콘을 클릭 합니다.

2. 활동 디자이너에 주석이 표시됩니다. 아래의 스크린샷에서 활동 디자이너에 "워크플로에서 활동 시작" 주석이 표시됩니다.

     ![활동 디자이너에 표시되는 주석](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")

3. 활동 디자이너 외부에 주석을 표시 하려면 활동 디자이너에서 주석 영역을 마우스로 가리키고 **고정 해제** 아이콘을 클릭 합니다.

     ![활동 디자이너 외부에 표시되는 주석](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")

### <a name="showing-or-hiding-all-annotations"></a>모든 주석 표시 또는 숨기기

1. 주석이 있는 활동을 마우스 오른쪽 단추로 클릭합니다. **주석**, **모든 주석 표시**를 선택 합니다.

2. 활동 디자이너에 모든 주석이 표시됩니다.

3. 활동 디자이너 외부에 모든 주석을 표시 하려면 활동을 마우스 오른쪽 단추로 클릭 하 고 **주석**, **모든 주석 숨기기**를 선택 합니다.

### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>활동 주석 편집 또는 삭제

1. 주석이 있는 활동을 마우스 오른쪽 단추로 클릭합니다.

2. 주석 **,** **주석 편집** 또는 **주석 삭제**를 선택 합니다.

3. 편집 또는 삭제할 주석이 열립니다.

4. 모든 주석을 한 번에 삭제 하려면 워크플로 디자이너를 마우스 오른쪽 단추로 클릭 하 고 **주석**, **모든 주석 삭제**를 선택 합니다.

### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>변수 또는 인수에 대한 주석 추가, 편집 및 삭제

1. 변수 또는 인수를 마우스 오른쪽 단추로 클릭하고 주석 추가를 선택합니다.

2. 주석의 텍스트를 입력합니다. 변수 또는 인수에 주석 아이콘이 표시됩니다.

3. 주석이 있는 변수 또는 인수를 마우스 오른쪽 단추로 클릭합니다. 주석 편집을 선택합니다.

4. 편집할 주석이 열립니다.

5. 주석이 있는 변수 또는 인수를 마우스 오른쪽 단추로 클릭합니다. 주석 삭제를 선택합니다.

6. 주석이 삭제됩니다.