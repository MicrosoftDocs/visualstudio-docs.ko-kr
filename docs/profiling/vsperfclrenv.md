---
title: VSPerfCLREnv | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2163ebb9b363de8ee638998dbe56fd76f5a891c8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779911"
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv

VSPerfCLREnv 도구는 .NET Framework 애플리케이션을 프로파일링하는 데 필요한 환경 변수를 설정하는 데 사용됩니다. 이 도구는 다음 구문을 사용합니다.

```cmd
VsPerfCLREnv [/option]
```

선택하는 옵션은 세 가지 프로파일링 유형(샘플링, 계측, 전역) 중 사용하는 유형에 따라 달라집니다. 프로파일링 데이터에 계층 상호 작용 데이터를 포함하려면 별도의 옵션이 필요합니다. 다음 표에는 각 옵션의 구문에 대한 설명이 나와 있습니다.

> [!NOTE]
> 프로파일링을 완료한 후에는 **/off** 또는 **/globaloff** 옵션을 포함해 **VSPerfCLREnv**를 실행하여 프로파일링에 필요한 환경 변수를 삭제합니다. 자세한 내용은 이 문서에 나와 있는 환경 설정 삭제를 위한 VSPerfCLREnv 옵션을 참조하세요.

## <a name="vsperfclrenv-options-for-including-tier-interaction-data"></a>계층 상호 작용 데이터를 포함하기 위한 VSPerfCLREnv 옵션

> [!WARNING]
> 계층 상호 작용 프로파일링은 Visual Studio의 모든 버전을 사용하여 수집할 수 있습니다. 그러나 계층 상호 작용 프로파일링 데이터는 Visual Studio Enterprise에서만 볼 수 있습니다.

계층 상호 작용 프로파일링에서는 다층 계층 애플리케이션의 ADO.NET 쿼리에 대한 추가 정보를 제공합니다. 동기 함수 호출에 대해서만 데이터가 수집됩니다. 원하는 프로파일링 방법을 사용하여 상호 작용 데이터를 프로파일링 실행에 추가할 수 있습니다.

**InteractionOn** 및 **GlobalInteractionOn** 옵션을 사용하면 계층 상호 작용 데이터를 수집할 수 있습니다. 애플리케이션을 프로파일링하는 데 필요한 VSPerfCLREnv 환경 변수를 설정한 후에 상호 작용 옵션을 설정해야 합니다.

다음 예제에는 샘플링 방법을 사용하는 프로파일링 실행의 계층 상호 작용 데이터가 포함되어 있습니다.

```cmd
VSPerfCLREnv /SampleOn
VSPerfCLREnv /InteractionOn
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe
```

다음 예제에는 Windows 서비스에 대한 프로파일링 실행의 계층 상호 작용 데이터가 포함되어 있습니다.

```cmd
VSPerfCLREnv /GlobalSampleOn
VSPerfCLREnv /GlobalInteractionOn
REM Restart the computer and start the service
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp
VSPerfCmd /Attach:MyService.exe
```

## <a name="vsperfclrenv-options-for-process-instrumentation-profiling"></a>프로세스 계측 프로파일링을 위한 VSPerfCLREnv 옵션

다음 표에는 계측 프로파일링을 위한 VSPerfCLREnv 옵션에 대한 설명이 나와 있습니다.

|옵션|Description|
|------------|-----------------|
|**TraceOn**|계측 방법을 사용하여 프로파일링을 활성화합니다. 메모리 할당 프로파일링 또는 개체 수명 데이터 수집은 활성화되지 않습니다.|
|**TraceGC**|계측 방법을 사용하여 메모리 할당 프로파일링을 활성화합니다. 개체 수명 데이터 수집은 활성화되지 않습니다.|
|**TraceGCLife**|계측 방법을 사용하여 메모리 할당 프로파일링 및 개체 수명 데이터 수집을 활성화합니다.|

## <a name="vsperfclrenv-options-for-process-sampling-profiling"></a>프로세스 샘플링 프로파일링을 위한 VSPerfCLREnv 옵션

다음 표에는 샘플링 프로파일링을 위한 VSPerfCLREnv 옵션에 대한 설명이 나와 있습니다.

