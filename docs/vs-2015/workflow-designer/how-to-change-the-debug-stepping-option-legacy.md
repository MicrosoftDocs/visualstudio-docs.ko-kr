---
title: '방법: 단계별 디버깅 옵션 변경 (레거시) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5126b3dc45d33471080ae154e06f4a327e21fef7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663445"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>방법: 단계별 디버깅 옵션 변경(레거시)
이 항목에서는 [!INCLUDE[wf](../includes/wf-md.md)]에서 동시 동작이 있는 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 애플리케이션의 단계별 디버깅 옵션을 변경하는 방법에 대해 설명합니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

 **ParallelActivity** 또는 **ConditionedActivityGroup**와 같이 동시에 실행 되는 레거시 작업을 디버깅 하는 경우 두 가지 옵션 중 하나를 사용 하 여 코드를 단계별로 실행할 수 있습니다.

 레거시 워크플로 프로젝트에서 단계별 디버깅 옵션을 변경하려면 다음 단계를 따르세요.

## <a name="procedures"></a>프로시저

#### <a name="to-change-the-debug-stepping-option"></a>디버그 단계별 옵션을 변경하려면

1. Visual Studio를 시작합니다.

2. 기존 레거시 워크플로 프로젝트를 열거나 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 하며 동시 활동을 사용하는 새 프로젝트를 만듭니다.

3. 레거시의 **워크플로** 메뉴에서 [!INCLUDE[wfd2](../includes/wfd2-md.md)] **디버그**를 가리킨 다음 **단계별 옵션**을 가리킵니다.

4. **인스턴스** 또는 **분기**중 하나를 선택 합니다.

## <a name="see-also"></a>관련 항목
 [레거시 워크플로 디버깅](../workflow-designer/debugging-legacy-workflows.md) [단계별 실행 옵션 (레거시)](../workflow-designer/debug-stepping-options-legacy.md)