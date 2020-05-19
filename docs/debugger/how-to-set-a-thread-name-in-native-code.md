---
title: '방법: 네이티브 코드에 스레드 이름 설정 | Microsoft Docs'
ms.date: 12/17/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 1e719563c831c50cc325d70d0de431f4be1bf514
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911424"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>방법: 네이티브 코드에 스레드 이름 설정
스레드 명명 기능은 Visual Studio의 모든 버전에서 사용할 수 있습니다. 스레드 이름 지정은 실행 중인 프로세스를 디버그할 때 **스레드** 창에서 원하는 스레드를 식별하는 데 유용합니다. 쉽게 알 수 있는 이름이 지정된 스레드를 포함하는 것은 크래시 덤프 검사를 통해 사후 평가 디버깅을 수행할 경우 및 다양한 도구를 사용하여 성능 캡처를 분석할 경우 유용할 수 있습니다.

## <a name="ways-to-set-a-thread-name"></a>스레드 이름을 설정하는 방법

스레드 이름을 설정하는 방법에는 두 가지가 있습니다. 첫 번째는 [SetThreadDescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) 함수를 사용하는 것입니다. 두 번째는 Visual Studio 디버거가 프로세스에 연결되는 동안 특정 예외를 throw하는 것입니다. 각 접근 방식에는 이점과 주의 사항이 있습니다. `SetThreadDescription` 사용은 Windows 10 버전 1607 또는 Windows Server 2016부터 지원됩니다.

접근 방식의 작동 메커니즘은 서로 독립적이므로 접근 방식을 ‘둘 다’ 함께 사용할 수 있습니다.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>`SetThreadDescription`을 사용하여 스레드 이름 설정

혜택:
* SetThreadDescription이 호출될 때 디버거가 프로세스에 연결되었는지 여부와 관계없이 Visual Studio에서 디버그할 때 스레드 이름이 표시됩니다.
* Visual Studio에서 크래시 덤프를 로드하여 사후 평가 디버깅을 수행할 때 스레드 이름이 표시됩니다.
* [WinDbg](/windows-hardware/drivers/debugger/debugger-download-tools) 디버거 및 [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer) 성능 분석기와 같은 다른 도구를 사용하는 경우에도 스레드 이름이 표시됩니다.

주의 사항:
* 스레드 이름은 Visual Studio 2017 버전 15.6 이상 버전에서만 표시됩니다.
* 사후 평가에서 크래시 덤프 파일을 디버그할 때 Windows 10 버전 1607, Windows Server 2016 이상 버전의 Windows에서 크래시가 생성된 경우에만 스레드 이름이 표시됩니다.

*예제:*

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

### <a name="set-a-thread-name-by-throwing-an-exception"></a>예외를 throw하여 스레드 이름 설정

프로그램에서 스레드 이름을 설정하는 또 다른 방법은 특별 구성된 예외를 throw하여 원하는 스레드 이름을 Visual Studio 디버거에 전달하는 것입니다.

혜택:
* 모든 버전의 Visual Studio에서 작동합니다.

주의 사항:
* 예외 기반 메서드가 사용될 때 디버거가 연결되는 경우에만 작동합니다.
* 이 방법을 사용하여 설정된 스레드 이름은 덤프 또는 성능 분석 도구에서 사용할 수 없습니다.

*예제:*

아래 표시된 `SetThreadName` 함수는 이 예외 기반 접근 방식을 보여 줍니다. `threadName` 호출이 완료된 후 `SetThreadName` 매개 변수의 메모리가 해제될 수 있도록 스레드 이름은 자동으로 스레드에 복사됩니다.

```C++
//
// Usage: SetThreadName ((DWORD)-1, "MainThread");
//
#include <windows.h>
const DWORD MS_VC_EXCEPTION = 0x406D1388;
#pragma pack(push,8)
typedef struct tagTHREADNAME_INFO
{
    DWORD dwType; // Must be 0x1000.
    LPCSTR szName; // Pointer to name (in user addr space).
    DWORD dwThreadID; // Thread ID (-1=caller thread).
    DWORD dwFlags; // Reserved for future use, must be zero.
} THREADNAME_INFO;
#pragma pack(pop)
void SetThreadName(DWORD dwThreadID, const char* threadName) {
    THREADNAME_INFO info;
    info.dwType = 0x1000;
    info.szName = threadName;
    info.dwThreadID = dwThreadID;
    info.dwFlags = 0;
#pragma warning(push)
#pragma warning(disable: 6320 6322)
    __try{
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);
    }
    __except (EXCEPTION_EXECUTE_HANDLER){
    }
#pragma warning(pop)
}
```

## <a name="see-also"></a>참조
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
- [방법: 관리 코드에 스레드 이름 설정](../debugger/how-to-set-a-thread-name-in-managed-code.md)
