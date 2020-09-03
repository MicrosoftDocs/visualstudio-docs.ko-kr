---
title: 덤프 파일 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
caps.latest.revision: 56
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1a2d6215887512f2e0c1410688b2bc924dc1fe3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387059"
---
# <a name="using-dump-files"></a>덤프 파일 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

힙을 포함하거나 포함하지 않는 덤프 파일, 덤프 파일 만들기, 덤프 파일 열기, 덤프 파일에 필요한 이진 파일, pdb 및 소스 파일 검색에 대해 설명합니다. 
  
## <a name="contents"></a><a name="BKMK_Contents"></a> 목차  
 [덤프 파일이란?](#BKMK_What_is_a_dump_file_)  
  
 [힙을 포함 하거나 포함 하지 않는 덤프 파일](#BKMK_Dump_files__with_or_without_heaps)  
  
 [요구 사항 및 제한 사항:](#BKMK_Requirements_and_limitations)  
  
 [덤프 파일 만들기](#BKMK_Create_a_dump_file)  
  
 [덤프 파일 열기](#BKMK_Open_a_dump_file)  
  
 [이진 파일, 기호(.pdb) 파일 및 소스 파일 찾기](#BKMK_Find_binaries__symbol___pdb__files__and_source_files)  
  
## <a name="what-is-a-dump-file"></a><a name="BKMK_What_is_a_dump_file_"></a> 덤프 파일 이란?  
 *덤프 파일* 은 덤프가 생성 된 시점의 앱 스냅숏입니다. 이 파일에서는 실행 중이던 프로세스와 로드된 모듈을 보여 줍니다. 덤프를 힙 정보와 함께 저장하는 경우 덤프 파일에는 해당 시점에 응용 프로그램 메모리에 있던 것의 스냅샷이 포함됩니다. Visual Studio에서 힙을 포함하는 덤프 파일을 여는 것은 디버그 세션의 중단점에서 중지하는 것과 같습니다. 실행을 계속할 수 없지만 덤프가 발생한 시간에 응용 프로그램의 스택, 스레드 및 변수 값을 검사할 수 있습니다.  
  
 덤프는 개발자가 액세스할 수 없는 컴퓨터에서 발생하는 문제를 디버깅하는 데 주로 사용됩니다. 예를 들어 컴퓨터에서 고객의 크래시 또는 응답 하지 않는 프로그램을 재현할 수 없는 경우 고객의 컴퓨터에서 덤프 파일을 사용할 수 있습니다. 테스터는 테스트 컴퓨터를 사용 하 여 더 많은 테스트를 수행할 수 있도록 크래시 또는 응답 하지 않는 프로그램 데이터를 저장 하기 위해 테스터에 의해 만들어집니다. Visual Studio 디버거는 관리 코드 또는 네이티브 코드에 대한 덤프 파일을 저장할 수 있습니다. 디버거는 Visual Studio 또는 파일을 *미니 덤프* 형식으로 저장 하는 다른 프로그램에 의해 생성 된 덤프 파일을 로드할 수 있습니다.  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> 힙을 포함 하거나 포함 하지 않는 덤프 파일  
 힙 정보를 포함하거나 포함하지 않고 덤프 파일을 만들 수 있습니다.  
  
- **힙을 사용 하는 덤프 파일** 에는 앱 메모리의 스냅숏이 포함 됩니다. 여기에는 덤프가 만들어진 시점의 변수 값이 포함됩니다. 힙과 함께 저장된 덤프 파일을 로드하는 경우에는 애플리케이션 이진 파일을 찾을 수 없더라도 Visual Studio에서 기호를 로드할 수 있습니다. 또한 Visual Studio에서는 로드된 네이티브 모듈의 이진 파일을 덤프 파일에 저장하므로 디버깅을 훨씬 쉽게 수행할 수 있습니다.  
  
- 힙이 **없는 덤프 파일** 은 힙 정보가 있는 덤프 보다 훨씬 작습니다. 그러나 디버거는 기호 정보를 찾기 위해 응용 프로그램 이진 파일을 로드해야 합니다. 이 이진 파일은 덤프가 만들어졌을 때 사용된 이진 파일과 정확히 일치해야 합니다. 스택 변수의 값만 힙 데이터를 포함하지 않는 덤프 파일에 저장됩니다.  
  
  ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> 요구 사항 및 제한 사항  
  
- 최적화된 코드의 덤프 파일 디버깅은 혼란을 줄 수 있습니다. 예를 들어 함수의 컴파일러 인라인 처리로 예기치 않은 호출 스택이 발생할 수 있으며 다른 최적화로 변수의 수명이 변경될 수 있습니다.  
  
- 64비트 컴퓨터의 덤프 파일은 64비트 컴퓨터에서 실행 중인 Visual Studio 인스턴스에서 디버깅되어야 합니다.  
  
- VS 2013 이전 버전의 Visual Studio에서는 일부 도구(예: 작업 관리자 및 64비트 WinDbg)로 수집된 64비트 컴퓨터에서 실행된 32비트 응용 프로그램의 덤프를 Visual Studio에서 열 수 없었습니다. 하지만 VS 2013에서는 이러한 제한이 사라졌습니다.  
  
- Visual Studio에서는 ARM 디바이스에서 네이티브 애플리케이션의 덤프 파일을 디버깅할 수 있습니다. 또한 Visual Studio에서는 ARM 디바이스에서 관리되는 애플리케이션의 애플리케이션 덤프 파일을 디버깅할 수 있지만 이는 네이티브 디버거에서만 가능합니다.  
  
- Visual Studio 2013에서 [커널 모드](https://msdn.microsoft.com/library/windows/hardware/ff551880.aspx) 덤프 파일을 디버그 하려면 [Windows 8.1 버전의 Windows 용 디버깅 도구](https://msdn.microsoft.com/windows/hardware/gg463009)를 다운로드 합니다. [Visual Studio의 커널 디버깅을](https://msdn.microsoft.com/library/windows/hardware/jj149675.aspx)참조 하세요.  
  
- Visual Studio는 [전체 사용자 모드 덤프](/windows-hardware/drivers/debugger/user-mode-dump-files#full)라는 이전 덤프 형식으로 저장 된 덤프 파일을 디버그할 수 없습니다. 전체 사용자 모드 덤프는 힙을 포함하는 덤프와 동일하지 않습니다.  
  
- Visual Studio에서 [SOS.dll (SOS 디버깅 확장)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498) 를 사용 하 여 디버깅 하려면 WDK (Windows 드라이버 키트)의 일부인 Windows 용 디버깅 도구를 설치 해야 합니다. [Windows 8.1 Preview: 키트, 비트 및 도구 다운로드를](https://msdn.microsoft.com/library/windows/hardware/bg127147.aspx)참조 하세요.  
  
  ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> 덤프 파일 만들기  
 Visual Studio에서 덤프 파일을 만들려면  
  
- Visual Studio에서 프로세스를 디버깅하는 동안 디버거가 예외 또는 중단점에서 중지되었을 때 덤프 파일을 저장할 수 있습니다. 다른 **이름으로 덤프 저장**, **디버그**를 선택 합니다. 다른 이름 **으로 덤프 저장** 대화 상자의 **파일 형식** 목록에서 **미니 덤프** 또는 **힙 사용 미니 덤프** (기본값)를 선택할 수 있습니다.  
  
- [Just-in-time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md) 을 사용 하는 경우 디버거 외부에서 실행 되는 충돌 하는 프로세스에 디버거를 연결한 다음 덤프 파일을 저장할 수 있습니다. [실행 중인 프로세스에 연결을](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) 참조 하세요.  
  
  또한 Windows 미니덤프 형식을 지원하는 프로그램으로 덤프 파일을 만들 수도 있습니다. 예를 들어 [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default) 의 **procdump** 명령줄 유틸리티는 트리거 또는 요청 시에 따라 프로세스 크래시 덤프 파일을 만들 수 있습니다. 다른 도구를 사용 하 여 덤프 파일을 만드는 방법에 대 한 자세한 내용은이 항목의 [요구 사항 및 제한 사항](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations) 을 참조 하세요.  
  
  ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> 덤프 파일 열기  
  
1. Visual Studio에서 **파일**, **열기**, **파일**을 차례로 선택 합니다.  
  
2. **파일 열기** 대화 상자에서 덤프 파일을 찾아 선택합니다. 덤프 파일의 확장명은 일반적으로 .dmp입니다. 그런 후 **확인**을 선택합니다.  
  
3. **덤프 파일 요약** 창이 나타납니다. 이 창에서는 덤프 파일의 디버깅 요약 정보를 보고 기호 경로를 설정하고 디버깅을 시작하고 요약 정보를 클립보드로 복사할 수 있습니다.  
  
     ![미니덤프 요약 페이지](../debugger/media/dbg-dump-summarypage.png "DBG_DUMP_SummaryPage")  
  
4. 디버깅을 시작 하려면 **작업** 섹션으로 이동 하 고 **네이티브 전용 디버그** 또는 **혼합으로 디버그**를 선택 합니다.  
  
## <a name="find-binaries-symbol-pdb-files-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> 이진 파일, 기호 (.pdb) 파일 및 소스 파일 찾기  
 덤프 파일을 디버깅하기 위해 Visual Studio의 전체 기능을 사용하려면 다음에 액세스해야 합니다.  
  
- 덤프가 만들어진 .exe 파일과 덤프 프로세스에서 사용된 다른 이진 파일(DLL 등)  
  
   힙 데이터를 포함하는 덤프를 디버깅하는 경우 Visual Studio에서는 일부 모듈의 누락된 이진 파일 문제를 처리할 수 있지만 유효한 호출 스택을 생성하는 데 충분한 모듈의 이진 파일이 있어야 합니다. Visual Studio에서는 힙을 포함하는 덤프 파일에 네이티브 모듈을 포함합니다.  
  
- .exe 및 기타 이진 파일에 대한 기호(.pdb) 파일  
  
- 관심 있는 모듈의 소스 파일  
  
   실행 파일과 .pdb 파일은 덤프가 만들어졌을 때 사용된 파일의 버전 및 빌드와 정확히 일치해야 합니다.  
  
   소스 파일을 찾을 수 없는 경우 모듈의 디스어셈블리를 사용하여 디버깅할 수 있습니다.  
  
  **실행 파일의 기본 검색 경로**  
  
  Visual Studio에서는 덤프 파일에 포함되지 않은 실행 파일을 다음 위치에서 자동으로 검색합니다.  
  
1. 덤프 파일이 포함된 디렉터리  
  
2. 덤프 파일에서 지정된 모듈의 경로. 덤프가 수집된 컴퓨터의 모듈 경로입니다.  
  
3. Visual Studio **도구**, **옵션** 대화 상자의 **디버깅**, **옵션**, **기호** 페이지에 지정 된 기호 경로입니다. 이 페이지에서 검색할 위치를 더 추가할 수 있습니다.  
  
   **이진 파일/기호/소스 없음 페이지 사용**  
  
   Visual Studio에서 덤프의 모듈을 디버깅 하는 데 필요한 파일을 찾을 수 없는 경우 적절 한 페이지 (**이진 파일 없음**, **기호 없음**또는 **소스 없음**)를 표시 합니다. 이러한 페이지에서는 문제의 원인에 대한 자세한 정보를 제공하고 파일의 올바른 위치를 식별하는 데 도움이 되는 작업 링크를 제공합니다. [기호 (.pdb) 및 소스 파일 지정을](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)참조 하세요.  
  
   ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="see-also"></a>관련 항목  
 [Just-in-time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [기호 (.pdb) 및 소스 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [IntelliTrace](../debugger/intellitrace.md)