|옵션|Description|
|------------|-----------------|
|**SampleOn**|샘플링 방법을 사용하여 프로파일링을 활성화합니다. 메모리 할당 프로파일링 또는 개체 수명 데이터 수집은 활성화되지 않습니다.|
|**SampleGC**|샘플링 방법을 사용하여 메모리 할당 프로파일링을 활성화합니다. 개체 수명 데이터 수집은 활성화되지 않습니다.|
|**SampleGCLife**|샘플링 방법을 사용하여 메모리 할당 프로파일링을 활성화합니다. 개체 수명 데이터 수집도 활성화됩니다.|
|**SampleLineOff**|.NET 줄 수준 프로파일링 데이터 수집을 비활성화합니다.|

## <a name="vsperfclrenv-options-for-global-profiling"></a>전역 프로파일링을 위한 VSPerfCLREnv 옵션

사용자가 시작하는 것이 아니라 운영 체제에 의해 시작되는 ASP.NET 웹 애플리케이션과 관리 서비스를 프로파일링하려면 VSPerfCLREnv 옵션의 전역 프로파일링용 옵션을 사용합니다. 다음 표에는 VSPerfCLREnv 옵션의 전역 버전에 대한 설명이 나와 있습니다. 이러한 옵션은 레지스트리에서 적절한 환경 변수를 설정합니다.

|옵션|Description|
|------------|-----------------|
|**GlobalTraceOn**|계측 방법을 사용하여 전역 프로파일링을 활성화합니다. 메모리 할당 이벤트 또는 개체 수명 데이터는 수집되지 않습니다.|
|**GlobalTraceGC**|계측 방법을 사용하여 전역 메모리 할당 프로파일링을 활성화합니다. 개체 수명 데이터 수집은 활성화되지 않습니다.|
|**GlobalTraceGCLife**|계측 방법을 사용하여 전역 메모리 할당 프로파일링을 활성화합니다. 개체 수명 데이터 수집도 활성화됩니다.|
|**GlobalSampleOn**|샘플링 방법을 사용하여 전역 프로파일링을 활성화합니다. 메모리 할당 이벤트 또는 개체 수명 데이터 수집은 활성화되지 않습니다.|
|**GlobalSampleGC**|샘플링 방법을 사용하여 전역 메모리 할당 프로파일링을 활성화합니다. 개체 수명 데이터 수집은 활성화되지 않습니다.|
|**GlobalSampleGCLife**|샘플링 방법을 사용하여 전역 메모리 할당 프로파일링을 활성화합니다. 개체 수명 데이터 수집도 활성화됩니다.|

## <a name="vsperfclrenv-options-to-delete-environment-settings"></a>환경 설정 삭제를 위한 VSPerfCLREnv 옵션

 관리되는 애플리케이션 프로파일링을 완료한 후에는 다음 옵션 중 하나를 사용하여 VSPerfCLREnv가 추가한 환경 변수를 삭제합니다. 다음 표에서는 표준 환경 변수와 전역 환경 변수를 둘 다 삭제하는 방법을 설명합니다.

|옵션|Description|
|------------|-----------------|
|**Off**|표준 .NET 프로파일링용 환경 변수를 삭제합니다. 비전역 VSPerfClrEnv 옵션을 사용하여 프로파일러 환경 변수를 설정한 경우 이 옵션을 사용합니다.|
|**GlobalOff**|전역 .NET 프로파일링용 환경 변수를 삭제합니다. 프로파일러가 아닌 운영 체제에 의해 애플리케이션이 시작된 경우 이 옵션을 사용합니다.|

## <a name="remarks"></a>설명

IDE의 성능 탐색기를 사용하여 애플리케이션을 시작한 경우에는 관리되는 애플리케이션을 프로파일링하는 데 이러한 옵션이 필요하지 않습니다. 성능 탐색기가 필요한 모든 환경 설정을 자동으로 지정합니다.

프로파일링 중에 올바른 환경이 설정되지 않은 경우에는 분석 중에 경고가 보고되며 관리되는 함수 이름이 적절하게 확인되지 않습니다.

## <a name="see-also"></a>참고 항목

[명령줄에서 프로파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)
