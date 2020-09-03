---
title: .NET 메모리 데이터 뷰 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method views
- profiling tools,.NET memory profiling views
ms.assetid: 79184d8e-769b-4ace-be2b-521147772081
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d31213dc970fa7cb28c4d4620c6731692db83d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185236"
---
# <a name="net-memory-data-views"></a>.NET 메모리 데이터 뷰
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 섹션에는 .NET 메모리 프로파일링 데이터가 포함된 프로파일러 데이터 파일의 뷰와 보고서에 대한 참조 정보가 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [요약 뷰](../profiling/summary-view-dotnet-memory-data.md)  
 가장 많은 메모리를 할당한 함수 및 형식을 나열합니다.  
  
 [할당 뷰](../profiling/dotnet-memory-allocations-view.md)  
 프로파일링 실행에서 할당된 형식 및 형식 할당을 일으킨 호출 트리(실행 경로)를 나열합니다.  
  
 [개체 수명 뷰](../profiling/object-lifetime-view.md)  
 프로파일링 실행에서 할당된 형식, 인스턴스 수, 크기(바이트) 및 형식의 가비지 수집 세대를 나열합니다.  
  
 [호출 트리 뷰 - 샘플링](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
 프로파일링 실행에서 함수의 실행 경로 및 메모리 할당 데이터를 나타내는 계층 구조 트리를 표시합니다.  
  
 [모듈 뷰 - 샘플링](../profiling/modules-view-dotnet-memory-sampling-data.md)  
 .NET 메모리 할당 데이터를 모듈별로 구성하고 함수, 소스 코드 줄, 메모리가 할당될 때 실행되고 있던 명령을 나열합니다.  
  
 [호출자/호출 수신자 뷰 - .NET 메모리 샘플링 데이터](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)  
 선택된 함수에 대한 메모리 할당 데이터, 선택된 함수를 호출한 함수, 선택된 함수에서 호출한 함수를 나열합니다.  
  
 [함수 뷰 - 샘플링](../profiling/functions-view-dotnet-memory-sampling-data.md)  
 프로파일링 실행에서 함수에 대한 메모리 할당 데이터를 나열합니다.  
  
 [줄 뷰 - 샘플링](../profiling/lines-view-dotnet-memory-sampling-data.md)  
 프로파일링 실행에서 함수의 소스 코드 줄에 대한 메모리 할당 데이터를 나열합니다.  
  
 [IP(명령 포인터) 뷰 - 샘플링](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)  
 프로파일링 실행에서 함수의 명령에 대한 메모리 할당 데이터를 나열합니다.  
  
 [호출 트리 뷰 - 계측](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)  
 프로파일링 실행에서 계측된 함수의 실행 경로, 메모리 할당 데이터, 세부 타이밍 데이터를 나타내는 계층 구조 트리를 표시합니다.  
  
 [모듈 뷰 - 계측](../profiling/modules-view-dotnet-memory-instrumentation-data.md)  
 프로파일링 데이터를 모듈별로 구성하고 모듈의 함수, 메모리 할당 데이터, 세부 타이밍 정보를 나열합니다.  
  
 [호출자/호출 수신자 뷰 - .NET 메모리 계측 데이터](../profiling/caller-callee-view-net-memory-instrumentation-data.md)  
 선택된 계측된 함수에 대한 메모리 할당 데이터 및 세부 타이밍 정보, 선택된 함수를 호출한 함수, 선택된 함수에서 호출한 함수를 나열합니다.  
  
 [함수 뷰 - 계측](../profiling/functions-view-dotnet-memory-instrumentation-data.md)  
 프로파일링 실행에서 계측된 함수에 대한 메모리 할당 데이터를 나열합니다.  
  
## <a name="reference"></a>참조  
 [함수 세부 정보 뷰](../profiling/function-details-view.md)  
 선택한 함수와 해당 함수를 호출한 함수 및 해당 함수가 호출한 함수의 관계에 대한 그래픽 차트를 표시합니다.  
  
 [프로세스 뷰](../profiling/process-view.md)  
 프로세스 및 스레드 시작/종료 시간을 나열합니다.  
  
 [표시 뷰](../profiling/marks-view.md)  
 프로파일링 데이터 파일에 삽입된 ETW 및 샘플링 이벤트가 표시됩니다.  
  
## <a name="related-sections"></a>관련 섹션  
 [샘플링 방법 데이터 뷰](../profiling/profiler-sampling-method-data-views.md)  
 샘플링 방법을 사용하여 생성된 프로파일러 데이터 파일의 뷰와 보고서에 대한 참조 정보입니다.  
  
 [계측 방법 데이터 뷰](../profiling/instrumentation-method-data-views.md)  
 계측 방법을 사용하여 생성된 프로파일러 데이터 파일의 뷰와 보고서에 대한 참조 정보입니다.
