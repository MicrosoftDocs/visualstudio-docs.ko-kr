---
title: Just-In-Time 디버깅
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
- CSharp
- VB
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 51
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ad2814dffa75809a318dc7cebe7831b5ecec7d29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690601"
---
# <a name="just-in-time-debugging-in-visual-studio"></a>Visual Studio에서 Just-In-Time 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 외부에서 실행 되는 응용 프로그램에서 예외 또는 충돌이 발생 하면 just-in-time 디버깅을 통해 Visual Studio가 자동으로 시작 됩니다. 이를 통해 Visual Studio가 실행 되 고 있지 않을 때 응용 프로그램을 테스트 하 고, 문제가 발생 하면 Visual Studio를 사용 하 여 디버깅을 시작할 수 있습니다.

Just-In-Time 디버깅은 Windows 데스크톱 앱에서 작동합니다. Windows 유니버설 앱에서는 작동 하지 않으며 시각화 도우미와 같은 네이티브 응용 프로그램에서 호스팅되는 관리 코드에 대해서는 작동 하지 않습니다.

## <a name="did-the-just-in-time-debugger-dialog-box-appear-when-trying-to-run-an-app"></a><a name="BKMK_Scenario"></a> 앱을 실행 하려고 할 때 Just-in-time 디버거 대화 상자가 표시 되나요?

Visual Studio Just-in-time debugger 대화 상자가 표시 되는 경우 수행 하려는 작업에 따라 수행 해야 하는 작업은 다음과 같습니다.

#### <a name="if-you-want-to-get-rid-of-the-dialog-box-and-just-run-the-app-normally"></a>대화 상자를 제거 하 고 앱을 정상적으로 실행 하려면

