---
title: 성능 도구 데이터 저장 및 내보내기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3be6d5d732e5cbb2050c68ac8c7db722c3f709f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841579"
---
# <a name="saving-and-exporting-performance-tools-data"></a>성능 도구 데이터 저장 및 내보내기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 성능 데이터 파일을 저장하고 내보내는 방법을 설명합니다.  
  
## <a name="how-to-save-performance-data-files-as-analyzed-report-files"></a><a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> 방법: 성능 데이터 파일을 분석 보고서 파일로 저장  
 프로파일링 데이터(.vsp) 파일의 필터링되거나 필터링되지 않은 뷰를 분석 보고서(.vsps) 파일로 저장할 수 있습니다. 분석 보고서 파일은 보고서 뷰 창에서 볼 수 있으며 .vsp 원본 파일보다 훨씬 작습니다. 하지만 .vsps 파일의 데이터에 필터를 적용할 수 없습니다. IDE(통합 개발 환경)에서 파일을 열지 않고 성능 탐색기에서 분석 보고서를 만들거나 .vsp 파일을 열어서 필터링한 다음 결과를 저장할 수 있습니다.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>성능 탐색기에서 분석 성능 보고서를 저장하려면  
  
1. **보고서**에서 분석할 프로파일링 데이터 파일을 마우스 오른쪽 단추로 클릭한 다음 **분석 결과 저장**을 클릭합니다.  
  
2. **분석 데이터 저장** 대화 상자에서 디렉터리를 지정하고 파일 이름을 입력합니다.  
  
3. **저장**을 클릭합니다.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>보고서 뷰 창에서 분석 성능 보고서를 저장하려면  
  
1. 보고서 뷰 창에서 프로파일링 데이터(.vsp) 파일을 엽니다.  
  
2. (선택적) 데이터에 필터를 적용합니다. 자세한 내용은 [성능 보고서 뷰 필터](../profiling/performance-report-view-filter.md)를 참조 하세요.  
  
3. 보고서 뷰 창 도구 모음에서 **분석 결과 저장** 을 클릭합니다.  
  
4. **분석 데이터 저장** 대화 상자에서 디렉터리를 지정하고 파일 이름을 입력합니다.  
  
5. **저장**을 클릭합니다.  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>방법: 프로파일링 도구 보고서를 .Xml 또는 .Csv 파일로 내보내기  
 .vsp 파일 도는 .vsps 프로파일링 데이터 파일에서 하나 이상의 보고서 뷰를 쉼표로 분리된 파일 또는 XML 파일로 내보낼 수 있습니다. 내보내기 전에 보고서 뷰 창에서 데이터를 필터링하거나 **성능 탐색기** 창에서 전체 데이터 파일의 보고서 뷰를 내보낼 수 있습니다.  
  
> [!NOTE]
> 보고서 뷰 창에서 선택한 행을 복사하여 탭으로 구분된 값으로 붙여 넣을 수도 있습니다.  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>성능 탐색기 창에서 성능 보고서를 내보내려면  
  
1. **성능 탐색기**에서 보고서를 선택한 다음 마우스 오른쪽 단추를 클릭하고 **내보내기**를 선택합니다.  
  
     **보고서 내보내기** 대화 상자가 나타납니다.  
  
2. 내보낼 보고서 뷰를 선택합니다.  
  
3. **Prefix report with**(보고서 접두사)에서 보고서 이름에 추가할 접두사를 지정합니다.  
  
4. **내보낸 보고서 위치**에서 디렉터리를 지정합니다.  
  
5. **내보낸 보고서 형식**에서 (쉼표로 구분) (* .csv) 또는 xml 데이터 (.xml)를 선택 \* 합니다.  
  
6. **내보내기**를 클릭합니다.  
  
     각 보고서 뷰는 \<prefix>_\<report view name>이라는 별도의 파일에 저장됩니다.\<csv&#124;xml>  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>보고서 뷰 창에서 성능 보고서를 내보내려면  
  
1. 보고서 뷰 창에서 .vsp 파일을 엽니다.  
  
2. (선택적) 데이터에 필터를 적용합니다. 자세한 내용은 [성능 보고서 뷰 필터](../profiling/performance-report-view-filter.md)를 참조 하세요.  
  
3. 보고서 뷰 창 도구 모음에서 **보고서 내보내기** 를 클릭합니다.  
  
4. 내보낼 보고서 뷰를 선택합니다.  
  
5. **Prefix report with**(보고서 접두사)에서 보고서 이름에 추가할 접두사를 지정합니다.  
  
6. **내보낸 보고서 위치**에서 디렉터리를 지정합니다.  
  
7. **내보낸 보고서 형식**에서 (쉼표로 구분) (* .csv) 또는 xml 데이터 (.xml)를 선택 \* 합니다.  
  
8. **내보내기**를 클릭합니다.  
  
     각 보고서 뷰는 \<prefix>_\<report view name>이라는 별도의 파일에 저장됩니다.\<csv&#124;xml>  
  
## <a name="see-also"></a>참고 항목  
 [성능 탐색기](../profiling/performance-explorer.md)   
 [성능 도구 데이터 분석](../profiling/analyzing-performance-tools-data.md)   
 [성능 데이터 파일 비교](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
