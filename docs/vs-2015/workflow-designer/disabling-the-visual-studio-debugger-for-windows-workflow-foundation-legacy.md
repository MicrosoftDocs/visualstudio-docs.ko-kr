---
title: Windows Workflow Foundation에 대해 디버거를 사용 하지 않도록 설정 (레거시) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eddd72d648e7349f51096a21131f38c2e370a277
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656780"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Visual Studio Debugger for Windows Workflow Foundation을 사용하지 않도록 설정(레거시)
이 항목에서는 레거시 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 [!INCLUDE[wf](../includes/wf-md.md)] 애플리케이션을 빌드할 때 구성 파일을 사용하여 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 디버거를 비활성화하는 방법에 대해 설명합니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

 기본적으로는 호스트 프로세스에 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]용 [!INCLUDE[wf](../includes/wf-md.md)] 디버거를 사용할 수 있습니다. 워크플로 디버깅을 사용 하지 않도록 설정 하려면 **\<switches>** **\<system.diagnostics>** 호스트 구성 파일의 섹션에 "DisableWorkflowDebugging" 항목 요소를 추가 하 여 명시적으로 해제 해야 합니다.

 다음 예제에서는 워크플로 디버깅을 사용하지 않도록 호스트 구성 파일을 수정하는 방법을 보여 줍니다.

```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>관련 항목
 [Windows Workflow Foundation에 대 한 Visual Studio 디버거 호출 (레거시)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [레거시 워크플로 디버깅](../workflow-designer/debugging-legacy-workflows.md)