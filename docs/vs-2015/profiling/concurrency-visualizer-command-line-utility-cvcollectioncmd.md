---
title: 동시성 시각화 도우미 명령줄 유틸리티(CVCollectionCmd) | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.cvcollectioncmd
ms.assetid: 476601be-1608-4014-af15-5aba6ccbed1c
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b08035deec65c8c42fe875d380d9cc3d15533a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850265"
---
# <a name="concurrency-visualizer-command-line-utility-cvcollectioncmd"></a>동시성 시각화 도우미 명령줄 유틸리티(CVCollectionCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

동시성 시각화 도우미 명령줄 유틸리티(CVCollectionCmd.exe)를 사용하면 명령줄에서 추적을 수집하여 Visual Studio용 동시성 시각화 도우미에서 확인할 수 있습니다. 이러한 도구는 Visual Studio가 설치되지 않은 컴퓨터에서도 사용할 수 있습니다.  
  
> [!NOTE]
> Visual Studio 2013부터 동시성 시각화 도우미는 선택적 확장입니다. (이전에는 Visual Studio에 포함 되었습니다.) 다운로드 센터에서 [Visual Studio 2015 용 동시성 시각화 수집 도구](https://www.microsoft.com/download/details.aspx?id=49103) 를 다운로드할 수 있습니다.  
  
## <a name="download-the-concurrency-visualizer-command-line-utility"></a>동시성 시각화 도우미 명령줄 유틸리티 다운로드  
 명령줄 유틸리티를 다운로드하여 설치하려면 Microsoft 다운로드 센터 웹 사이트에서 [Visual Studio 2015용 동시성 시각화 수집 도구](https://www.microsoft.com/download/details.aspx?id=49103) 로 이동한 후 아래 지침을 따르세요. 기본적으로 CVCollectionCmd.exe는 %ProgramFiles%\Microsoft Concurrency Visualizer Collection Tools\(%ProgramFiles(x86)%\Microsoft Concurrency Visualizer Collection Tools\ on x64 computers)에 설치됩니다.  
  
## <a name="collect-a-trace-with-cvcollectioncmd"></a>CVCollectionCmd를 사용하여 추적 수집  
 CVCollectionCmd를 사용하여 앱을 시작하거나 CVCollectionCmd에 연결하여 추적을 수집할 수 있습니다. 옵션은 아래의 명령 참조를 참조하세요. 예  
  
```  
<Path>CVCollectionCmd /launch c:\myapp\myapp.exe /outdir c:\myapp\data  
```  
  
## <a name="commands-and-parameters"></a>명령 및 매개 변수  
 명령줄 유틸리티의 명령 및 매개 변수에 대한 도움말을 보려면 명령 프롬프트에 다음과 같이 입력합니다.  
  
 **CvCollectionCmd /?**  
  
|옵션|설명|매개 변수|반환 값|  
|------------|-----------------|----------------|-------------------|  
|쿼리|수집을 시작할 수 있는지 여부를 반환합니다.|없음|수집을 시작할 준비가 되면 0입니다.<br /><br /> 수집이 이미 진행 중이면 1입니다.<br /><br /> 수집이 진행 중이 아니지만 필수 [ETW](https://msdn.microsoft.com/library/ac99a063-e2d2-40cc-b659-d23c2f783f92) 세션 중 하나 이상이 이미 사용 하도록 설정 된 경우 2입니다.|  
|Launch|Concurrency 시각화 도우미 아래에서 지정한 프로세스를 실행합니다.|실행 파일의 경로|실행에 성공한 경우 0입니다.<br /><br /> 대상 애플리케이션을 시작할 수 없어 실행에 실패한 경우 1입니다.<br /><br /> CVCollectionCmd에 지정한 출력 디렉토리에 쓸 수 있는 충분한 권한이 없어 실행에 실패한 경우 13입니다.|  
|연결|시스템 차원에서 추적 수집을 시작합니다. 그렇지 않고 프로세스가 지정되어 있으면 해당 프로세스에 연결합니다.|없음|연결에 성공한 경우 0입니다.<br /><br /> 지정한 프로세스가 잘못되었거나 모호해서 연결에 실패한 경우 1입니다.<br /><br /> CVCollectionCmd에 지정한 출력 디렉토리에 쓸 수 있는 충분한 권한이 없어 연결에 실패한 경우 13입니다.|  
|Detach|수집을 중지합니다.|없음|분리에 성공한 경우 0입니다.<br /><br /> 현재 수집이 진행되고 있지 않아 분리에 실패한 경우 1입니다.<br /><br /> 수집을 중지할 수 없어 분리에 실패한 경우 2입니다.|  
|분석|지정한 추적을 분석합니다.|CVTrace 파일의 전체 경로입니다.|분석에 성공한 경우 0입니다.<br /><br /> 지정한 추적이 시스템 차원이지만 대상 프로세스를 지정하지 않아 분석을 시작할 수 없는 경우 1입니다.<br /><br /> 프로세스를 지정했으나 추적이 시스템 차원이 아니라서 분석을 시작할 수 없는 경우 2입니다.<br /><br /> 지정한 프로세스가 잘못되어 분석에 실패한 경우 3입니다.<br /><br /> 지정한 CVTrace 파일이 잘못되어 분석에 실패한 경우 4입니다.|  
|LaunchArgs|실행 가능한 대상 인수를 지정합니다. 이 옵션은 Launch 명령에만 적용됩니다.|애플리케이션에 대한 명령줄 인수|없음|  
|Outdir|추적 파일을 저장할 디렉터리를 지정합니다. Launch 및 Attach 명령에 적용됩니다.|디렉터리 경로 또는 상대 경로|없음|  
|프로세스|Attach 명령이 실행되면 연결할 프로세스 또는 Analyze 명령이 실행되면 분석할 추적의 프로세스를 지정합니다. Attach 및 Analyze 명령에 적용됩니다.|프로세스의 PID 또는 이름|없음|  
|Config|기본값 이외의 수집 설정이 필요한 경우 구성 파일의 경로를 지정합니다.   Launch, Attach 및 Analyze 명령에 적용됩니다.|XML 구성 파일의 디렉터리 경로 또는 상대 경로|없음|  
  
## <a name="customizing-configuration-settings"></a>구성 설정 사용자 지정  
 CVCollectionCmd를 사용해 추적을 수집하고 수집 설정을 사용자 지정하려는 경우 구성 파일을 사용해 설정을 지정합니다.  
  
> [!NOTE]
> Visual Studio를 사용해 추적을 수집하는 경우에는 구성 파일을 직접 수정하지 마세요.  대신 [고급 설정](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) 대화 상자를 사용해 설정을 수정합니다.  
  
 수집 설정을 수정하려면 CVCollectionCmd 유틸리티를 실행할 컴퓨터에 구성 파일을 만듭니다. 구성 파일을 처음부터 만들거나 Visual Studio 설치된 컴퓨터에서 구성 파일을 복사하고 수정할 수 있습니다. 이 파일의 이름은 `UserConfig.xml` 로 **Local AppData** 폴더에 있습니다. 이 유틸리티를 실행하면 Launch, Attach 또는 Analyze 명령과 함께 Config 옵션을 사용합니다.  Config 옵션과 관련된 매개 변수에서 구성 파일의 경로를 지정합니다.  
  
### <a name="configuration-file-tags"></a>구성 파일 태그  
 구성 파일은 XML 기반입니다. 올바른 태그 및 값은 다음과 같습니다.  
  
|태그|설명|값|  
|---------|-----------------|------------|  
|Config|전체 구성 파일의 경계를 지정합니다.|다음 요소를 포함해야 합니다.<br /><br /> -   MinorVersion<br />-   MajorVersion|  
|MajorVersion|구성 파일의 주 버전을 지정합니다.|[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 프로젝트의 경우 1이어야 합니다. 1이 아니면 유틸리티가 작동하지 않습니다.|  
|MinorVersion|구성 파일의 부 버전을 지정합니다.|[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 프로젝트의 경우 0이어야 합니다. 0이 아니면 유틸리티가 작동하지 않습니다.|  
|IncludeEnvSymbolPath|환경 기호 경로(_NT_SYMBOL_PATH)를 사용할지 여부를 결정하는 값을 설정합니다.|-   True<br />-   False|  
|DeleteEtlsAfterAnalysis|분석이 완료되면 ETL 파일을 삭제할지 여부를 결정하는 값을 설정합니다.|-   True<br />-   False|  
|SymbolPath|기호 서버의 경로를 지정합니다. 자세한 내용은 [Microsoft 기호 서버를 사용하여 디버그 기호 파일 얻기](https://support.microsoft.com/kb/311503)를 참조하세요.|디렉터리 이름 또는 URL|  
|Markers|표식 공급자 목록을 포함합니다.|MarkerProvider 요소를 0개 이상 포함할 수 있습니다.|  
|MarkerProvider|단일 표식 공급자를 지정합니다.|다음 요소를 포함해야 합니다.<br /><br /> -   Level<br />-   GUID<br />-   Name<br /><br /> 다음 요소를 포함할 수 있습니다.<br /><br /> -   Categories<br />-   IsEnabled|  
|Level|MarkerProvider의 중요도 수준을 설정합니다.|-   Low<br />-   Normal<br />-   High<br />-   Critical<br />-   Everything|  
|GUID|ETW 표식 공급자의 고유한 전역 식별자입니다.|GUID|  
|이름|표식 공급자에 대한 설명을 지정합니다.|문자열|  
|범주|표식 공급자에 대해 수집된 범주를 지정합니다.|쉼표로 구분된 숫자 문자열 또는 숫자 범위|  
|IsEnabled|표식 공급자를 수집에 사용할지 여부를 결정하는 값을 설정합니다.|-   True<br />-   False|  
|FilterConfig|수집에서 필터링된 ETW 이벤트의 구성 옵션 목록을 지정합니다.|다음 요소가 포함되어 있을 수 있습니다.<br /><br /> -   CollectClrEvents<br />-   ClrCollectionOptions<br />-   CollectSampleEvents<br />-   CollectGpuEvents<br />-   CollectFileIO|  
|CollectClrEvents|CLR 이벤트 수집 여부를 결정하는 값을 설정합니다.|-   True<br />-   False|  
|ClrCollectionOptions|네이티브 앱의 CLR 이벤트 수집 여부와 NGEN 런다운 이벤트 수집 여부를 지정합니다.|다음 값 중 하나 또는 둘 다를 포함하거나 둘 다 포함하지 않을 수 있습니다.<br /><br /> -   CollectForNative<br />-   DisableNGenRundown|  
|CollectSampleEvents|샘플 이벤트를 수집할지 여부를 결정하는 값을 설정합니다.|-   True<br />-   False|  
|CollectGpuEvents|DX에서 생성한 이벤트를 수집할지 여부를 결정하는 값을 설정합니다.|-   True<br />-   False|  
|CollectFileIO|파일 I/O 이벤트를 수집할지 여부를 결정하는 값을 설정합니다.|-   True<br />-   False|  
|UserBufferSettings|사용자 버퍼 설정 매개 변수의 목록을 지정합니다.|다음 요소를 포함해야 합니다.<br /><br /> -   BufferFlushTimer<br />-   BufferSize<br />-   MinimumBuffers<br />-   MaximumBuffers|  
|KernelBufferSettings|커널 버퍼 설정 매개 변수 목록을 지정합니다.|다음 요소를 포함해야 합니다.<br /><br /> -   BufferFlushTimer<br />-   BufferSize<br />-   MinimumBuffers<br />-   MaximumBuffers|  
|BufferFlushTimer|ETW 버퍼의 플러시 타이머를 지정합니다.|양의 정수|  
|BufferSize|각 이벤트 추적 세션 버퍼에 할당된 메모리 양(킬로바이트)입니다.|0~1024의 숫자|  
|MinimumBuffers|이벤트 추적 세션의 버퍼 풀에 할당된 최소 버퍼 수 입니다.|논리 코어 수의 2배 이상인 양의 정수|  
|MaximumBuffers|이벤트 추적 세션의 버퍼 풀에 할당된 최대 버퍼 수 입니다.|MinimumBuffers 이상의 수|  
|JustMyCode|내 코드만 디렉터리의 목록을 지정합니다.|MyCodeDirectory 요소 0개 이상으로 구성된 목록|  
|MyCodeDirectory|코드가 포함된 디렉터리를 지정합니다.|절대 경로|  
  
### <a name="example"></a>예제  
 처음부터 구성 파일을 만드는 대신 다음 예제를 복사한 다음 요구 사항에 맞춰 수정할 수 있습니다.  
  
```xml  
<?xml version="1.0"?>  
<LocalConfig xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" MajorVersion="1" MinorVersion="0">  
  
  <IncludeEnvSymbolPath>true</IncludeEnvSymbolPath>  
  
  <DeleteEtlsAfterAnalysis>true</DeleteEtlsAfterAnalysis>  
  
  <TraceLocation>C:\traces</TraceLocation>  
  
  <SymbolPath>http://symweb</SymbolPath>  
  
  <Markers>  
    <MarkerProvider Name="Default" Guid="8d4925ab-505a-483b-a7e0-6f824a07a6f0" Level="Low" />  
    <MarkerProvider Name="TPL" Guid="2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5" Level="Normal" />  
    <MarkerProvider Name="TPL Dataflow" Guid="16f53577-e41d-43d4-b47e-c17025bf4025" Level="Normal" />  
    <MarkerProvider Name="TPL Synchronization" Guid="ec631d38-466b-4290-9306-834971ba0217" Level="Normal" />  
    <MarkerProvider Name="PLINQ" Guid="159eeeec-4a14-4418-a8fe-faabcd987887" Level="Normal" />  
    <MarkerProvider Name="Concurrency Runtime" Guid="f7b697a3-4db5-4d3b-be71-c4d284e6592f" Level="Normal" />  
    <MarkerProvider Name="Scenario Markers" Guid="fb9244c9-f23a-4966-8a9c-97a51f8c355b" Level="Low" />  
  
    <!-- The IsEnabled and Categories elements are optional -->  
    <MarkerProvider Name="myMarker1" Guid="d0dbb3a3-895c-4ce6-96d9-28f69d664dc3" Level="Critical" IsEnabled="false" Categories="0,1,3-5,8" />  
    <MarkerProvider Name="myMarker2" Guid="03452127-a617-4302-9e30-c0d10442e4ee" Level="Low" IsEnabled="false" Categories="0,1,3-5,8-10,11-13" />  
  </Markers>  
  
  <FilterConfig>  
    <CollectClrEvents>true</CollectClrEvents>  
    <ClrCollectionOptions>CollectForNative DisableNGenRundown</ClrCollectionOptions>  
    <CollectSampleEvents>true</CollectSampleEvents>  
    <CollectGpuEvents>true</CollectGpuEvents>  
    <CollectFileIO>true</CollectFileIO>  
  </FilterConfig>  
  
  <UserBufferSettings>  
    <BufferFlushTimer>0</BufferFlushTimer>  
    <BufferSize>256</BufferSize>  
    <MinimumBuffers>512</MinimumBuffers>  
    <MaximumBuffers>1024</MaximumBuffers>  
  </UserBufferSettings>  
  
  <KernelBufferSettings>  
    <BufferFlushTimer>0</BufferFlushTimer>  
    <BufferSize>256</BufferSize>  
    <MinimumBuffers>512</MinimumBuffers>  
    <MaximumBuffers>1024</MaximumBuffers>  
  </KernelBufferSettings>  
  
  <!-- List of MyCodeDirectory directories -->  
  <JustMyCode>  
    <MyCodeDirectory>C:\myBinaries1</MyCodeDirectory>  
    <MyCodeDirectory>C:\myBinaries2</MyCodeDirectory>  
  </JustMyCode>  
</LocalConfig>  
  
```
