---
title: 디버거에서 덤프 파일 사용 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/05/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.crashdump
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- dumps, about dumps
- crash dumps
- dump files
- dumps
ms.assetid: b71be6dc-57e0-4730-99d2-b540a0863e49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db6d4e8bc5b2f09194e03bbadc8f49b773d24f1e
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386955"
---
# <a name="dump-files-in-the-visual-studio-debugger"></a>Visual Studio 디버거의 덤프 파일

<a name="BKMK_What_is_a_dump_file_"></a> *덤프 파일*은 실행 중인 프로세스 및 특정 시점에 앱에 대해 로드된 모듈을 보여주는 스냅샷입니다. 힙 정보가 있는 덤프에는 해당 시점의 앱 메모리 스냅샷도 포함됩니다.

Visual Studio에서 힙을 포함하는 덤프 파일을 여는 것은 디버그 세션의 중단점에서 중지하는 것과 같습니다. 실행을 계속할 수 없지만 덤프 시 앱의 스택, 스레드 및 변수 값을 검사할 수 있습니다.

덤프는 개발자가 액세스할 수 없는 머신에서 발생하는 문제를 디버깅하는 데 주로 사용됩니다. 크래시 또는 응답하지 않는 프로그램을 자신의 머신에서 재현할 수 없는 경우 고객의 머신에서 덤프 파일을 사용할 수 있습니다. 또한 테스터는 추가 테스트에 사용할 크래시 또는 응답하지 않는 프로그램 데이터를 저장하는 덤프를 만듭니다.

Visual Studio 디버거는 관리 코드 또는 네이티브 코드에 대한 덤프 파일을 저장할 수 있습니다. Visual Studio 또는 파일을 *미니덤프* 형식으로 저장하는 다른 앱에서 만든 덤프 파일을 디버그할 수 있습니다.

## <a name="requirements-and-limitations"></a><a name="BKMK_Requirements_and_limitations"></a> 요구 사항 및 제한 사항

- 64비트 머신에서 덤프 파일을 디버그하려면 Visual Studio가 64비트 머신에서 실행되고 있어야 합니다.

- Visual Studio에서는 ARM 디바이스에서 네이티브 애플리케이션의 덤프 파일을 디버깅할 수 있습니다. 또한 ARM 디바이스에서 관리형 앱의 덤프를 디버그할 수 있지만 이는 네이티브 디버거에서만 가능합니다.

- Visual Studio에서 [커널 모드](/windows-hardware/drivers/debugger/kernel-mode-dump-files) 덤프 파일을 디버그하거나 [SOS.dll](/dotnet/framework/tools/sos-dll-sos-debugging-extension) 디버깅 확장을 사용하려면 [WDK(Windows 드라이버 키트)](/windows-hardware/drivers/download-the-wdk)에서 Windows용 디버깅 도구를 다운로드합니다.

- Visual Studio에서는 [전체 사용자 모드 덤프](/windows/desktop/wer/collecting-user-mode-dumps) 형식으로 저장된 덤프 파일을 디버그할 수 없습니다. 전체 사용자 모드 덤프는 힙이 있는 덤프와 동일하지 않습니다.

- 최적화된 코드의 덤프 파일 디버깅은 혼란을 줄 수 있습니다. 예를 들어 함수의 컴파일러 인라인 처리로 예기치 않은 호출 스택이 발생할 수 있으며 다른 최적화로 변수의 수명이 변경될 수 있습니다.

## <a name="dump-files-with-or-without-heaps"></a><a name="BKMK_Dump_files__with_or_without_heaps"></a> 힙을 포함하거나 포함하지 않는 덤프 파일

덤프 파일에는 힙 정보가 있거나 없을 수 있습니다.

- **힙이 있는 덤프 파일**에는 덤프 시 변수 값을 비롯하여 앱 메모리의 스냅샷이 포함되어 있습니다. 또한 Visual Studio에서는 로드된 네이티브 모듈의 이진 파일을 힙이 있는 덤프 파일에 저장하므로 디버깅을 훨씬 쉽게 수행할 수 있습니다. Visual Studio는 앱 이진 파일을 찾을 수 없는 경우에도 힙이 있는 덤프 파일에서 기호를 로드할 수 있습니다.

- **힙이 없는 덤프 파일**은 힙이 있는 덤프보다 훨씬 작지만 디버거는 앱 이진 파일을 로드하여 기호 정보를 찾아야 합니다. 로드된 이진 파일은 덤프를 만드는 동안 실행되는 이진 파일과 정확히 일치해야 합니다. 힙 없는 덤프 파일은 스택 변수의 값만 저장합니다.

## <a name="create-a-dump-file"></a><a name="BKMK_Create_a_dump_file"></a> 덤프 파일 만들기

Visual Studio에서 프로세스를 디버깅하는 동안 디버거가 예외 또는 중단점에서 중지되었을 때 덤프를 저장할 수 있습니다.

[Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)을 사용하면 Visual Studio 디버거를 Visual Studio 외부에서 충돌된 프로세스에 연결한 다음, 더버거에서 덤프 파일을 저장할 수 있습니다. [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조하세요.

**덤프 파일을 저장하려면**

1. 디버깅 중 오류 또는 중단점에서 중지된 동안 **디버그** > **다른 이름으로 덤프 저장**을 선택합니다.

1. **다른 이름으로 덤프 저장** 대화 상자의 **파일 형식으로 저장**에서 **미니덤프** 또는 **힙이 있는 미니덤프**(기본값)를 선택합니다.

1. 경로를 찾아 덤프 파일의 이름을 선택한 다음, **저장**을 선택합니다.

>[!NOTE]
>Windows 미니덤프 형식을 지원하는 프로그램으로 덤프 파일을 만들 수 있습니다. 예를 들어 [Windows Sysinternals](https://technet.microsoft.com/sysinternals/default)에 있는 **Procdump** 명령줄 유틸리티는 트리거에 따라서나 요청 시에 프로세스 크래시 덤프 파일을 만들 수 있습니다. 기타 도구를 사용하여 덤프 파일을 만드는 방법에 대한 정보는 [요구 사항 및 제한 사항](../debugger/using-dump-files.md#BKMK_Requirements_and_limitations)을 참조하세요.

## <a name="open-a-dump-file"></a><a name="BKMK_Open_a_dump_file"></a> 덤프 파일 열기

1. Visual Studio에서 **파일** > **열기** > **파일**을 선택합니다.

1. **파일 열기** 대화 상자에서 덤프 파일을 찾아 선택합니다. 덤프 파일의 확장명은 일반적으로 *.dmp*입니다. **확인**을 선택합니다.

   **미니덤프 파일 요약** 창에는 덤프 파일에 대한 요약 및 모듈 정보와 수행할 수 있는 작업이 표시됩니다.

   ![미니덤프 요약 페이지](../debugger/media/dbg_dump_summarypage.png "미니덤프 요약 페이지")

1. **작업**에서 다음을 수행합니다.
   - 기호 로드 위치를 설정하려면 **기호 경로 설정**을 선택합니다.
   - 디버깅을 시작하려면 **관리 전용으로 디버그**, **네이티브 전용으로 디버그**, **혼합 디버그** 또는 **관리되는 메모리로 디버그**를 선택합니다.

## <a name="find-exe-pdb-and-source-files"></a><a name="BKMK_Find_binaries__symbol___pdb__files__and_source_files"></a> .exe, .pdb 및 원본 파일 찾기

덤프 파일에서 전체 디버깅 기능을 사용하려면 Visual Studio에 다음이 필요합니다.

- 덤프가 만들어진 *.exe* 파일과 덤프 프로세스가 사용하는 기타 이진 파일(DLL 등)입니다.
- *.exe* 및 기타 이진 파일에 대한 기호( *.pdb*) 파일
- 덤프 생성 시 파일의 버전 및 빌드와 정확히 일치하는 *.exe* 및 *.pdb* 파일입니다.
- 관련 모듈의 원본 파일입니다. 원본 파일을 찾을 수 없는 경우 모듈의 디스어셈블리를 사용할 수 있습니다.

덤프에 힙 데이터가 있는 경우 Visual Studio에서는 일부 모듈의 누락된 이진 파일 문제를 처리할 수 있지만 유효한 호출 스택을 생성하는 데 충분한 모듈의 이진 파일이 있어야 합니다.

### <a name="search-paths-for-exe-files"></a>.exe 파일의 경로 검색

Visual Studio에서는 덤프 파일에 포함되지 않은 *.exe* 파일을 다음 위치에서 자동으로 검색합니다.

1. 덤프 파일이 포함된 폴더입니다.
2. 덤프 파일이 지정하는 모듈 경로는 덤프를 수집한 머신의 모듈 경로입니다.
3. **도구**(또는 **디버그**) > **옵션** > **디버깅** > **기호**에 저정된 기호 경로입니다. **덤프 파일 요약** 창의 **작업** 창에서 **기호** 페이지를 열 수도 있습니다. 이 페이지에서 검색할 위치를 더 추가할 수 있습니다.

### <a name="use-the-no-binary-no-symbols-or-no-source-found-pages"></a>이진 파일 없음, 기호 없음 또는 소스를 찾을 수 없음 페이지를 사용합니다.

Visual Studio에서는 덤프의 모듈을 디버깅하는 데 필요한 파일을 찾을 수 없는 경우 **이진 파일 없음**, **기호 없음** 또는 **소스 없음** 페이지를 표시합니다. 이러한 페이지에서는 문제의 원인에 대한 자세한 정보를 제공하고 파일을 찾는 데 도움이 되는 작업 링크를 제공합니다. [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

## <a name="see-also"></a>참조

- [Just-In-Time 디버깅](../debugger/just-in-time-debugging-in-visual-studio.md)
- [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [IntelliTrace](../debugger/intellitrace.md)