---
title: 고급 설정 대화 상자(동시성 시각화 도우미) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.settings
ms.assetid: bb3d90aa-5f08-4953-9be0-be6cea11633d
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 128327b956734f7d28e7ff88f3eb6c297544587c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849815"
---
# <a name="advanced-settings-dialog-box-concurrency-visualizer"></a>고급 설정 대화 상자(동시성 시각화 도우미)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

동시성 시각화 도우미의 **고급 설정** 대화 상자에서는 추적 수집 방법을 제어할 수 있습니다.  이 대화 상자에는 기호, 내 코드만, 버퍼링, 필터링, CLR 이벤트, 표식, 공급자 및 파일에 대한 탭이 포함됩니다.  
  
## <a name="symbols"></a>Symbols  
 동시성 시각화 도우미에는 Visual Studio 디버거와 동일한 기호 설정이 사용됩니다. 동시성 시각화 도우미는 이 설정을 사용해서 성능 데이터와 연관된 호출 스택을 분석합니다.  추적을 처리할 때 동시성 시각화 도우미는 설정 페이지에 지정된 기호 서버에 액세스합니다.  네트워크를 통해 이 데이터에 액세스할 경우에는 추적 처리 속도가 느려집니다.  기호를 분석하는 데 필요한 시간을 줄이기 위해서는 기호를 로컬로 캐시할 수 있습니다. 기호가 다운로드되었으면 Visual Studio가 로컬 캐시에서 기호를 로드합니다.  
  
## <a name="just-my-code"></a>내 코드만  
 기본적으로 내 코드만은 Visual Studio의 현재 솔루션과 연관된 .exe 및 .dll 파일 집합입니다. 동시성 시각화 도우미는 내 코드만 기능을 사용해서 호출 스택을 필터링할 때 이 파일 집합을 평가합니다. 내 코드만 탭에서는 동시성 시각화 도우미가 내 코드만에 사용하는 위치에 .exe 및 .dll 파일이 포함된 디렉터리를 추가할 수 있습니다.  
  
 .Exe 및 .dll 파일의 경로는 추적을 수집할 때 추적 파일에 저장됩니다.  이 설정을 변경해도 이전에 수집된 모든 추적에는 영향을 주지 않습니다.  
  
