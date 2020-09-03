---
title: HPC(고성능 컴퓨팅) 클러스터에서 프로파일링 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.hpc.wizard.exeoptions
- vs.performance.hpc.wizard.summary
- vs.performance.hpc.wizard.startoptions
- vs.performance.hpc.wizard.intro
- vs.performance.hpc.property.basic
- vs.performance.hpc.wizard.application
- vs.performance.hpc.wizard.clusteroptions
- vs.performance.hpc.property.advanced
helpviewer_keywords:
- profililng tools,HPC
- HPC profiling
ms.assetid: 1525bbdb-27da-4088-8487-a486cee5e7b3
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b63f9ddf29ff74a4aa4bf089c266e12e37bb2f50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535540"
---
# <a name="profiling-on-hpc-high-performance-computing-clusters"></a>HPC(High Performance Computing) 클러스터에서 프로파일링
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsPreExt](../includes/vspreext-md.md)] 또는 [!INCLUDE[vsUltExt](../includes/vsultext-md.md)] 프로파일링 도구의 샘플링 방법을 사용하여 Microsoft Windows HPC 클러스터의 컴퓨팅 노드에서 프로파일링을 수행할 수 있습니다. HPC에 대 한 자세한 내용은 Microsoft 웹 사이트에서 [빅 계산: hpc & Batch](https://azure.microsoft.com/solutions/big-compute/) 를 참조 하세요.  
  
## <a name="prerequisites"></a>사전 요구 사항  
 HPC 컴퓨팅 노드에서 프로파일링하려면 다음을 수행해야 합니다.  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]과 같은 컴퓨터에 Microsoft HPC 팩 2008을 설치합니다. 컴퓨터는 HPC 클러스터의 일부분이 아니어도 됩니다. HPC 팩은 [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=2800)에서 설치할 수 있습니다.  
  
- [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] 및 독립 실행형 버전의 프로파일링 도구를 HPC 컴퓨팅 노드에 설치합니다. [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 및 독립 실행형 프로파일러의 설치 프로그램은 모두 [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] 설치 미디어에 포함되어 있습니다. **참고**[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]를 설치한 후 프로파일링 도구를 설치하기 전에 컴퓨팅을 다시 시작해야 합니다.  
  
  활성 HPC 컴퓨팅 노드에 [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] 및 독립 실행형 프로파일링 도구를 설치하고 클러스터 컴퓨터에 대한 프로파일링을 활성화하려면 다음 단계를 수행합니다.  
  
1. HPC 팩과 함께 설치된 명령 프롬프트 창을 엽니다.  
  
2. 별도의 명령 프롬프트에서 다음 명령을 입력합니다.  
  
    1. `clusrun /all /scheduler:` *%HeadNode% %FxPath%* `/q /norestart`  
  
    2. `clusrun /all /scheduler:` *%HeadNode%* `shutdown /r /t 0 /d u:4:2 /c "Microsoft .NET Framework install required restart"`  
  
    3. `clusrun /all /scheduler:` *%HeadNode% %ProfilerPath%* `/q /norestart`  
  
|구문 요소|설명|  
|-|-|  
|*헤드 노드에*|클러스터의 헤드 노드 이름입니다.|  
|*%FxPath%*|[!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] 설치 관리자의 경로입니다. [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] 설치 미디어에서 경로는 WCU\dotNetFramework\dotNetFx40_Full_x86_x64.exe입니다.|  
|*%ProfilerPath%*|프로파일링 도구 설치 관리자의 독립 실행형 버전 경로입니다. [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] 설치 미디어에서 경로는 Standalone Profiler\x64\vs_profiler.exe입니다.|  
  
## <a name="profiling-on-an-hpc-compute-node"></a>HPC 컴퓨팅 노드에서 프로파일링  
 HPC 성능 마법사를 사용하여 HPC 클러스터 및 대상 정보를 지정하는 방식으로 프로파일링 세션을 구성합니다. 성능 세션 속성 페이지에서 추가 옵션을 설정할 수 있습니다. 프로파일링 도구는 필요한 대상 이진 파일을 자동으로 배포하고 프로파일러 및 HPC 애플리케이션을 시작합니다.  
  
#### <a name="to-profile-on-an-hpc-compute-node"></a>HPC 컴퓨팅 노드에서 프로파일링하려면  
  
1. **분석** 메뉴에서 **HPC 성능 마법사 시작**을 클릭합니다. 명령을 사용할 수 없는 경우 위에 나와 있는 필수 구성 요소를 충족했는지 확인합니다.  
  
2. 마법사의 첫 페이지에서 **다음**을 클릭합니다.  
  
3. 마법사의 두 번째 페이지에서 프로파일링할 애플리케이션을 선택합니다.  
  
    - 현재 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]에 열려 있는 프로젝트를 프로파일링하려면 **하나 이상의 사용 가능한 프로젝트** 옵션을 선택하고 목록에서 프로젝트 이름을 선택합니다.  
  
    - 열린 프로젝트에 없는 이진 파일을 프로파일링하려면 **실행 파일(.EXE 파일)** 옵션을 선택합니다.  
  