1. (고급 사용자) Visual Studio가 설치 되어 있거나 이전에 설치 하 고 제거한 경우 [just-in-time 디버깅을 사용 하지 않도록 설정](#BKMK_Enabling) 하 고 앱을 다시 실행 해 봅니다.

2. Internet Explorer에서 웹 앱을 실행 하는 경우 스크립트 디버깅을 사용 하지 않도록 설정 합니다.

    인터넷 옵션 대화 상자에서 스크립트 디버깅을 사용 하지 않도록 설정 합니다. **제어판**  /  **네트워크 및 인터넷**인터넷 옵션에서이에 액세스할 수 있습니다  /  **Internet Options** (정확한 단계는 Windows 및 internet Explorer 버전에 따라 달라 짐).

    ![JITInternetOptions](../debugger/media/jitinternetoptions.png "JITInternetOptions")

3. 오류가 발견 된 웹 페이지를 다시 엽니다. 그래도 문제가 해결 되지 않으면 웹 앱 소유자에 게 문의 하 여 문제를 해결 하십시오.

4. 다른 유형의 Windows 앱을 실행 중인 경우 응용 프로그램의 소유자에 게 문의 하 여 오류를 해결 한 다음, 앱의 고정 버전을 다시 설치 해야 합니다.

#### <a name="if-you-want-to-fix-or-debug-the-error-advanced-users"></a>오류를 수정 하거나 디버깅 하려면 (고급 사용자)

- 오류에 대 한 자세한 정보를 확인 하 고 디버깅을 시도 하려면 [Visual Studio가 설치](https://visualstudio.microsoft.com/vs/older-downloads/) 되어 있어야 합니다. 자세한 지침은 [JIT 사용](#BKMK_Using_JIT) 을 참조 하세요. 오류를 해결 하 고 앱을 수정할 수 없는 경우 앱 소유자에 게 문의 하 여 오류를 해결 하십시오.

## <a name="enable-or-disable-just-in-time-debugging"></a><a name="BKMK_Enabling"></a> Just-in-time 디버깅 사용 또는 사용 안 함
 Visual Studio **도구/옵션** 대화 상자에서 just-in-time 디버깅을 사용 하거나 사용 하지 않도록 설정할 수 있습니다.

#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Just-In-Time 디버깅을 활성화하거나 비활성화하려면

1. Visual Studio를 엽니다. **도구** 메뉴에서 **옵션**을 클릭합니다.

2. **옵션** 대화 상자에서 **디버깅** 폴더를 선택 합니다.

3. **디버깅** 폴더에서 **just-in-time** 페이지를 선택 합니다.

4. **이러한 형식의 코드에 just-in-time 디버깅 사용** 상자에서 **관리**, **네이티브**또는 **스크립트**와 관련 된 프로그램 유형을 선택 하거나 선택 취소 합니다.

    활성화되어 있는 Just-In-Time 디버깅을 비활성화하려면 프로그램을 관리자 권한으로 실행해야 합니다. Just-In-Time 디버깅을 활성화하면 레지스트리 키가 설정되고 이 키를 변경하려면 관리자 권한이 있어야 합니다.

5. **확인**을 클릭합니다.

   컴퓨터에 Visual Studio가 더 이상 설치되어 있지 않아도 Just-In-Time 디버깅은 계속 활성화되어 있습니다. Visual Studio가 설치 되어 있지 않으면 Visual Studio **옵션** 대화 상자에서 just-in-time 디버깅을 사용 하지 않도록 설정할 수 없습니다. 이 경우 Windows 레지스트리를 편집하여 Just-In-Time 디버깅을 비활성화할 수 있습니다.

#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>레지스트리를 편집하여 Just-In-Time 디버깅을 비활성화하려면

1. **시작** 메뉴에서를 검색 하 고 실행 합니다.`regedit.exe`

2. **레지스트리 편집기** 창에서 다음 레지스트리 항목을 찾아 삭제 합니다.

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\DbgManagedDebugger

3. 컴퓨터에서 64 비트 운영 체제를 실행 하는 경우 다음 레지스트리 항목도 삭제 합니다.

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger

    - HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\DbgManagedDebugger

4. 실수로 다른 레지스트리 키를 삭제하거나 변경하지 않도록 주의합니다.

5. **레지스트리 편집기** 창을 닫습니다.

> [!NOTE]
> 서버 쪽 앱에 대 한 Just-in-time 디버깅을 사용 하지 않도록 설정 하려는 경우 이러한 단계를 수행 해도 문제가 해결 되지 않으면 IIS 응용 프로그램 설정에서 서버 쪽 디버깅을 해제 하 고 다시 시도 합니다.

#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Windows Form에 Just-In-Time 디버깅을 사용하려면

1. 기본적으로 Windows Forms 애플리케이션에는 복구할 수 있는 경우 프로그램을 계속 실행할 수 있도록 하는 최상위 예외 처리기가 있습니다. 예를 들어 Windows Forms 응용 프로그램이 처리 되지 않은 예외를 throw 하는 경우 다음과 같은 대화 상자가 표시 됩니다.

     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")

     Windows Forms 응용 프로그램에 대 한 Just-in-time 디버깅을 사용 하도록 설정 하려면 다음과 같은 추가 단계를 수행 해야 합니다.

2. `jitDebugging` `true` `system.windows.form` machine.config 또는.exe.config 파일의 섹션에서 값을로 설정 합니다 *\<application name>* .

    ```
    <configuration>
        <system.windows.forms jitDebugging="true" />
    </configuration>
    ```

3. C++ Windows Forms 애플리케이션의 경우 .config 파일이나 코드에서 `DebuggableAttribute`도 설정해야 합니다. [/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)만 사용하고 [/Og](https://msdn.microsoft.com/library/d10630cc-b9cf-4e97-bde3-8d7ee79e9435)는 사용하지 않은 상태에서 컴파일하면 컴파일러에서 이 특성을 자동으로 설정합니다. 그러나 최적화되지 않은 릴리스 빌드를 디버깅하려면 이 특성을 직접 설정해야 합니다. 애플리케이션의 AssemblyInfo.cpp 파일에 다음 줄을 추가하여 이 특성을 설정할 수 있습니다.

    ```
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];
    ```

     자세한 내용은 <xref:System.Diagnostics.DebuggableAttribute>를 참조하세요.

## <a name="a-namebkmk_using_jituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Just-in-time 디버깅 사용
 이 섹션에서는 실행 파일이 예외를 throw 할 때 발생 하는 상황을 보여 줍니다.

 이러한 단계를 수행하려면 Visual Studio가 설치되어 있어야 합니다. Visual Studio가 없는 경우 무료 [Visual studio 2015 Community Edition](https://visualstudio.microsoft.com/vs/older-downloads/)을 다운로드할 수 있습니다.

 Visual Studio를 설치하면 Just-In-Time 디버깅이 기본적으로 활성화됩니다.

 이 섹션에서는를 throw 하는 c # 콘솔 앱을 Visual Studio에서 만듭니다 <xref:System.NullReferenceException> .

 Visual Studio에서 **ThrowsNullException**라는 c # 콘솔 앱 (**파일/새로 만들기/프로젝트/c #/콘솔 응용 프로그램**)을 만듭니다. Visual Studio에서 프로젝트를 만드는 방법에 대 한 자세한 내용은 [연습: 간단한 응용 프로그램 만들기](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)를 참조 하세요.

 Visual Studio에서 프로젝트가 열리면 Program.cs 파일을 엽니다. Main() 메서드를 콘솔에 줄을 출력한 다음, NullReferenceException을 throw하는 다음 코드로 바꿉니다.

```csharp
static void Main(string[] args)
{
    Console.WriteLine("we will now throw a NullReferenceException");
    throw new NullReferenceException("this is the exception thrown by the console app");
}
```

> [!IMPORTANT]
> 이 절차가 [릴리스 구성](../debugger/how-to-set-debug-and-release-configurations.md)에서 작동 하려면 [내 코드만](../debugger/just-my-code.md)해제 해야 합니다. Visual Studio에서 **도구/옵션**을 클릭 합니다. **옵션** 대화 상자에서 **디버깅**을 선택 합니다. **내 코드만 사용**에서 확인을 제거 합니다.

 솔루션을 빌드합니다 (Visual Studio에서 **솔루션 빌드/다시**빌드를 선택). 디버그 또는 릴리스 구성을 선택할 수 있습니다. 빌드 구성에 대 한 자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md)를 참조 하세요.

 빌드 프로세스는 실행 파일 ThrowsNullException.exe를 만듭니다. C # 프로젝트를 만든 폴더 ( **. ..\ThrowsNullException\ThrowsNullException\bin\Debug** 또는 **. ..\ThrowsNullException\ThrowsNullException\bin\Release**)에서 찾을 수 있습니다.

 ThrowsNullException.exe를 두 번 클릭 합니다. 다음과 같은 명령 창이 표시 됩니다.

 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")

 몇 초 후에 오류 창이 나타납니다.

 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")

 **취소**를 클릭 하지 마십시오. 몇 초 후에 **디버그** 및 **닫기 프로그램**이라는 두 가지 단추가 표시 됩니다. **디버그**를 클릭 합니다.

> [!CAUTION]
> 응용 프로그램에 신뢰할 수 없는 코드가 포함 되어 있으면 보안 경고가 있는 대화 상자가 나타납니다. 이 대화 상자에서 디버깅을 계속할지 여부를 결정할 수 있습니다. 디버깅을 계속하기 전에 코드를 신뢰할 수 있는지 확인해야 합니다. 직접 작성한 코드인지, 코드 작성자를 신뢰할 수 있는지, 애플리케이션이 원격 컴퓨터에서 실행 중인 경우 프로세스 이름을 알 수 있는지 등을 확인합니다. 애플리케이션이 로컬로 실행 중이라고 해서 반드시 신뢰할 수 있는 것은 아닙니다. 악의적인 코드가 컴퓨터에서 실행 될 가능성을 고려 합니다. 디버깅 하려는 코드가 신뢰할 수 있는 것으로 판단 되 면 **디버그**를 클릭 합니다. 그렇지 않으면 **디버그 안 함**을 클릭 합니다.

 **Visual Studio Just-in-time Debugger** 창이 표시 됩니다.

 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")

 **가능한 디버거에서** **Microsoft Visual Studio 2015 줄의 새 인스턴스가** 선택 되어 있는 것을 확인할 수 있습니다. 아직 선택 하지 않은 경우 지금 선택 합니다.

 창의 아래쪽에서 **선택한 디버거를 사용 하 여 디버깅**하 시겠습니까?에서 **예**를 클릭 합니다.

 ThrowsNullException 프로젝트는 Visual Studio의 새 인스턴스에서 열리고, 예외를 throw 하는 줄에서 실행이 중지 됩니다.

 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")

 이 지점에서 디버깅을 시작할 수 있습니다. 실제 응용 프로그램의 경우 코드에서 예외를 throw 하는 이유를 확인 해야 합니다.

## <a name="just-in-time-debugging-errors"></a>Just-In-Time 디버깅 오류
 프로그램이 충돌 하는 경우 대화 상자가 표시 되지 않으면 컴퓨터의 설정이 Windows 오류 보고 때문일 수 있습니다. 자세한 내용은을 참조 하십시오 [. WER 설정](https://msdn.microsoft.com/library/windows/desktop/bb513638\(v=vs.85\).aspx).

 Just-In-Time 디버깅과 관련된 다음 오류 메시지가 나타날 수도 있습니다.

- **충돌 프로세스에 연결할 수 없습니다. 지정한 프로그램은 Windows 또는 MS-DOS 프로그램이 아닙니다.**

     이 오류는 다른 사용자로 실행 중인 프로세스에 연결 하려고 할 때 발생 합니다.

     이 문제를 해결 하려면 Visual Studio를 시작 하 고 **디버그** 메뉴에서 **프로세스에 연결** 대화 상자를 연 다음 **사용 가능한 프로세스** 목록에서 디버깅할 프로세스를 찾습니다. 프로세스 이름을 모르는 경우에는 **Visual Studio Just-in-time Debugger** 대화 상자에서 프로세스 ID를 확인 합니다. **사용 가능한 프로세스** 목록에서 프로세스를 선택 하 고 **연결**을 클릭 합니다. **Visual Studio Just-in-time Debugger** 대화 상자에서 **아니요** 를 클릭 하 여 대화 상자를 닫습니다.

- **로그온한 사용자가 없으므로 디버거를 시작할 수 없습니다.**

     이 오류는 콘솔에 로그온한 사용자가 없는 컴퓨터에서 Just-In-Time 디버깅 시 Visual Studio를 시작하려고 할 때 발생합니다. 로그온한 사용자가 없으므로 Just-In-Time 디버깅 대화 상자를 표시할 사용자 세션이 없습니다.

     이 문제를 해결하려면 컴퓨터에 로그온합니다.

- **클래스가 등록되지 않았습니다.**

     이 오류는 설치 문제 등으로 인해 등록되지 않은 COM 클래스를 디버거에서 만들려고 했음을 의미합니다.

     이 문제를 해결하려면 설치 디스크를 사용하여 Visual Studio를 다시 설치하거나 Visual Studio 설치를 복구합니다.

## <a name="see-also"></a>관련 항목
 [디버거 보안](../debugger/debugger-security.md) [디버거 기본 사항](../debugger/debugger-basics.md) [Just-in-time 디버깅, 옵션 대화 상자](../debugger/just-in-time-debugging-options-dialog-box.md) [보안 경고: 신뢰할 수 없는 사용자가 소유한 프로세스에 연결 하는 것은 위험할 수 있습니다. 다음 정보가 의심 스 럽 거 나 잘 모르겠으면이 프로세스에 연결 하지 마십시오](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015) .
