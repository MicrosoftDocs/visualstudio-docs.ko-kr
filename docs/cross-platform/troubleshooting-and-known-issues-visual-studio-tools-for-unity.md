---
title: 문제 해결 및 알려진 문제(VS Tools for Unity)
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d6856ff73f9aab2325a31e164e7983a919097d46
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "66261122"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>문제 해결 및 알려진 문제(Visual Studio Tools for Unity)

이 섹션에서는 Visual Stuio Tools for Unity와 관련된 일반적인 문제에 대한 솔루션, 알려진 문제의 설명을 찾아보고 오류를 보고하여 Visual Studio Tools for Unity를 개선하는 데 도움이 되는 방법을 알아봅니다.

## <a name="troubleshooting-the-connection-between-unity-and-visual-studio"></a>Unity와 Visual Studio 간의 연결 문제 해결

### <a name="confirm-editor-attaching-is-enabled"></a>편집기 연결이 사용하도록 설정되어 있는지 확인

Unity 메뉴에서 **편집 > 기본 설정**을 선택한 다음, **외부 도구** 탭을 선택합니다. **편집기 연결** 확인 상자가 사용하도록 설정되어 있는지 확인합니다. 자세한 내용은 [Unity 기본 설정 설명서](https://docs.unity3d.com/Manual/Preferences.html)를 참조하세요.

### <a name="unable-to-attach"></a>연결할 수 없음

- VS 및 Unity 모두에 대해 바이러스 백신을 일시적으로 사용하지 않도록 설정하거나 제외 규칙을 만들어 봅니다.
- 방화벽을 일시적으로 사용하지 않도록 설정하거나 VS와 Unity 간에 TCP/UDP 네트워킹을 허용하는 규칙을 만들어 봅니다.
- Team Viewer와 같은 일부 프로그램은 프로세스 검색을 방해할 수 있습니다. 임시로 추가 소프트웨어를 중지하여 변경 내용이 있는지 확인할 수 있습니다.
- VSTU가 "Unity.exe" 프로세스를 모니터링하는 경우 기본 Unity 실행 파일의 이름을 바꾸지 않습니다.

## <a name="visual-studio-crashes"></a>Visual Studio 크래시

이 문제는 Visual Studio MEF 캐시가 손상되었기 때문에 발생할 수 있습니다.

MEF 캐시를 다시 설정하려면 다음 폴더를 제거해 보세요. 먼저 Visual Studio를 닫은 후에 이 작업을 수행하세요.

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

이렇게 하면 문제가 해결됩니다. 문제가 여전히 발생하는 경우 관리자 권한으로 Visual Studio용 개발자 명령 프롬프트를 실행하고 다음 명령을 사용합니다.

```batch
 devenv /setup
```

## <a name="visual-studio-hangs"></a>Visual Studio 중지

Parse, FMOD, UMP(Universal Media Player), ZFBrowser 또는 Embedded Browser와 같이 몇 가지 Unity 플러그 인은 네이티브 스레드를 사용합니다. 플러그인에서 네이티브 스레드를 런타임에 연결할 때 발생하는 문제이며, 이는 OS에 대한 호출을 차단합니다. 즉 Unity에서 디버거(또는 도메인 다시 로드)에 대한 해당 스레드를 중단하고 정지할 수 없습니다.

FMOD의 경우 일시적인 해결 방법이 있습니다. 즉, `FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE` 초기화 [플래그](https://www.fmod.com/resources/documentation-studio?version=2.0&page=https://fmod.com/resources/documentation-api?version=2.0&page=studio-api-system.html#fmod_studio_initflags)를 전달하여 비동기 처리를 비활성화하고 주 스레드에서 모든 처리를 수행할 수 있습니다.

## <a name="incompatible-project-in-visual-studio"></a>Visual Studio에서 호환되지 않는 프로젝트

먼저 Unity에서 Visual Studio가 외부 스크립트 편집기로 설정되어 있는지 확인합니다(편집/기본 설정/외부 도구). 다음으로 Unity에 Visual Studio 플러그인이 설치되어 있는지 확인합니다(도움말/정보에 Microsoft Visual Studio Tools for Unity와 같은 메시지가 표시되어야 함). 다음으로 확장이 Visual Studio에 제대로 설치되어 있는지 확인합니다(도움말/정보).

## <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>추가 다시 로드 또는 열린 모든 창이 손실되는 Visual Studio

자산 처리기나 다른 도구에서 프로젝트 파일을 직접 터치하지 마십시오. 프로젝트 파일을 정말로 조작해야 하는 경우 API를 사용하는 것이 좋습니다. [어셈블리 참조 문제 섹션](#assembly-reference-issues)을 참조하세요.

다시 로드가 추가로 발생하거나 Visual Studio에서 다시 로드 시 열려 있는 창이 모두 손실되면 적절한 .NET 타기팅 팩이 설치되어 있는지 확인해야 합니다. 자세한 내용은 프레임워크에 대한 다음 섹션을 참조하세요.

## <a name="the-debugger-does-not-break-on-exceptions"></a>디버거가 예외 발생 시 중단되지 않음

레거시 Unity 런타임(.NET 3.5와 동일)을 사용할 때 예외가 처리되지 않으면 디버거가 항상 중단됩니다(=try/catch 블록 외부에서). 예외가 처리되면 디버거는 예외 설정 창을 사용하여 중단이 필요한지 여부를 결정합니다.

새 런타임(.NET 4.6과 동일)을 통해 Unity에 사용자 예외를 관리하는 새로운 방법이 도입되었기 때문에 모든 예외가 try/catch 블록 외부에 있어도 "사용자 처리"로 표시됩니다. 따라서 디버거를 중단하려면 예외 설정 창에서 명시적으로 디버거를 확인해야 합니다.

예외 설정 창(디버그 > 창 > 예외 설정)에서 예외 범주(예: .NET 예외를 의미하는 공용 언어 런타임 예외)에 대한 노드를 확장하고 해당 범주 내에서 catch하려는 특정 예외(예: System.NullReferenceException)에 대한 확인란을 선택합니다. 전체 예외 범주를 선택할 수도 있습니다.

## <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>Windows에서 Visual Studio는 Unity 대상 프레임워크를 다운로드하도록 요청합니다.

Visual Studio Tools for Unity를 사용하려면 Windows 8 또는 10에 기본적으로 설치되지 않는 .NET Framework 3.5가 필요합니다. 이 문제를 해결하려면 지침에 따라 .NET framework 3.5를 다운로드하고 설치하세요.

새로운 Unity 런타임을 사용하는 경우 .NET 타기팅 팩 버전 4.6 및 4.7.1도 필요합니다. VS2017 설치 관리자를 사용하여 신속하게 설치할 수 없습니다(VS2017 설치, 개별 구성 요소, .NET 범주 수정, 모든 4.x 타기팅 팩 선택).

## <a name="assembly-reference-issues"></a>어셈블리 참조 문제

프로젝트가 복잡한 전체 참조이거나 이 생성 단계를 더 잘 제어하려는 경우 [API](../cross-platform/customize-project-files-created-by-vstu.md)를 사용하여 생성된 프로젝트 또는 솔루션 콘텐츠를 조작할 수 있습니다. Unity 프로젝트에서 [응답 파일](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)을 사용할 수도 있으며, 이렇게 처리할 예정입니다.

## <a name="breakpoints-with-a-warning"></a>경고가 있는 중단점

Visual Studio에서 특정 중단점에 대한 원본 위치를 찾을 수 없는 경우 중단점 주변에 경고가 표시됩니다. 사용하는 스크립트가 현재 Unity 장면에 제대로 로드/사용되었는지 확인합니다.

## <a name="breakpoints-not-hit"></a>적중되지 않는 중단점

사용하는 스크립트가 현재 Unity 장면에 제대로 로드/사용되었는지 확인합니다. Visual Studio와 Unity를 모두 종료한 다음, 생성된 모든 파일(\*.csproj, \*.sln)과 전체 라이브러리 폴더를 삭제합니다.

## <a name="unable-to-debug-android-players"></a>Android 플레이어를 디버그할 수 없음

플레이어 검색(Unity에서 사용하는 기본 메커니즘)에 멀티캐스트를 사용하지만, 이후에는 일반 TCP 연결을 사용하여 디버거를 연결합니다. 검색 단계는 Android 디바이스에 대한 주요 문제입니다.

Wi-Fi는 유용하지만 대기 시간 때문에 USB에 비해 속도가 느립니다. 일부 라우터 또는 디바이스에 대해 적절한 멀티캐스트 지원이 부족하다는 것을 확인했습니다(Nexus 시리즈는 이에 대해 잘 알려져 있음).

USB는 디버깅하기에 매우 빠릅니다. 이제 Visual Studio Tools for Unity에서 USB 디바이스를 감지할 수 있고 디버깅을 위해 adb 서버와 통신하여 포트를 올바르게 전달할 수 있습니다.

## <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Visual Studio 2015 및 IntelliSense 또는 코드 색 지정 관련 문제입니다.

Visual Studio 2015를 업데이트 3으로 업그레이드해 보세요.

## <a name="known-issues"></a>알려진 문제

 Visual Studio Tools for Unity에는 디버거가 C# 컴파일러의 Unity 이전 버전과 상호작용하는 방법에서 발생하는 알려진 문제가 있습니다. 문제를 해결하기 위해 노력 중이지만 해결하기 전까지 다음과 같은 문제가 발생할 수 있습니다.

- 디버그할 때 Unity가 충돌되는 경우가 있습니다.

- 디버그할 때 Unity가 중지되는 경우가 있습니다.

- 특히 반복기 또는 switch 문 내에서 경우에 따라 메서드를 한 단계씩 코드 실행하고 메서드의 프로시저에서 나가는 동작이 제대로 작동하지 않습니다.

## <a name="report-errors"></a>오류 보고

 충돌, 고정 또는 기타 오류가 발생하는 경우 오류 보고서를 전송하여 Visual Studio Tools for Unity의 품질을 개선할 수 있도록 도와주시기 바랍니다. Visual Studio Tools for Unity의 문제를 조사하고 해결하는 데 도움이 됩니다. 감사합니다!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Visual Studio가 고정될 때 오류를 보고하는 방법

 Visual Studio가 Visual Studio Tools for Unity로 디버그할 때 중지되는 경우가 있다는 보고가 있지만 이 문제를 파악하려면 더 많은 데이터가 필요합니다. 아래의 단계를 따라 이 문제를 조사하는 데 도움을 주실 수 있습니다.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Visual Studio가 Visual Studio Tools for Unity로 디버그할 때 중지되는 문제를 보고하려면

*Windows:*

1. 새 Visual Studio 인스턴스를 엽니다.

1. 프로세스에 연결 대화 상자를 엽니다. Visual Studio의 새 인스턴스에 있는 주 메뉴에서 **디버그**, **프로세스에 연결**을 선택합니다.

1. Visual Studio의 중지된 인스턴스에 디버거를 연결합니다. **프로세스에 연결** 대화 상자에서 **사용 가능한 프로세스** 테이블로부터 Visual Studio의 중지된 인스턴스를 선택한 다음 **연결** 단추를 선택합니다.

1. 디버거를 일시 중지합니다. Visual Studio의 새 인스턴스에 있는 주 메뉴에서 **디버그**, **모두 중단**을 차례로 선택하거나 **Ctrl+Alt+Break**를 누르기만 하면 됩니다.

1. 스레드 덤프를 만듭니다. [명령] 창에서 다음 명령을 입력하고 **Enter** 키를 누릅니다.

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    **명령** 창이 먼저 표시되도록 해야 할 수 있습니다. Visual Studio의 주 메뉴에서 **보기**, **다른 창**, **명령 창**을 선택합니다.

*Mac:*

1. 터미널을 열고 Mac용 Visual Studio의 PID를 가져옵니다.

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. lldb 디버거를 시작합니다.

    ```shell
    lldb
    ```

1. PID를 사용하여 Mac용 Visual Studio 인스턴스에 연결합니다.

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. 모든 스레드에 대한 스택 추적을 검색합니다.

    ```shell
    bt all
    ```

마지막으로 Visual Studio가 중지되었을 때 수행한 작업에 대한 설명과 함께 스레드 덤프를 [vstusp@microsoft.com](mailto:vstusp@microsoft.com)으로 보냅니다.
