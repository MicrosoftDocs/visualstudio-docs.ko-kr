---
title: '방법: 이동 경로 탐색 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c01e48e6aa34513e57b373150c605cb0a7f5b18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659150"
---
# <a name="how-to-use-breadcrumb-navigation"></a>방법: 이동 경로 탐색 사용
[!INCLUDE[wfd1](../includes/wfd1-md.md)]에 표시되는 활동 집합을 변경하는 방법은 크게 세 가지입니다.

1. 두 번 클릭하여 자식 활동으로 드릴인합니다.

2. 이동 경로 탐색 막대의 단추를 클릭하여 상위 활동으로 이동합니다.

3. 현재 위치의 활동을 확장하거나 축소합니다.

### <a name="using-breadcrumb-navigation"></a>이동 경로 탐색 사용

1. [!INCLUDE[wfd2](../includes/wfd2-md.md)]의 활동을 두 번 클릭하여 루트 활동을 클릭한 활동으로 변경합니다. 그러면 클릭한 활동이 루트에서 완전히 확장되고 상위 항목이 이동 경로 탐색 막대에 표시됩니다. 이를 활동 드릴인/드릴아웃이라고도 합니다.

2. 현재 루트 활동의 상위 항목으로 이동하려면 이동 경로 탐색 막대에서 해당 활동을 클릭합니다.

### <a name="expanding-or-collapsing-an-activity-in-place"></a>현재 위치의 활동 확장 또는 축소

1. 활동의 갈매기형 펼침 단추를 클릭하면 현재 위치의 활동이 확장되거나 축소됩니다.

2. 이 단추를 클릭하여 확장 상태를 변경하면 확장의 새로운 상태가 XAML에 저장됩니다.

    > [!WARNING]
    > 일부 활동은 현재 위치에서 확장되지 않을 수도 있습니다. 현재 위치에서 활동을 확장할 수 없는 경우는 두 가지입니다. 즉, 활동의 부모가 현재 위치에서 자식을 확장하도록 허용하지 않는 경우(예: 순서도의 활동은 현재 위치에서 확장 불가능) 또는 활동 디자이너 자체에서 현재 위치에서의 확장을 허용하지 않는 경우입니다. [!INCLUDE[wfd2](../includes/wfd2-md.md)]에 포함된 활동 디자이너는 후자와 같이 작동하지 않지만 일부 사용자 지정 활동은 이와 같은 작동을 보일 수도 있습니다.

### <a name="expanding-all-or-collapsing-all-activities"></a>모든 활동 확장명 또는 축소

1. 사용자 인터페이스의 모두 **확장** 및 **모두 축소** 단추를 사용 하 여 현재 이동 경로 루트의 모든 활동을 확장 하거나 축소 합니다. 모두 확장 및 모두 축소는 전역 상태입니다. 즉, 이동 경로 탐색을 사용 하 여 루트 활동을 변경 하는 경우 **복원**을 클릭할 때까지 모두 확장 또는 모두 축소 상태가 지속 됩니다.

2. 모두 확장 또는 모두 축소 상태를 적용 한 후에는 표시 되는 **복원** 단추를 클릭 하 여 이전에 각 작업에 적용 된 상태를 볼 수 있습니다.

    > [!WARNING]
    > 와 같은 활동이 <xref:System.Activities.Statements.Flowchart> 현재 위치의 확장에서 옵트아웃 된 경우 **모두 확장** 및 **모두 축소** 단추와 연결 된 기능을 **순서도** 디자이너에서 사용할 수 없습니다. [!INCLUDE[crabout](../includes/crabout-md.md)]**순서도** 디자이너에서 [순서도](../workflow-designer/flowchart-activity-designer.md) 항목을 참조 하세요.

    > [!WARNING]
    > 모두 확장은 **Switch** 및 **TryCatch** activity designer에서 특수 한 효과를 가집니다. **모두 확장**을 클릭 하면 모든 스위치 사례와 모든 try/catch/finally 블록이 표시 됩니다. **복원** 또는 **모두 축소** 를 클릭 하면 이러한 디자이너가 기본 상태로 돌아갑니다. 여기서 개별 case/블록을 클릭 하 여 해당 내용을 볼 수 있습니다.