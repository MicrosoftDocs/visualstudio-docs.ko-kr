---
title: '방법: 관리 코드에서 여러 스레드 관리 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe5cef9f7aebcbfc93ffd057a109647e45b5967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387072"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>방법: 관리 코드에서 여러 스레드 관리
비동기 메서드를 호출 하거나 Visual Studio UI 스레드가 아닌 스레드에서 실행 되는 작업을 포함 하는 관리 되는 VSPackage 확장이 있는 경우 아래 제공 된 지침을 따라야 합니다. 다른 스레드의 작업이 완료 될 때까지 기다릴 필요가 없기 때문에 UI 스레드 응답성을 유지할 수 있습니다. 스택 공간을 차지 하는 추가 스레드가 없으므로 코드를 보다 효율적으로 만들 수 있으며, 교착 상태와 응답 하지 않는 코드를 방지 하기 때문에 더 안정적이 고 쉽게 디버깅할 수 있습니다.

 일반적으로 UI 스레드에서 다른 스레드로 전환 하거나 그 반대로 전환할 수 있습니다. 메서드가 반환 될 때 현재 스레드는 원래 호출 된 스레드입니다.

> [!IMPORTANT]
> 다음 지침에서는 네임 스페이스의 Api 인 <xref:Microsoft.VisualStudio.Threading> 특히 클래스를 사용 합니다 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . 이 네임 스페이스의 Api는의 새로운 Api [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] 입니다. 속성에서의 인스턴스를 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory` .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>UI 스레드에서 백그라운드 스레드로 전환

1. UI 스레드를 사용 하 고 백그라운드 스레드에서 비동기 작업을 수행 하려는 경우 다음을 사용 합니다 `Task.Run()` .

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. UI 스레드를 사용 중이 고 백그라운드 스레드에서 작업을 수행 하는 동안 동기적으로 차단 하려는 경우에는 내에서 속성을 사용 합니다 <xref:System.Threading.Tasks.TaskScheduler> `TaskScheduler.Default` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> .

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>백그라운드 스레드에서 UI 스레드로 전환

1. 백그라운드 스레드를 사용 하 고 UI 스레드에서 작업을 수행 하려는 경우 다음을 사용 합니다 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> .

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     메서드를 사용 하 여 <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> UI 스레드로 전환할 수 있습니다. 이 메서드는 현재 비동기 메서드의 연속을 사용 하 여 UI 스레드에 메시지를 게시 하 고, 나머지 스레딩 프레임 워크와 통신 하 여 올바른 우선 순위를 설정 하 고 교착 상태를 방지 합니다.

     백그라운드 스레드 메서드가 비동기가 아니며 비동기 상태로 만들 수 없는 경우에도 `await` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> 다음 예제와 같이 구문을 사용 하 여 작업을로 래핑하여 UI 스레드로 전환할 수 있습니다.

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
