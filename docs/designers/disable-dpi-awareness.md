---
title: Visual Studio에서 DPI 인식 사용 안 함
description: HDPI 모니터에 대한 Windows Forms 디자이너의 제한 사항 및 Visual Studio를 DPI를 인식하지 않는 프로세스로 실행하는 방법에 대해 설명합니다.
ms.date: 04/05/2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.topic: conceptual
ms.openlocfilehash: 8e7a5a5871b66fd388d7c5a9f774a22163d06729
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589567"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Visual Studio에서 DPI 인식 사용 안 함

Visual Studio는 DPI 인식 애플리케이션으로, 이를 통해 디스플레이 배율이 자동으로 조정됩니다. 애플리케이션에서 DPI를 인식하지 못하는 경우 운영 체제는 애플리케이션을 비트맵으로 확장합니다. 이 동작을 DPI 가상화라고도 합니다. 애플리케이션은 여전히 100% 배율 또는 96dpi로 실행되고 있다고 생각합니다.

이 문서에서는 HDPI 모니터에 대한 Windows Forms 디자이너의 제한 사항 및 Visual Studio를 DPI를 인식하지 않는 프로세스로 실행하는 방법에 대해 설명합니다.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>HDPI 모니터의 Windows Forms 디자이너

Visual Studio의 **Windows Forms 디자이너**는 크기 조정을 지원하지 않습니다. 따라서 HDPI 모니터의 **Windows Forms 디자이너**에서 일부 양식을 열 때 문제가 표시됩니다. 예를 들어 다음 이미지와 같이 컨트롤이 겹칠 수 있습니다.

![HDPI 모니터의 Windows Forms 디자이너](./media/win-forms-designer-hdpi.png)

HDPI 모니터의 Visual Studio에서 **Windows Forms 디자이너**의 양식을 열면 Visual Studio는 디자이너 맨 위에 노란색 알림 표시줄을 표시합니다.

![DPI를 인식하지 않는 모드로 다시 시작하기 위한 Visual Studio의 알림 표시줄](./media/scaling-gold-bar.png)

메시지 내용은 다음과 같습니다. **기본 화면의 배율은 200%(192dpi)로 설정됩니다. 이로 인해 디자이너 창에서 렌더링 문제가 발생할 수 있습니다.**

> [!NOTE]
> 이 알림 표시줄은 Visual Studio 2017 버전 15.8에서 도입되었습니다.