4. **다음**을 클릭합니다.  
  
5. 마법사의 세 번째 페이지에서 다음을 수행합니다.  
  
    - 열린 프로젝트에 없는 실행 파일을 프로파일링하는 경우 **실행 파일의 전체 경로**에서 이진 파일의 경로를 지정합니다.  
  
    - 열린 프로젝트에 없는 실행 파일을 프로파일링하는 경우 **명령줄 인수**에서 프로세스에 전달할 명령줄 인수를 지정할 수 있습니다.  
  
    - **원격 작업 디렉터리**에서 개별 컴퓨팅 노드의 프로세스 인스턴스가 사용하는 폴더의 경로를 지정합니다.  
  
    - **배포 위치**에서 HPC 서버가 배포용 이미지를 준비하는 데 사용하는 디렉터리의 경로를 지정합니다.  
  
6. **다음**을 클릭합니다.  
  
7. 마법사의 네 번째 페이지에서 다음을 수행합니다.  
  
    - **헤드 노드** 목록에서 프로파일링 실행의 HPC 헤드 노드로 사용할 컴퓨터를 클릭합니다. 헤드 노드는 "localhost"일 수 있습니다. 이 경우 클러스터를 사용하지 않고도 로컬 컴퓨터에서 프로파일링할 수 있습니다.  
  
    - **프로세스 수** 목록에서 실행할 애플리케이션 인스턴스의 수를 클릭합니다.  
  
    - **프로파일링 옵션** 목록에서 프로파일링 대상을 선택합니다.  
  
         클러스터의 특정 프로세스를 프로파일링하려면 **순위의 프로필** 옵션을 선택하고 드롭다운 목록에서 프로세스의 순위를 선택합니다.  
  
         HPC 클러스터의 특정 노드에서 실행되는 하나 이상의 프로세스를 프로파일링하려면 **노드의 프로필** 옵션을 선택하고 드롭다운 목록에서 노드를 선택합니다.  
  
8. **다음**을 클릭합니다.  
  
9. 마법사의 다섯 번째 페이지에서는 프로파일러 및 프로파일링 프로세스를 즉시 시작하거나 성능 탐색기를 사용하여 프로파일링을 나중에 시작하도록 선택할 수 있습니다.  
  
    - 프로파일링을 즉시 시작하려면 **마법사를 완료한 후 프로파일링을 시작합니다.** 를 선택하고, 수동으로 프로파일링을 시작하려면 확인란 선택을 취소합니다.  
  
10. **마침**을 클릭합니다.  
  
## <a name="setting-hpc-profiling-properties-by-using-performance-session-property-pages"></a>성능 세션 속성 페이지를 사용하여 HPC 프로파일링 속성 설정  
 성능 세션 속성 페이지의 HPC 시작 속성 페이지에서 HPC 프로파일링 마법사에 대해 설정한 성능 세션 속성을 변경할 수 있습니다. HPC 고급 속성 페이지에서 추가 옵션을 설정합니다.  
  
#### <a name="to-open-the-performance-session-property-pages"></a>성능 세션 속성 페이지를 열려면  
  
