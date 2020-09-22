---
title: '연습: 계측을 사용하여 명령줄 프로파일링 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
- performance tools, command-line tools
ms.assetid: 1c6f1586-3d6a-431f-bedf-c54088e280ba
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3a37350cf274fbb551326ac96387330b0f3956e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841982"
---
# <a name="walkthrough-command-line-profiling-using-instrumentation"></a>연습: 계측을 사용하여 명령줄 프로파일링
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 프로파일링 도구의 계측 방법을 사용하여 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 독립 실행형 애플리케이션을 프로파일링해 자세한 타이밍 및 호출 수 데이터를 수집하는 과정을 안내합니다. 이 연습에서는 다음 작업을 수행합니다.  
  
- [VSInstr](../profiling/vsinstr.md) 명령줄 도구를 사용하여 계측된 이진 파일을 생성합니다.  
  
- [VSPerfCLREnv](../profiling/vsperfclrenv.md) 도구를 사용하여 .NET 프로파일링 데이터를 수집하도록 환경 변수를 설정합니다.  
  
- [VSPerfCmd](../profiling/vsperfcmd.md) 도구를 사용하여 프로파일링 데이터를 수집합니다.  
  
- [VSPerfReport](../profiling/vsperfreport.md) 도구를 사용하여 프로파일링 데이터의 파일 기반 보고서를 생성합니다.  
  
## <a name="prerequisites"></a>전제 조건  
  
- [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]  
  
- C#에 대한 중간 정도의 이해도  
  
- 명령줄 도구 사용법에 대한 중간 정도의 이해도  
  
- [PeopleTrax 샘플](../profiling/peopletrax-sample-profiling-tools.md) 의 복사본  
  
- 프로파일링을 통해 제공되는 정보를 사용하려면 디버깅 기호 정보를 준비해 두는 것이 가장 좋습니다. 자세한 내용은 [방법: Windows 기호 정보 참조](../profiling/how-to-reference-windows-symbol-information.md)를 참조 하세요.  
  
## <a name="command-line-profiling-using-the-instrumentation-method"></a>계측 방법을 사용하여 명령줄 프로파일링  
 계측은 계측된 모듈의 함수에 대한 진입 및 종료 시 타이밍 정보를 수집하는 프로브 함수를 특수하게 작성된 버전의 프로파일링된 이진 파일에 포함할 수 있는 프로파일링 방법입니다. 이 프로파일링 방법은 샘플링보다 침입성이 높으므로오버헤드가 더 많이 발생합니다. 계측된 이진 파일도 디버그 또는 릴리스 이진 파일보다 더 크므로 배포할 수 없습니다.  
  
> [!NOTE]
> 고객에게는 계측된 이진 파일을 전송하지 마세요. 계측된 이진 파일에는 여러 가지 위험 요소가 포함될 수 있습니다. 이진 파일에는 애플리케이션을 보다 쉽게 리버스 엔지니어링할 수 있도록 만드는 정보와 보안 위험이 포함되어 있습니다.  
  
#### <a name="to-profile-the-peopletrax-application-by-using-the-instrumentation-method"></a>계측 방법을 사용하여 PeopleTrax 애플리케이션을 프로파일링하려면  
  
1. PeopleTrax 샘플 애플리케이션을 설치하고 릴리스 버전을 빌드합니다.  
  
2. 명령 프롬프트 창을 열고 **프로파일링 도구** 디렉터리를 로컬 Path 환경 변수에 추가합니다.  
  
3. 작업 디렉터리를 PeopleTrax 이진 파일이 포함된 디렉터리로 변경합니다.  
  
4. 파일 기반 보고서를 포함할 디렉터리를 만듭니다. 다음 명령을 입력합니다.  
  
    ```  
    md Reports  
    ```  
  
5. VSInstr 명령줄 도구를 사용하여 애플리케이션의 이진 파일을 계측합니다. 별도의 명령줄에서 다음 명령을 입력합니다.  
  
    ```  
    VSInstr PeopleTrax.exe  
    VSInstr PeopleTrax.exe  
    VSInstr People.dll  
    VSInstr Person.dll  
    VSInstr Operation.dll  
    ```  
  
     **참고** 기본적으로 VSInstr은 원본 파일의 계측되지 않은 백업을 저장합니다. 백업 파일 이름의 확장명은 .orig입니다 예를 들어 원본 버전 "MyApp.exe"는 "MyApp.exe.orig"로 저장됩니다.  
  
6. 다음 명령을 입력하여 적절한 환경 변수를 설정합니다.  
  
    ```  
    VsPerfCLREnv /traceon  
    ```  
  
7. 프로파일러를 시작하려면 다음 명령을 입력합니다.  
  
    ```  
    VsPerfCmd /start:trace /output:Reports\Report.vsp  
    ```  
  
8. 프로파일러를 추적 모드에서 시작한 후 PeopleTrax.exe 프로세스의 계측된 버전을 실행하여 데이터를 수집합니다.  
  
     **PeopleTrax** 애플리케이션 창이 나타납니다.  
  
9. **사용자 가져오기**를 클릭합니다.  
  
     PeopleTrax 데이터 표에 데이터가 채워집니다.  
  
10. **데이터 내보내기**를 클릭합니다.  
  
     메모장이 시작되고 **PeopleTrax** 애플리케이션의 사용자 목록이 들어 있는 새 파일이 표시됩니다.  
  
11. 메모장을 닫은 다음 **PeopleTrax** 애플리케이션을 닫습니다.  
  
12. 프로파일러를 종료합니다. 다음 명령을 입력합니다.  
  
    ```  
    VSPerfCmd /shutdown  
    ```  
  
13. 다음 명령을 입력하여 환경 변수를 다시 설정합니다.  
  
    ```  
    VSPerfCLREnv /off  
    ```  
  
14. VSPerfReport 도구를 사용하여 쉼표로 구분된 값(.csv) 보고서 파일을 생성합니다. 유형:  
  
    ```  
    VSPerfReport Reports\Report.vsp /output:Reports /summary:all  
    ```  
  
     스프레드시트 응용 프로그램에서 생성된 보고서를 분석하거나, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE를 사용하여 Report.vsp 파일에서 프로파일링 데이터를 분석할 수 있습니다. 자세한 내용은 [성능 도구 데이터 분석](../profiling/analyzing-performance-tools-data.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [성능 세션 개요](../profiling/performance-session-overview.md)   
 [명령줄에서 프로 파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [샘플링 데이터 값 이해](../profiling/understanding-sampling-data-values.md)   
 [성능 보고서 뷰](../profiling/performance-report-views.md)