디자이너에서 작업하지 않고 양식의 레이아웃을 조정하지 않아도 되는 경우에는 알림 표시줄을 무시하고 코드 편집기나 다른 유형의 디자이너에서 작업을 계속할 수 있습니다. ([알림을 사용하지 않도록 설정](#disable-notifications)하여 알림 표시줄이 계속 나타나지 않게 할 수도 있습니다.) **Windows Forms 디자이너**에만 영향을 미칩니다. **Windows Forms 디자이너**에서 작업해야 하는 경우 다음 섹션을 통해 [문제를 해결](#to-resolve-the-display-problem)할 수 있습니다.

## <a name="to-resolve-the-display-problem"></a>화면 표시 문제를 해결하려면

화면 표시 문제를 해결하기 위한 세 가지 옵션이 있습니다.

- [Visual Studio를 DPI를 인식하지 않는 프로세스로 다시 시작](#restart-visual-studio-as-a-dpi-unaware-process)
- [레지스트리 항목 추가](#add-a-registry-entry)
- [화면 표시 배율 설정을 100%로 설정](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Visual Studio를 DPI를 인식하지 않는 프로세스로 다시 시작

노란색 알림 표시줄에서 옵션을 선택하여 Visual Studio를 DPI를 인식하지 않는 프로세스로 다시 시작할 수 있습니다. 이것은 문제를 해결하는 기본 방법입니다.

Visual Studio가 DPI를 인식하지 않는 프로세스로 실행되면 디자이너 레이아웃 문제가 해결되지만 글꼴이 흐리게 표시될 수 있습니다. Visual Studio는 DPI를 인식하지 않는 프로세스로 실행될 때 다음과 같이 노란색 알림 메시지를 표시합니다. **Visual Studio가 DPI를 인식하지 않는 프로세스로 실행됩니다. WPF 및 XAML 디자이너가 제대로 표시되지 않을 수 있습니다.** 알림 표시줄에는 **Visual Studio를 DPI 인식 프로세스로 다시 시작**하는 옵션도 제공됩니다.

> [!NOTE]
> - DPI를 인식하지 않는 프로세스를 다시 시작하는 옵션을 선택하고 Visual Studio에서 도구 창을 도킹 해제한 경우 해당 도구 창의 위치가 변경될 수 있습니다.
> - 기본 Visual Basic 프로필을 사용하는 경우 또는 **도구** > **옵션** > **프로젝트 및 솔루션**에서 **만들어질 때 새 프로젝트 저장** 옵션을 선택 취소한 경우 Visual Studio는 DPI를 인식하지 않는 프로세스로 다시 시작될 때 프로젝트를 다시 열 수 없습니다. 그러나 **파일** > **최근에 사용한 프로젝트 및 솔루션**에서 프로젝트를 선택하여 열 수 있습니다.

**Windows Forms 디자이너**에서 작업이 완료되면 Visual Studio를 DPI를 인식하는 프로세스로 다시 시작해야 합니다. DPI를 인식하지 않는 프로세스로 실행되는 경우 글꼴이 흐리게 표시되고 **XAML 디자이너**와 같은 디자이너에서 문제가 발생할 수 있습니다. DPI를 인식하지 않는 모드에서 실행되는 Visual Studio를 닫았다가 다시 열면 DPI를 다시 인식하게 됩니다. 알림 표시줄에서 **Visual Studio를 DPI 인식 프로세스로 다시 시작** 옵션을 클릭할 수도 있습니다.

### <a name="add-a-registry-entry"></a>레지스트리 항목 추가

레지스트리를 수정하여 Visual Studio를 DPI를 인식하지 않는 프로세스로 표시할 수 있습니다. **레지스트리 편집기**를 열고 **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** 하위 키

**Entry**에 항목을 추가합니다. Visual Studio 2017 또는 2019 사용 여부에 따라 다음 값 중 하나를 사용합니다.

- C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Visual Studio Professional 또는 Enterprise Edition을 사용하는 경우 항목에서 **Community**를 **Professional** 또는 **Enterprise**로 바꿉니다. 또한 필요에 따라 드라이브 문자를 바꿉니다.

**형식**: REG_SZ

**값**: DPIUNAWARE

> [!NOTE]
> Visual Studio는 레지스트리 항목을 제거할 때까지 DPI를 인식하지 않는 모드로 유지됩니다.

### <a name="set-your-display-scaling-setting-to-100"></a>화면 표시 배율 설정을 100%로 설정

Windows 10에서 화면 표시 배율을 100%로 설정하려면 작업 표시줄 검색 상자에 **표시 설정**을 입력하고 **표시 설정 변경**을 선택합니다. **설정** 창에서 **텍스트, 앱 및 기타 항목 크기 변경**을 **100%** 로 설정합니다.

화면 표시 배율을 100%로 설정하면 사용자 인터페이스가 너무 작아져서 사용하지 못할 수 있기 때문에 바람직하지 않을 수도 있습니다.

## <a name="disable-notifications"></a>알림 사용 안 함

Visual Studio에서 DPI 배율 문제에 대한 알림이 표시되지 않도록 선택할 수 있습니다. 예를 들어 디자이너에서 작업하지 않는 경우 알림을 사용하지 않도록 설정할 수 있습니다.

알림을 사용하지 않도록 설정하려면 **도구** > **옵션**을 선택하여 **옵션** 대화 상자를 엽니다. 그런 다음, **Windows Forms 디자이너** > **일반**을 선택하고 **DPI 배율 알림**을 **False**로 설정합니다.

![Visual Studio의 DPI 배율 알림 옵션](./media/notifications-option.png)

나중에 배율 알림을 다시 활성화하려면 속성을 **True**로 설정합니다.

## <a name="troubleshoot"></a>문제 해결

DPI 인식 전환이 Visual Studio에서 예상대로 작동하지 않는 경우 레지스트리 편집기에서 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** 하위 키에 `dpiAwareness` 값이 있는지 확인합니다. 값이 있는 경우 삭제합니다.

## <a name="see-also"></a>참조

- [Windows Forms의 자동 크기 조정](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
