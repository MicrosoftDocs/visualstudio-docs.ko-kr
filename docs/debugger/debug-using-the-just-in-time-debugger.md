---
title: Just-In-Time 디버거를 사용하여 디버그 | Microsoft Docs
ms.date: 09/24/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b842fa4ce7c75e061a58d980cefe5648094c2ef7
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188675"
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Visual Studio에서 Just-In-Time 디버거를 사용하여 디버그

Just-In-Time 디버깅은 Visual Studio 외부에서 실행 중인 앱에 오류 또는 충돌이 발생하면 Visual Studio를 자동으로 시작할 수 있습니다. Just-In-Time 디버깅을 사용하면 Visual Studio 외부의 앱을 테스트하고, 문제가 발생하는 경우 Visual Studio를 열어 디버깅을 시작할 수 있습니다.

Just-In-Time 디버깅은 Windows 데스크톱 앱에서 작동합니다. 유니버설 Windows 앱 또는 시각화 도우미와 같은 네이티브 애플리케이션에 호스팅된 관리 코드에는 작동하지 않습니다.

> [!TIP]
> Just-In-Time 디버거 대화 상자가 나타나지 않게 하고 Visual Studio가 설치되지 않은 경우 [Just-In-Time 디버거 사용 안 함](../debugger/just-in-time-debugging-in-visual-studio.md)을 참조하세요. Visual Studio를 설치한 후에는 [Windows 레지스트리에서 Just-In-Time 디버깅을 사용하지 않도록 설정](#disable-just-in-time-debugging-from-the-windows-registry)해야 할 수 있습니다.

## <a name="enable-or-disable-just-in-time-debugging-in-visual-studio"></a><a name="BKMK_Enabling"></a> Visual Studio에서 Just-In-Time 디버깅 사용 또는 사용 안 함

>[!NOTE]
>Just-in-time 디버깅을 사용하거나 사용하지 않도록 설정하려면 관리자 권한으로 Visual Studio를 실행해야 합니다. Just-In-Time 디버깅을 사용하거나 사용하지 않도록 설정하면 레지스트리 키가 설정되며 해당 키를 변경하려면 관리자 권한이 필요할 수 있습니다. Visual Studio를 관리자 권한으로 열려면 Visual Studio 앱을 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 선택합니다.

Visual Studio **도구** > **옵션**(또는 **디버그** > **옵션**) 대화 상자에서 Just-In-Time 디버깅을 구성할 수 있습니다.

**Just-In-Time 디버깅을 활성화하거나 비활성화하려면:**

1. **도구** 또는 **디버그** 메뉴에서 **옵션** > **디버깅** > **Just-In-Time**을 선택합니다.

   ![JIT 디버깅 사용 또는 사용 안 함](../debugger/media/dbg-jit-enable-or-disable.png "JIT 디버깅 사용 또는 사용 안 함")

1. **이러한 코드 형식에 Just-In-Time 디버깅 사용** 상자에서 Just-In-Time 디버깅이 디버그할 코드 형식을 선택합니다. **관리**, **네이티브** 및/또는 **스크립트**.

1. **확인**을 선택합니다.

Just-In-Time 디버거를 사용하도록 설정했지만 앱이 충돌하거나 오류가 발생할 때 열리지 않으면 [Just-In-Time 디버깅 문제 해결](#jit_errors)을 참조하세요.

## <a name="disable-just-in-time-debugging-from-the-windows-registry"></a>Windows 레지스트리에서 Just-In-Time 디버깅 비활성화

컴퓨터에 Visual Studio가 더 이상 설치되어 있지 않아도 Just-In-Time 디버깅은 계속 활성화되어 있습니다. Visual Studio가 더 이상 설치되어 있지 않으면 Windows 레지스트리를 편집하여 Just-In-Time 디버깅을 비활성화할 수 있습니다.

**레지스트리를 편집하여 Just-In-Time 디버깅을 비활성화하려면:**

1. Windows **시작** 메뉴에서 **레지스트리 편집기**(*regedit.exe*)를 실행합니다.

2. **레지스트리 편집기** 창에서 다음 레지스트리 항목을 찾아 삭제합니다.

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    ![JIT 레지스트리 키](../debugger/media/dbg-jit-registry.png "JIT 레지스트리 키")

3. 컴퓨터가 64비트 운영 체제에서 실행되는 경우에는 다음 레지스트리 항목도 삭제합니다.

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger**

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger**

    다른 레지스트리 키를 삭제하거나 변경하지 않도록 해야 합니다.

5. **레지스트리 편집기** 창을 닫습니다.

## <a name="enable-just-in-time-debugging-of-a-windows-form"></a>Windows Form의 Just-In-Time 디버깅 사용

기본적으로 Windows Forms 앱에는 복구할 수 있는 경우 앱을 계속 실행할 수 있도록 하는 최상위 예외 처리기가 있습니다. Windows Forms 앱이 처리되지 않은 예외를 throw하는 경우 다음과 같은 대화 상자가 표시됩니다.

![Windows Form 처리되지 않은 예외](../debugger/media/windowsformsunhandledexception.png "Windows Form 처리되지 않은 예외")

표준 Windows Form 오류 처리 대신 Just-In-Time 디버깅을 사용하도록 설정하려면 다음 설정을 추가합니다.

- *machine.config* 또는 *\<app name>.exe.config* 파일의 `system.windows.forms` 섹션에서 `jitDebugging` 값을 `true`로 설정합니다.

    ```xml
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

- C++ Windows Forms 애플리케이션의 경우 *.config* 파일 또는 코드에서 `DebuggableAttribute`를 `true`로 설정합니다. [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format)만 사용하고 [/Og](/cpp/build/reference/og-global-optimizations)는 사용하지 않은 상태에서 컴파일하면 컴파일러에서 이 특성을 자동으로 설정합니다. 그러나 최적화되지 않은 릴리스 빌드를 디버그하려면 앱의 *AssemblyInfo.cpp* 파일에 다음 줄을 추가하여 `DebuggableAttribute`를 설정해야 합니다.

   ```cpp
   [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
   ```

   자세한 내용은 <xref:System.Diagnostics.DebuggableAttribute>를 참조하세요.

## <a name="use-just-in-time-debugging"></a><a name="BKMK_Using_JIT"></a>Just-In-Time 디버깅 사용
이 예제에서는 앱에서 오류를 throw할 때 Just-In-Time 디버깅을 안내합니다.

- 이러한 단계를 수행하려면 Visual Studio가 설치되어 있어야 합니다. Visual Studio가 없는 경우 체험판 [Visual Studio Community Edition](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)을 다운로드할 수 있습니다.

- **도구** > **옵션** > **디버깅** > **Just-In-Time**에서 Just-In-Time 디버깅을 [사용하도록 설정](#BKMK_Enabling)해야 합니다.

이 예제에서는 Visual Studio에서 [NullReferenceException](/dotnet/api/system.nullreferenceexception)을 throw하는 C# 콘솔 앱을 만듭니다.

1. Visual Studio에서 *ThrowsNullException*이라는 C# 콘솔 앱(**파일** > **새로 만들기** > **프로젝트** > **Visual C#**  > **콘솔 애플리케이션**)을 만듭니다. Visual Studio에서 프로젝트를 만드는 방법에 대한 자세한 내용은 [연습: 간단한 애플리케이션 만들기](../get-started/csharp/tutorial-wpf.md)를 참조하세요.

1. Visual Studio에서 프로젝트가 열리면 *Program.cs* 파일을 엽니다. Main() 메서드를 콘솔에 줄을 출력한 다음, NullReferenceException을 throw하는 다음 코드로 바꿉니다.

   ```csharp
   static void Main(string[] args)
   {
       Console.WriteLine("we will now throw a NullReferenceException");
       throw new NullReferenceException("this is the exception thrown by the console app");
   }
   ```

1. 솔루션을 빌드하려면 **디버그**(기본값) 또는 **릴리스** 구성 중 하나를 선택한 다음, **빌드** > **솔루션 다시 빌드**를 선택합니다.

   > [!NOTE]
   > - 전체 디버깅 환경에 대한 **디버그** 구성을 선택합니다.
   > - [릴리스](../debugger/how-to-set-debug-and-release-configurations.md) 구성을 선택하는 경우 이 절차를 수행하려면 [내 코드만](../debugger/just-my-code.md)을 해제해야 합니다. **도구** > **옵션** > **디버깅**에서 **내 코드만 사용**을 선택 취소합니다.

   빌드 구성에 대한 자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md)를 참조하세요.

1. C# 프로젝트 폴더( *...\ThrowsNullException\ThrowsNullException\bin\Debug* 또는 *...\ThrowsNullException\ThrowsNullException\bin\Release*)에서 빌드된 앱 *ThrowsNullException.exe*를 엽니다.

   다음 명령 창이 표시됩니다.

   ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

1. **Just-In-Time 디버거 선택** 대화 상자가 열립니다.

   ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

   **사용 가능한 디버거**에서 **\<기본 설정된 Visual Studio 버전/에디션>의 새 인스턴스**를 선택합니다(아직 선택하지 않은 경우).

1. **확인**을 선택합니다.

   ThrowsNullException 프로젝트는 예외를 throw한 줄에서 실행이 중지되는 Visual Studio의 새 인스턴스에서 열립니다.

   ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

이 지점에서 디버깅을 시작할 수 있습니다. 실제 앱을 디버깅하는 경우 코드에서 예외를 throw하는 이유를 확인해야 합니다.

> [!CAUTION]
> 앱에 신뢰할 수 없는 코드가 포함된 경우 디버깅을 계속할지 여부를 결정할 수 있는 보안 경고 대화 상자가 나타납니다. 디버깅을 계속하기 전에 코드를 신뢰할 수 있는지 확인해야 합니다. 직접 작성한 코드인지, 애플리케이션이 원격 컴퓨터에서 실행 중인 경우 프로세스 이름을 알 수 있는지 등을 확인합니다. 앱이 로컬로 실행 중인 경우 컴퓨터에서 악성 코드가 실행될 가능성을 고려합니다. 코드를 신뢰할 수 있다고 판단되면 **확인**을 선택합니다. 그렇지 않으면 **취소**를 선택합니다.

## <a name="troubleshoot-just-in-time-debugging"></a><a name="jit_errors"></a> Just-In-Time 디버깅 문제 해결

Visual Studio에서 앱을 사용하도록 설정했지만 앱이 충돌할 때 Just-In-Time 디버깅이 시작되지 않는 경우:

- Windows 오류 보고가 컴퓨터의 오류 처리를 대신할 수 있습니다.

  이 문제를 해결하려면 레지스트리 편집기를 사용하여 **값 데이터**가 **1**인 **DWORD 값**을 **사용 안함**으로 다음 레지스트리에 추가합니다.

  - **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\Windows 오류 보고**

  - (64비트 머신의 경우): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows\Windows 오류 보고**

  자세한 내용은 [.WER 설정](/windows/desktop/wer/wer-settings)을 참조하세요.

- 알려진 Windows 문제로 인해 Just-In-Time 디버거가 실패할 수 있습니다.

  이 문제를 해결하려면 **값 데이터**가 **1**인 **DWORD 값**을 **자동**으로 다음 레지스트리 키에 추가합니다.

  - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug**

  - (64비트 머신의 경우): **HKEY_LOCAL_MACHINE\Software\WOW6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug**

Just-In-Time 디버깅 중에 다음 오류 메시지가 표시될 수 있습니다.

- **충돌 프로세스에 연결할 수 없습니다. 지정한 프로그램은 Windows 또는 MS-DOS 프로그램이 아닙니다.**

    디버거가 다른 사용자로 실행 중인 프로세스에 연결하려고 했습니다.

    이 문제를 해결하려면 Visual Studio에서 **디버그** > **프로세스에 연결**을 열고 **사용 가능한 프로세스** 목록에서 디버깅할 프로세스를 찾습니다. 프로세스 이름을 모르는 경우에는 **Visual Studio Just-In-Time 디버거** 대화 상자에서 프로세스 ID를 찾습니다. **사용 가능한 프로세스** 목록에서 프로세스를 선택하고 **연결**을 선택합니다. **아니요**를 선택하여 Just-In-Time 디버거 대화 상자를 닫습니다.

- **로그온한 사용자가 없으므로 디버거를 시작할 수 없습니다.**

    콘솔에 로그온한 사용자가 없으므로 Just-In-Time 디버깅 대화 상자를 표시할 사용자 세션이 없습니다.

    이 문제를 해결하려면 컴퓨터에 로그온합니다.

- **클래스가 등록되지 않았습니다.**

    디버거가 설치 문제로 인해 등록되지 않은 COM 클래스를 만들려고 했습니다.

    이 문제를 해결하려면 Visual Studio 설치 관리자를 사용하여 Visual Studio 설치를 다시 설치하거나 복구합니다.

## <a name="see-also"></a>참조

- [디버거 보안](../debugger/debugger-security.md)
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [옵션, 디버깅, Just-In-Time 대화 상자](../debugger/just-in-time-debugging-options-dialog-box.md)
- [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결하면 위험할 수 있습니다. 아래의 정보가 의심스럽거나 잘 모르겠으면 이 프로세스에 연결하지 마세요.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)
