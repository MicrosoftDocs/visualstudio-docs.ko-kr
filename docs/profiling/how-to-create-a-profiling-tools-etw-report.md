---
title: 방법 - 프로파일링 도구 ETW 보고서 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5fe610ea87c492e0bf562fe00145c3abaf76b8ef
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520629"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>방법: 프로파일링 도구 ETW 보고서 만들기
ETW(Windows용 이벤트 추적) 보고서에는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구의 성능 세션에서 기록된 ETW 이벤트가 나열됩니다. ETW 데이터는 이진(.*etl*) 파일에 수집됩니다. 이 보고서에 대한 자세한 내용은 [ETW(Windows용 이벤트 추적) 보고서](../profiling/event-tracing-for-windows-etw-report.md)를 참조하세요.

> [!NOTE]
> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]용 인터페이스에는 ETW 보고서를 표시할 수 없습니다.

- [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]용 인터페이스를 사용하여 ETW 데이터를 수집하는 방법에 대한 자세한 내용은 [방법: ETW(Windows용 이벤트 추적) 데이터 수집](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)을 참조하세요.

- 명령 프롬프트에서 ETW 데이터를 수집하는 방법에 대한 자세한 내용은 [VSPerfCmd](../profiling/vsperfcmd.md) 및 [이벤트](../profiling/events-vsperfcmd.md)를 참조하세요.

  **VSReport/summary:etw** 명령을 사용하여 ETW 보고서를 생성합니다. ETW 데이터를 포함하는 .*etl*은 프로파일링 데이터(.*vsp* 또는 .*vsps*) 파일과 동일한 디렉터리에 있어야 합니다. 기본적으로 이 보고서는 쉼표로 구분된 값(.*csv*) 파일로 생성됩니다. 자세한 내용은 [VSPerfReport](../profiling/vsperfreport.md)를 참조하세요.

### <a name="to-generate-an-etw-report"></a>ETW 보고서를 생성하려면

- **명령 프롬프트** 창에서 다음 명령줄을 입력합니다.

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**

    |항목|설명|
    |-|-|
    |*ToolsPath*|프로파일링 도구 유틸리티의 경로입니다. 자세한 내용은 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요.|
    |*VSPFile*|프로파일링 데이터(.*vsp* 또는 .*vsps*) 파일입니다. 전체 및 부분 경로를 사용할 수 있습니다.|
    |Xml|XML로 서식이 지정된 보고서를 생성합니다.|
