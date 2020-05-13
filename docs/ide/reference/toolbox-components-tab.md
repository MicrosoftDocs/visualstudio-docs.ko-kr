---
title: 도구 상자, 구성 요소 탭
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5eb8c320a3190121d95395f7b359aa9ed978408
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597310"
---
# <a name="toolbox-components-tab"></a>도구 상자, 구성 요소 탭

Windows Forms용 Visual Basic 및 C# 디자이너에 추가할 수 있는 구성 요소를 표시합니다. <xref:System.Messaging.MessageQueue> 및 <xref:System.Diagnostics.EventLog> 구성 요소와 같이 Visual Studio에 함께 제공되는 .NET 구성 요소 이외에 사용자 지정 또는 타사 구성 요소를 이 탭에 추가할 수 있습니다.

이 탭을 표시하려면 Windows Forms 디자이너를 엽니다. **보기** > **도구 상자**를 선택합니다. **도구 상자**에서 **구성 요소** 탭을 선택합니다.

## <a name="components"></a>구성 요소

**BackgroundWorker**

작업을 별도의 전용 스레드에서 실행할 수 있는 <xref:System.ComponentModel.BackgroundWorker> 구성 요소를 만듭니다. 자세한 내용은 [BackgroundWorker 구성 요소](/dotnet/framework/winforms/controls/backgroundworker-component)를 참조하세요.

**DirectoryEntry**

Active Directory 서비스 공급자를 조작하는 데 사용될 수 있고 Active Directory 계층 구조의 노드 또는 개체를 캡슐화하는 <xref:System.DirectoryServices.DirectoryEntry> 구성 요소 인스턴스를 만듭니다.

**DirectorySearcher**

Active Directory에 대해 쿼리를 실행하는 데 사용할 수 있는 <xref:System.DirectoryServices.DirectorySearcher> 구성 요소 인스턴스를 만듭니다.

**ErrorProvider**

최종 사용자에게 양식의 컨트롤에 관련 오류가 있음을 나타내는 <xref:System.Windows.Forms.ErrorProvider> 구성 요소 인스턴스를 만듭니다. 자세한 내용은 [ErrorProvider 구성 요소](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms)를 참조하세요.

**EventLog**

로그에 이벤트 쓰기 및 로그 데이터 읽기와 같이 시스템 및 사용자 지정 이벤트 로그를 조작하는 데 사용할 수 있는 <xref:System.Diagnostics.EventLog> 구성 요소 인스턴스를 만듭니다.

**FileSystemWatcher**

액세스 권한을 가진 디렉터리 또는 파일이 변경되었는지 모니터링하는 데 사용할 수 있는 <xref:System.IO.FileSystemWatcher> 구성 요소 인스턴스를 만듭니다.

**HelpProvider**

컨트롤에 대한 팝업 또는 온라인 도움말을 제공하는 <xref:System.Windows.Forms.HelpProvider> 구성 요소 인스턴스를 만듭니다. 자세한 내용은 [HelpProvider 구성 요소](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms)를 참조하세요.

**ImageList**

<xref:System.Windows.Forms.ImageList> 개체 컬렉션을 관리하는 메서드를 제공하는 <xref:System.Drawing.Image> 구성 요소 인스턴스를 만듭니다. 자세한 내용은 [ImageList 구성 요소](/dotnet/framework/winforms/controls/imagelist-component-windows-forms)를 참조하세요.

**MessageQueue**

큐에서 메시지 읽기, 큐에 메시지 쓰기, 트랜잭션 처리, 큐 관리 작업 수행과 같이 메시지 큐를 조작하는 데 사용할 수 있는 <xref:System.Messaging.MessageQueue> 구성 요소 인스턴스를 만듭니다.

**PerformanceCounter**

새 범주 및 인스턴스 만들기, 카운터에서 값 읽기, 카운터 데이터에 대한 계산 수행과 같이 Windows 성능 카운터를 조작하는 데 사용할 수 있는 <xref:System.Diagnostics.PerformanceCounter> 구성 요소 인스턴스를 만듭니다.

**처리**

시스템의 프로세스와 연결된 데이터를 중지, 시작, 조작하는 데 사용할 수 있는 <xref:System.Diagnostics.Process> 구성 요소 인스턴스를 만듭니다.

**SerialPort**

동기 및 이벤트 구동 I/O, 핀 및 중단 상태에 대한 액세스, 직렬 드라이버 속성에 대한 액세스를 제공하는 <xref:System.IO.Ports.SerialPort> 구성 요소 인스턴스를 만듭니다.

**ServiceController**

서비스 시작 및 중지, 서비스에 명령 보내기와 같이 기존 서비스를 조작하는 데 사용할 수 있는 <xref:System.ServiceProcess.ServiceController> 구성 요소 인스턴스를 만듭니다.

**타이머**

Windows 기반 애플리케이션에 시간 기반 기능을 추가하는 데 사용할 수 있는 <xref:System.Windows.Forms.Timer> 구성 요소 인스턴스를 만듭니다. 자세한 내용은 [Timer 구성 요소](/dotnet/framework/winforms/controls/timer-component-windows-forms)를 참조하세요.

> [!NOTE]
> <xref:System.Timers.Timer>도구 상자**에 추가할 수 있는 시스템 기반** 도 있습니다. 이 <xref:System.Timers.Timer>는 서버 애플리케이션에 최적화되어 있고 Windows Forms <xref:System.Windows.Forms.Timer>는 Windows Forms에 가장 적합합니다.

## <a name="see-also"></a>참고 항목

- [Windows Forms에 사용할 수 있는 컨트롤](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [도구 상자 항목 선택, WPF 구성 요소](choose-toolbox-items-wpf-components.md)
- [도구 상자](../../ide/reference/toolbox.md)