1. 필요한 경우 성능 탐색기에서 성능 세션(.psess) 파일을 엽니다. **파일** 메뉴에서 **열기**를 클릭하여 파일을 찾습니다.  
  
2. 성능 탐색기에서 성능 세션 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
3. 속성 페이지 대화 상자에서 다음 방법 중 하나를 사용합니다.  
  
    - **일반**을 클릭하고 **HPC 클러스터에서 수집**을 선택하여 HPC 프로파일링을 설정하거나 확인란 선택을 취소하여 HPC 프로파일링을 사용하지 않도록 설정합니다.  
  
    - **HPC 시작 속성**을 클릭하여 HPC 애플리케이션을 시작하는 속성을 변경합니다.  
  
    - **HPC 고급 속성**을 클릭하여 추가 옵션을 설정합니다.  
  
### <a name="hpc-launch-properties"></a>HPC 시작 속성  
  
|속성|설명|  
|--------------|-----------------|  
|**헤드 노드**|프로파일링 실행의 HPC 헤드 노드로 사용할 컴퓨터를 지정합니다.|  
|**프로세스 수**|프로파일링된 애플리케이션에서 실행할 애플리케이션의 인스턴스 수를 지정합니다.|  
|**순위의 프로필**|클러스터의 특정 프로세스를 프로파일링하려면 **순위의 프로필** 옵션을 선택하고 드롭다운 목록에서 프로세스의 순위를 선택합니다.|  
|**노드의 프로필**|HPC 클러스터의 특정 노드에서 실행되는 하나 이상의 프로세스를 프로파일링하려면 **노드의 프로필** 옵션을 선택하고 드롭다운 목록에서 노드를 선택합니다.|  
|**원격 작업 디렉터리**|개별 컴퓨팅 노드의 프로세스 인스턴스가 사용하는 폴더의 경로를 지정합니다.|  
|**배포 위치**|HPC 서버가 배포용 이미지를 준비하는 데 사용하는 디렉터리의 경로를 지정합니다.|  
  
### <a name="advanced-properties"></a>고급 속성  
  
|속성|설명|  
|--------------|-----------------|  
|**프로젝트 이름**|현재 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 프로젝트 또는 솔루션의 이름입니다.|  
|**프로파일러가 중지되면 정리**|true로 설정하면 실행 디렉터리에 배포된 이진 파일이 제거됩니다. 사용자 프로그램에서 만든 파일과 디렉터리는 이 단계에서 제거되지 않습니다. 실행 디렉터리와 배포 디렉터리를 IDE에서 만든 경우 IDE는 해당 디렉터리 제거를 시도하지만, IDE를 통해 배포되지 않은 파일이 포함되어 있는 경우에는 제거를 시도하지 않습니다.|  
|**배포할 추가 파일**|컴퓨팅 노드에서 배포할 추가 파일의 세미콜론으로 구분된 목록을 지정합니다. 줄임표 단추(**...**)를 클릭하면 대화 상자를 통해 여러 파일을 선택할 수 있습니다.|  
|**Mpiexec 명령**|MPI 애플리케이션을 시작 하는 애플리케이션을 지정합니다. 기본값은 **mpiexec.exe**입니다.|  
|**Mpiexec 인수**|Mpiexec.exe 명령에 전달할 인수를 지정합니다.|  
|**클러스터에서 요청된 노드**|애플리케이션을 실행할 클러스터의 노드 수를 지정합니다.|  
|**CRT 파일 배포**|true로 설정하면 클러스터에서 C/C++ 런타임을 배포합니다.|  
|**프로파일링 전 스크립트**|프로파일링 세션이 시작되기 전에 로컬 개발 컴퓨터에서 실행할 스크립트의 경로와 파일 이름을 지정합니다.|  
|**프로파일링 전 스크립트 인수**|프로파일링 전 스크립트에 전달할 인수를 지정합니다.|  
|**프로파일링 후 스크립트**|프로파일링 세션이 종료된 후에 로컬 개발 컴퓨터에서 실행할 스크립트의 경로와 파일 이름을 지정합니다.|  
|**프로파일링 후 스크립트 인수**|프로파일링 후 스크립트에 전달할 인수를 지정합니다.|
