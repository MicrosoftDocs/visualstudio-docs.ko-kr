---
title: '연습: 샘플링을 사용하여 명령줄 프로파일링 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1d53972f-6f35-4842-8c74-1b627f18c70a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96dfe49ce4e174680202cd60c3e8bca83cfbf575
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842038"
---
# <a name="walkthrough-command-line-profiling-using-sampling"></a>연습: 샘플링을 사용하여 명령줄 프로파일링
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 성능 문제를 파악하도록 명령줄 도구와 샘플링을 사용하여 애플리케이션을 프로파일링하는 방법을 설명합니다.  
  
 이 연습에서는 명령줄 도구를 사용하여 관리되는 애플리케이션을 프로파일링하고, 샘플링을 사용하여 애플리케이션의 성능 문제를 격리 및 식별하는 과정을 단계별로 진행합니다.  
  
 이 연습에서는 다음과 같은 단계를 수행합니다.  
  
- 샘플링 및 명령줄 도구를 사용하여 애플리케이션 프로파일링  
  
- 성능 문제를 찾아서 해결하기 위해 샘플링된 프로파일링 결과 분석  
  
## <a name="prerequisites"></a>전제 조건  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]또는 [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
- [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)]에 대한 중간 정도의 이해도  
  
- 명령줄 도구 사용법에 대한 중간 정도의 이해도  
  
- [PeopleTrax 샘플](../profiling/peopletrax-sample-profiling-tools.md) 의 복사본  
  
- 프로파일링을 통해 제공되는 정보를 사용하려면 디버깅 기호 정보를 준비해 두는 것이 가장 좋습니다.  
  
## <a name="command-line-profiling-using-the-sampling-method"></a>샘플링 방법을 사용하여 명령줄 프로파일링  
 샘플링은 특정 프로세스를 주기적으로 폴링하여 활성 함수를 확인하는 프로파일링 방법입니다. 결과 데이터는 프로세스를 샘플링할 때 함수가 호출 스택 위에 있었던 빈도에 해당하는 수를 제공합니다.  
  
> [!NOTE]
> 프로파일링 도구의 명령줄 도구는 Visual Studio 설치 디렉터리의 \Team Tools\Performance Tools 하위 디렉터리에 있습니다. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다. 자세한 내용은 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. PeopleTrax는 32비트 애플리케이션입니다.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-sampling-method"></a>샘플링 방법을 사용하여 PeopleTrax 애플리케이션을 프로파일링하려면  
  
1. PeopleTrax 샘플 애플리케이션을 설치하고 애플리케이션의 릴리스 버전을 빌드합니다.  
  
2. 명령 프롬프트 창을 열고 프로파일링 도구 디렉터리를 로컬 Path 환경 변수에 추가합니다.  
  
3. 작업 디렉터리를 PeopleTrax 이진 파일이 포함된 디렉터리로 변경합니다.  
  
4. 다음 명령을 입력하여 적절한 환경 변수를 설정합니다.  
  
    ```  
    VSPerfCLREnv /sampleon  
    ```  
  
5. 프로파일러를 제어하는 명령줄 도구인 VSPerfCmd.exe를 실행하여 프로파일링을 시작합니다. 다음 명령은 샘플링 모드에서 애플리케이션 및 프로파일러를 시작합니다.  
  
    ```  
    VsPerfCmd /start:sample /output:PeopleTraxReport.vsp /launch:PeopleTrax.exe  
    ```  
  
     프로파일러 프로세스가 시작되어 PeopleTrax.exe 프로세스에 연결됩니다. 프로파일러 프로세스가 수집된 프로파일링 데이터를 보고서 파일에 쓰기 시작합니다.  
  
6. **사용자 가져오기**를 클릭합니다.  
  
7. **ExportData**를 클릭합니다.  
  
     메모장이 열리고 **PeopleTrax**에서 내보낸 데이터가 들어 있는 새 파일이 표시됩니다.  
  
8. 메모장을 닫은 다음 **PeopleTrax** 애플리케이션을 닫습니다.  
  
9. 프로파일러를 종료합니다. 다음 명령을 입력합니다.  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
10. 다음 명령을 사용하여 환경 변수를 다시 설정합니다.  
  
    ```  
    VSPerfCLREnv /sampleoff  
    ```  
  
11. 프로파일링 데이터는 .vsp 파일에 저장됩니다. 다음 방법 중 하나를 사용하여 결과를 분석합니다.  
  
    - Visual Studio IDE에서 .vsp 파일을 엽니다.  
  
         — 또는 —  
  
    - VSPerfReport.exe 명령줄 도구를 사용하여 쉼표로 구분된 값 (.csv) 파일을 생성합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 외부에서 사용할 보고서를 생성하려면 다음 명령을 사용합니다.  
  
        ```  
        VSPerfReport <dir> PeopleTraxReport.vsp /output:<dir> /summary:all  
        ```  
  
## <a name="see-also"></a>참고 항목  
 [성능 세션 개요](../profiling/performance-session-overview.md)   
 [명령줄에서 프로 파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [샘플링 데이터 값 이해](../profiling/understanding-sampling-data-values.md)   
 [성능 보고서 뷰](../profiling/performance-report-views.md)