## <a name="buffering"></a>버퍼링  
 동시성 시각화 도우미는 추적을 수집할 때 ETW(Windows용 이벤트 추적)를 사용합니다.  ETW는 이벤트를 저장할 때 여러 버퍼를 사용합니다.  기본 ETW 버퍼 설정은 모든 경우에 최적이 아닐 수 있으며, 일부 경우에는 이벤트 손실과 같은 문제를 일으킬 수 있습니다.  버퍼링 탭을 사용하여 ETW 버퍼 설정을 구성할 수 있습니다. 자세한 내용은 [이벤트 추적](https://msdn.microsoft.com/library/bb968803(VS.85).aspx) 및 [EVENT_TRACE_PROPERTIES 구조](https://msdn.microsoft.com/library/aa363784(VS.85).aspx)를 참조하세요.  
  
## <a name="filter"></a>Assert  
 필터 탭에는 동시성 시각화 도우미에서 수집하는 이벤트 집합을 선택할 수 있습니다. 이벤트 하위 집합을 선택하면 보고서에 표시되는 데이터 형식이 제한되고, 각 추적의 크기가 감소하고, 추적 처리에 필요한 시간이 줄어듭니다.  
  
### <a name="clr-events"></a>CLR 이벤트  
 CLR(공용 언어 런타임)에서 생성된 이벤트는 동시성 시각화 도우미가 관리되는 호출 스택을 분석할 수 있게 해줍니다.  CLR 이벤트 수집을 비활성화하면 추적 크기가 줄어들지만 일부 호출 스택이 분석되지 않습니다.  따라서 일부 CPU 스레드 작업이 잘못 분류될 수 있습니다.  
  
### <a name="collect-for-native-processes"></a>네이티브 프로세스 수집  
 기본적으로 CLR 이벤트는 네이티브 프로세스에 대해 일반적으로 필요하지 않기 때문에 관리되는 프로세스가 프로파일링되었을 때만 수집됩니다.  네이티브 프로세스가 CLR을 호스팅하는 일부 경우에는 네이티브 프로세스에 대해 CLR 이벤트를 수집해야 할 수 있습니다.  이 경우 **네이티브 프로세스 수집** 확인란을 선택합니다.  
  
### <a name="disable-rundown-events"></a>런다운 이벤트 사용 안 함  
 CLR은 런타임 및 런다운의 두 공급자로부터 이벤트를 생성합니다.  CLR 런타임 이벤트를 수집하지만 런다운 이벤트는 수집하지 않으려면 **런다운 이벤트 사용 안 함** 확인란을 선택합니다.  그러면 컬렉션으로 생성되는 추적 파일 크기가 줄어들지만 일부 스택이 분석되지 않을 수 있습니다. 자세한 내용은 [CLR ETW 공급자](https://msdn.microsoft.com/library/0beafad4-b2c8-47f4-b342-83411d57a51f)를 참조하세요.  
  
### <a name="sample-events"></a>샘플 이벤트  
 샘플 이벤트를 사용해서 스레드 실행과 연관된 호출 스택을 추적할 수 있습니다. 이러한 이벤트는 현재 프로세스에서 실행 중인 스레드에 대해 대략적으로 밀리초당 한 번씩 수집됩니다. 샘플 이벤트의 수집을 비활성화하면 수집되는 추적 크기가 줄어들지만 스레드 실행과 연관된 호출 스택을 볼 수 없습니다.  
  
### <a name="gpu-events"></a>GPU 이벤트  
 GPU 이벤트는 DirectX에 의해 생성되는 이벤트입니다. GPU 이벤트의 수집을 비활성화하면 수집되는 추적 크기가 줄어들지만 사용률 보기에서 GPU 작업을 보거나 스레드 보기에서 DirectX 엔진 작업을 볼 수 없습니다.  
  
### <a name="file-io-events"></a>파일 I/O 이벤트  
 파일 I/O 이벤트는 현재 프로세스를 대신해서 디스크에 대한 액세스를 제공합니다.  파일 I/O 이벤트를 비활성화하면 추적 크기가 줄어들지만 스레드 보기에서 디스크 채널 또는 디스크 작업에 대한 정보를 보고하지 않습니다.  
  
## <a name="markers"></a>표식  
 표식 탭에서는 동시성 시각화 도우미에 표식으로 나타나는 ETW 공급자 집합을 구성할 수 있습니다.  또한 중요도 수준 및 ETW 범주에 따라 표식 컬렉션을 필터링 할 수 있습니다.  [동시성 시각화 도우미 SDK](../profiling/concurrency-visualizer-sdk.md)를 사용 중이고 고유한 표식 공급자를 사용 중이면 스레드 보기에 표시되도록 여기에서 등록할 수 있습니다.  
  
### <a name="adding-a-new-provider"></a>새 공급자 추가  
 코드에 [Concurrency 시각화 SDK](../profiling/concurrency-visualizer-sdk.md)가 사용되거나 <xref:System.Diagnostics.Tracing.EventSource> 규칙을 따르는 ETW 이벤트가 생성될 경우, 이 대화 상자에서 등록하여 Concurrency 시각화에서 이러한 이벤트를 볼 수 있습니다.  
  
 이름 필드에는 공급자가 생성하는 이벤트 유형을 설명하는 이름을 입력합니다.  GUID 필드에는 이 공급자와 연관된 GUID를 입력합니다. (GUID는 모든 ETW 공급자와 연결됩니다.)  
  
 선택적으로 범주 또는 중요도 수준을 기준으로 이 공급자의 이벤트를 필터링할지 여부를 지정할 수 있습니다.  범주 필드를 사용해서 동시성 시각화 도우미 SDK 범주를 기준으로 필터링할 수 있습니다.  이렇게 하려면 쉼표로 구분된 범주 문자열 또는 범주 범위를 입력합니다.  그러면 현재 공급자에서 표시할 이벤트 범주가 지정됩니다.  <xref:System.Diagnostics.Tracing.EventSource> 공급자를 추가하려는 경우, 범주 필드를 사용해서 ETW 키워드로 필터링할 수 있습니다.  키워드는 비트 마스크이기 때문에 쉼표로 구분된 정수 문자열을 사용해서 마스크에서 설정되는 비트를 지정할 수 있습니다. 예를 들어, "1,2"는 첫 번째 및 두 번째 비트를 설정하고 십진수 6으로 변환됩니다.  
  
 중요도 수준 목록을 사용해서 중요도 또는 ETW 수준이 지정된 값보다 낮은 이벤트를 필터링할 수 있습니다.  
  
### <a name="configuring-an-existing-provider"></a>기존 공급자 구성  
 기존 공급자와 연관된 설정을 편집하려면 목록에서 선택한 후 **공급자 편집** 단추를 선택합니다.  이름, GUID 및 필터 설정을 변경할 수 있습니다.  
  
### <a name="filter-marker-data-out-of-concurrency-visualizer-reports"></a>동시성 시각화 보고서에서 표식 데이터 필터링  
 이후 추적에 특정 공급자에 대한 데이터를 표시하지 않으려면 제거하려는 공급자 옆에 있는 확인란의 선택을 취소합니다.  
  
## <a name="files"></a>파일  
 **파일** 탭에서는 추적이 수집될 때마다 저장되는 추적 파일의 디렉터리를 지정할 수 있습니다.  동시성 시각화 도우미는 수집하는 각 추적에 대해 4개의 파일을 생성합니다.  
  
- 커널 모드 ETL(이벤트 추적 로그) 파일(*. kernel.etl)  
  
- 사용자 모드 이벤트 추적 로그 파일(*. user.etl)  
  
- 동시성 시각화 도우미 데이터 파일(*.CVData)  
  
- 동시성 시각화 도우미 추적 파일(*.CVTrace)  
  
  두 ETL 파일에는 원시 추적 데이터가 저장되고, 두 동시성 시각화 도우미 파일에는 처리된 데이터가 저장됩니다.  추적이 처리된 다음에는 일반적으로 원시 ETL 파일이 사용되지 않습니다.  **분석 후 ETL(이벤트 추적 로그) 파일 삭제** 확인란을 선택하면 디스크에 저장되는 추적 파일의 양이 줄어듭니다.  
  
## <a name="see-also"></a>관련 항목  
 [내 코드만](../profiling/just-my-code-threads-view.md)   
 [동시성 시각화 도우미 표식](../profiling/concurrency-visualizer-markers.md)
