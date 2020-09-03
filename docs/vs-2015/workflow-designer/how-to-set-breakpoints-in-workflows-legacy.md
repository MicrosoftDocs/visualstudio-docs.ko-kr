---
title: '방법: 워크플로에 중단점 설정 (레거시) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- breakpoints, setting in workflows
- debugging, setting breakpoints in workflows
- debugging workflows, setting breakpoints
- workflows, setting breakpoints
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 182f28a2b21ae3129ce0d34fae97280ba0a07218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603591"
---
# <a name="how-to-set-breakpoints-in-workflows-legacy"></a>방법: 워크플로에 중단점 설정(레거시)
이 항목에서는 레거시 [!INCLUDE[wf](../includes/wf-md.md)]를 사용하여 빌드된 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 애플리케이션에 중단점을 설정하는 방법에 대해 설명합니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[wf2](../includes/wf2-md.md)] 애플리케이션이 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

 [!INCLUDE[wfd2](../includes/wfd2-md.md)]의 레거시 [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 사용하여 [!INCLUDE[wf2](../includes/wf2-md.md)] 애플리케이션을 빌드할 경우 Visual Studio에서 중단점을 설정할 때와 같이 C# 및 Visual Basic 코드에 중단점을 설정할 수 있습니다. 예상대로 설정한 각 중단점에서 워크플로 실행이 중지됩니다.

 중단점에는 *Pending*, *Bound*및 *Error*의 세 가지 상태가 있습니다. 중단점을 설정하면 중단점이 보류 중 상태가 되고 속이 빈 빨간색 아이콘으로 표시됩니다. 런타임 시 워크플로 유형을 로드했으면 중단점이 바인딩됨 상태가 되고 속이 찬 빨간색 아이콘으로 표시됩니다. 올바르지 않은 동작 이름처럼 잘못된 형식을 중단점에 대해 지정하면 오류 창이 나타납니다. 그래도 중단점 창에 중단점이 추가되기는 하지만 소문자 "x"로 표시됩니다.

 다음과 같은 방법으로 워크플로 디자인 화면에서 활동에 중단점을 설정할 수 있습니다.

- 활동을 마우스 오른쪽 단추로 클릭 하 고 **중단점 \ 중단점 삽입**을 선택 합니다.

- 활동을 선택하고 F9 키를 누릅니다.

- **디버그** 메뉴에서 **새 중단점** 을 선택 합니다.

     이 옵션을 사용하여 디버깅 중에 새 중단점을 설정할 수도 있습니다. 이렇게 하면 디버거가 중단점에서 중지됩니다.

    > [!NOTE]
    > 호출된 워크플로에는 중단점을 설정할 수 없습니다.

### <a name="to-set-a-breakpoint-using-the-new-breakpoint-option-on-the-debug-menu"></a>디버그 메뉴의 새 중단점 옵션을 사용하여 중단점을 설정하려면

1. **디버그** 메뉴에서 **새 중단점**을 선택 합니다.

2. **함수에서 중단을**클릭 합니다.

     **새 중단점** 대화 상자가 열립니다.

3. 구문을 사용 하 여 **함수** 텍스트 상자에 활동 이름을 지정 `QualifiedActivityId[:[FullClassName][:InstanceId]]` 합니다.

    > [!NOTE]
    > 필요에 따라 **함수** 텍스트 상자에 활동 이름을 사용 하는 대신 워크플로 활동의 절대 경로를 지정 하 여 중단점을 설정할 수 있습니다. 예를 들어 이름이 **WorkflowConsoleApplication1** 인 워크플로 솔루션과 **Delay1**이라는 활동을 사용 하는 **workflow1.vb** 라는 솔루션에 워크플로가 있다고 가정 합니다. 활동 이름 **Delay1** 을 사용 하거나 경로를 **Delay1: WorkflowConsoleApplication1** 또는 Delay1: WorkflowConsoleApplication1 **: {workflow1.vb}** 으로 지정할 수 있습니다.

4. **IntelliSense 사용** 확인란을 선택 하 여 함수 이름을 확인 합니다.

     이 확인란을 선택하지 않으면 중단점 이름 확인이 수행되지 않습니다.

5. **언어** 목록에서 **워크플로** 를 선택 합니다.

6. **확인**을 클릭합니다.

## <a name="see-also"></a>참고 항목
 [레거시 워크플로 디버깅](../workflow-designer/debugging-legacy-workflows.md) [Windows Workflow Foundation 용 Visual Studio 디버거 호출 (레거시)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)