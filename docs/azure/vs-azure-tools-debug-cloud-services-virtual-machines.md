---
title: Azure 클라우드 서비스 또는 가상 머신 디버그
description: Visual Studio에서 클라우드 서비스 또는 Virtual Machine 디버깅
author: mikejo5000
manager: jillfra
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: how-to
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 68b64b3097d2b26d30593ac63de5e531d6cc7736
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88800491"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Visual Studio에서 Azure 클라우드 서비스 또는 가상 머신 디버깅

Visual Studio는 Azure 클라우드 서비스와 가상 머신 디버깅에 여러 가지 옵션을 제공합니다.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>로컬 컴퓨터에서 클라우드 서비스 디버그

Azure 컴퓨팅 에뮬레이터를 사용하여 로컬 머신에서 클라우드 서비스 디버그하면 시간과 돈을 절약할 수 있습니다. 배포하기 전에 로컬로 서비스를 디버깅하면, 컴퓨팅 시간이 소요되지 않고 안정성과 성능을 향상할 수 있습니다. 그러나, Azure 자체에서 클라우드 서비스를 실행하는 경우, 일부 오류가 발생할 수 있습니다. 서비스를 게시하거나 역할 인스턴스에 디버거를 연결할 때 원격 디버깅을 사용하면 이 오류들을 디버그할 수 있습니다.

에뮬레이터가 로컬 환경에서 Azure 컴퓨팅 서비스를 시뮬레이트 및 실행하여 클라우드 서비스를 배포하기 전에 테스트 및 디버그할 수 있습니다. 에뮬레이터는 역할 인스턴스의 수명 주기를 처리하고 로컬 스토리지 같은 시뮬레이트된 리소스에 대한 액세스를 제공합니다. Visual Studio에서 서비스를 디버그하거나 실행할 때, 에뮬레이터가 백그라운드 애플리케이션으로 자동으로 시작된 다음, 서비스가 에뮬레이터에 배포됩니다. 로컬 환경에서 서비스가 실행되는 것을 보기 위해 에뮬레이터를 사용할 수 있습니다. 에뮬레이터의 정식 버전 또는 Express 버전을 사용할 수 있습니다. (Azure 2.3부터 에뮬레이터의 express 버전이 기본값입니다.) [Emulator Express를 사용 하 여 로컬에서 클라우드 서비스 실행 및 디버그를](vs-azure-tools-emulator-express-debug-run.md)참조 하세요.

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>로컬 컴퓨터에서 클라우드 서비스를 디버그 하려면

1. 메뉴 모음에서 **디버그**  >  **디버깅 시작** 을 선택 하 여 Azure 클라우드 서비스 프로젝트를 실행 합니다. F5를 눌러도 디버깅을 시작할 수 있습니다. 컴퓨팅 에뮬레이터가 시작한다는 메시지가 표시됩니다. 에뮬레이터를 시작할 때 시스템 트레이 아이콘을 확인합니다.

    ![시스템 트레이의 Azure 에뮬레이터](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. 알림 영역에서 Azure 아이콘에 대한 바로 가기 메뉴를 연 다음, **Compute 에뮬레이터 UI 표시**를 선택하여 컴퓨팅 에뮬레이터에 대한 사용자 인터페이스를 표시합니다.

    UI의 왼쪽 창에서는 현재 컴퓨팅 에뮬레이터와 각 서비스를 실행하는 역할 인스턴스가 배포되는 서비스를 보여줍니다. 오른쪽 창에서 수명 주기, 로깅 및 진단 정보를 표시하는 서비스 또는 역할을 선택할 수 있습니다. 포함된 창의 위쪽 여백에 포커스를 맞추면 오른쪽 창에 맞게 확장됩니다.

3. **디버그** 메뉴에서 명령을 선택 하 고 코드에 중단점을 설정 하 여 응용 프로그램을 단계별로 실행 합니다. 디버거에서 애플리케이션을 통해 단계를 진행하면 애플리케이션의 현재 상태로 창이 업데이트됩니다. 디버깅을 중지하면 애플리케이션 배포가 삭제됩니다. 애플리케이션이 웹 역할을 포함하고 웹 브라우저를 시작하도록 시작 동작 속성을 설정하면, Visual Studio는 브라우저에서 웹 애플리케이션을 시작합니다. 서비스 구성에서 역할의 인스턴스 수를 변경한 경우, 클라우드 서비스를 중지하고 역할의 이러한 새 인스턴스를 디버깅할 수 있도록 디버깅을 다시 시작해야 합니다.

    > [!NOTE]
    > 서비스 실행이나 디버깅을 중지해도 로컬 컴퓨팅 에뮬레이터 및 스토리지 에뮬레이터는 중지되지 않습니다. 알림 영역에서 이 에뮬레이터들을 명시적으로 중지해야 합니다.

## <a name="debug-a-cloud-service-in-azure"></a>Azure에서 클라우드 서비스 디버그

원격 컴퓨터에서 클라우드 서비스를 디버그하려면, 클라우드 서비스를 배포할 때 명시적으로 이 기능을 사용할 수 있어야 역할 인스턴스에서 실행되는 서비스(예: msvsmon.exe)가 설치됩니다. 서비스를 게시할 때 원격 디버깅을 사용하지 않으면 원격 디버깅을 사용한 서비스를 다시 게시해야 합니다.

클라우드 서비스에 원격 디버깅을 사용하면, 성능이 저하되거나 추가 요금이 발생하지 않습니다. 서비스를 사용하는 클라이언트에 악영향을 줄 수 있으므로 원격 디버깅을 프로덕션 서비스에 사용하지 않도록 합니다.

> [!NOTE]
> Visual Studio에서 클라우드 서비스를 게시할 때 .NET Framework 4 또는 .NET Framework 4.5를 대상으로 하는 서비스의 모든 역할에 대해 **IntelliTrace** 를 사용할 수 있습니다. **IntelliTrace**를 사용하여 이전의 역할 인스턴스에서 발생한 이벤트를 검사하고 그 시점부터 컨텍스트를 재현할 수 있습니다. [IntelliTrace 및 Visual Studio를 사용하여 게시된 클라우드 서비스 디버깅](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md) 및 [IntelliTrace 사용하기](../debugger/intellitrace.md)를 참조하세요.

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>클라우드 서비스의 원격 디버깅을 사용하려면

1. Azure 프로젝트의 바로가기 메뉴를 열고, **게시**를 선택합니다.

2. **스테이징** 환경 및 **디버그** 구성을 선택합니다.

    단지 지침일 뿐입니다. 테스트 환경을 프로덕션 환경에서 실행하도록 선택할 수 있습니다. 그러나 프로덕션 환경에서 원격 디버깅을 사용할 경우 사용자에게 악영향을 끼칠 수 있습니다. 릴리스 구성을 선택할 수도 있지만, 디버그 구성이 디버깅을 더 쉽게 할 수 있습니다.

    ![디버그 구성 선택](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. 일반 단계를 따르지만, **고급 설정** 탭에서 **모든 역할에 원격 디버거 사용** 확인란을 선택합니다.

    ![디버그 구성](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Azure의 클라우드 서비스에 디버거를 연결하려면

1. 서버 탐색기에서 클라우드 서비스 노드를 확장합니다.

2. 연결하려는 역할 또는 역할 인스턴스에 대한 바로 가기 메뉴를 연 다음 **디버거 연결**을 선택합니다.

    역할을 디버깅하는 경우 Visual Studio 디버거는 해당 역할의 각 인스턴스에 연결합니다. 디버거는 코드 줄을 실행하고 중단점의 아무 조건이나 만족시키는 첫 번째 역할 인스턴스의 중단점에서 멈춥니다. 인스턴스를 디버그할 경우 디버거는 해당 인스턴스에만 연결되고 특정 인스턴스가 코드 줄을 실행하고 중단점의 조건을 만족시킬 때만 중단점에서 멈춥니다.

    ![디버거 연결](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. 인스턴스에 디버거가 연결된 후 평소와 같이 디버깅합니다. 디버거는 사용자의 역할에 적절한 호스트 프로세스에 자동으로 연결합니다. 역할에 따라 디버거는 w3wp.exe, WaWorkerHost.exe 또는 WallHost.exe에 연결됩니다. 프로세스가 어떤 디버거에 연결되어있는지 확인하려면 서버 탐색기에서 인스턴스 노드를 확장합니다. Azure 프로세스에 대한 자세한 내용은 [Azure 역할 아키텍처](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/)를 참조하세요.

    ![코드 형식 선택 대화 상자](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. 디버거가 연결 된 프로세스를 확인 하려면 메뉴 모음에서 **디버그**  >  **Windows**  >  **프로세스**를 선택 하 고 **프로세스** 대화 상자를 엽니다. (키보드: Ctrl+Alt+Z) 특정 프로세스와 연결을 분리하려면 해당 바로 가기를 열고 **프로세스 분리**를 선택하세요. 또는, 서버 탐색기에서 인스턴스 노드의 위치를 찾고, 프로세스를 찾고 해당 바로 가기를 열고 **프로세스 분리**를 선택합니다.

    ![디버그 프로세스](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> 원격 디버깅 시 중단점에서 장시간 중지하지 않도록 합니다. 프로세스가 몇 분간 중지되면 Azure는 응답하지 않는 프로세스로 간주하여 해당 인스턴스에 트래픽 전송을 중지합니다. 너무 오랫동안 중지하는 경우 msvmon.exe가 프로세스에서 분리됩니다.

인스턴스나 역할의 모든 프로세스에서 디버거를 분리하려면 디버깅하는 역할 또는 인스턴스의 바로가기를 열고 **디버거 분리**를 선택합니다.

## <a name="limitations-of-remote-debugging-in-azure"></a>Azure에서 원격 디버깅의 제한 사항

Azure SDK 2.3의 원격 디버깅은 다음과 같은 제한 사항이 있습니다.

* 원격 디버깅을 사용하면 모든 역할에 25개 이상의 인스턴스가 있는 클라우드 서비스를 게시할 수 없습니다.
* 디버거는 30400에서 30424, 31400에서 31424 및 32400에서 32424의 포트를 사용합니다. 이 포트 중 하나를 사용하려는 경우, 서비스를 게시할 수 없으며, 다음과 같은 오류 메시지 중 하나가 Azure 활동 로그에 표시됩니다.

  * .csdef 파일에 대한 .cscfg 파일의 유효성 검사 오류가 발생했습니다.
    예약된 포트의 범위는 엔드포인트 Microsoft.WindowsAzure.Plugins.RemoteDebugger의 범위입니다. 역할의 커넥터는 이미 정의된 포트 또는 범위를 겹치는 역할입니다.
  * 할당하지 못했습니다. 나중에 다시 시도하거나, 가상 컴퓨터 사이즈 또는 역할 인스턴스의 수를 줄이거나 다른 지역에 배포해 보십시오.

## <a name="debugging-azure-virtual-machines"></a>Azure 가상 머신을 디버깅합니다.

Visual Studio의 서버 탐색기를 사용하여 Azure 가상 머신에서 실행하는 프로그램을 디버그할 수 있습니다. Azure 가상 머신에서 원격 디버깅을 사용하면 Azure는 가상 머신에 원격 디버깅 확장을 설치합니다. 그리고 나서, 가상 머신의 프로세스에 연결할 수 있으며 평소대로 디버그할 수 있습니다.

> [!NOTE]
> Visual Studio 2015의 클라우드 탐색기를 이용하여 Azure 리소스 관리자 스택으로 생성한 가상 머신을 원격으로 디버그할 수 있습니다. 자세한 내용은 [클라우드 탐색기를 사용하여 Azure 리소스 관리](vs-azure-tools-resources-managing-with-cloud-explorer.md)를 참조하세요.

### <a name="to-debug-an-azure-virtual-machine"></a>Azure 가상 컴퓨터를 디버그하려면

1. 서버 탐색기에서 Virtual Machines 노드를 확장하고 디버깅하려는 Virtual Machines의 노드를 선택합니다.

2. 컨텍스트 메뉴를 열고 **디버깅 사용**을 선택합니다. 가상 머신 상에 디버깅 사용을 확인하는 메시지가 나오면 **예**를 선택합니다.

    디버깅을 사용할 수 있도록 Azure가 원격 디버깅 확장을 가상 머신에 설치합니다.

    ![가상 머신 디버깅 사용 명령](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure 활동 로그](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. 원격 디버깅 확장 설치가 끝나면, 가상 머신의 상황에 맞는 메뉴를 열고 **디버거 연결...**

    Azure에서는 가상 컴퓨터에 프로세스 목록을 가져와서 **프로세스에 연결** 대화 상자에 표시합니다.

    ![디버거 연결 명령](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. **프로세스에 연결** 대화 상자에서 디버그하려는 코드의 유형만 표시하도록 결과 목록 제한 **선택**을 선택합니다. 32비트 또는 64비트 관리 코드 및 네이티브 코드 또는 둘 다 디버그할 수 있습니다.

    ![코드 형식 선택 대화 상자](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. 가상 머신에서 디버깅할 프로세스를 선택한 다음 **연결**을 선택 합니다. 예를 들어, 가상 머신에서 웹앱을 디버그하려면 w3wp.exe 프로세스를 선택합니다. 자세한 내용은 [Visual Studio에서 하나 이상의 프로세스 디버그](https://msdn.microsoft.com/library/jj919165.aspx) 및 [Azure 역할 아키텍쳐](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/)를 참조하세요.

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>디버깅을 위한 웹 프로젝트 및 가상 머신 만들기

Azure 프로젝트를 게시하기 전에, 포함된 환경 - 디버깅 및 테스트 시나리오를 지원하고 테스트 및 모니터링 프로그램을 설치할 수 있는-에서 테스트에 유용한 것을 찾을 수 있습니다. 이러한 테스트를 실행하는 한 가지 방법은 가상 머신에서 앱을 원격으로 디버그합니다.

Visual Studio ASP.NET 프로젝트는 앱 테스트를 위해 사용할 수 있는 편리한 가상 머신을 만드는 옵션을 제공합니다. 가상 머신은 PowerShell, 원격 데스크톱 및 WebDeploy와 같은 일반적으로 필요한 엔드포인트를 포함합니다.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>웹 프로젝트 및 디버깅을 위한 가상 컴퓨터를 만들려면

1. Visual Studio에서 새 ASP.NET 웹 애플리케이션을 만듭니다.

2. 새 ASP.NET 프로젝트 대화 상자의 Azure 섹션에 있는 드롭다운 목록 상자에서 **가상 머신** 를 선택 합니다. **원격 리소스 만들기** 확인란을 선택한 상태로 둡니다. **확인** 을 선택하여 계속합니다.

    **Azure에 가상 컴퓨터 만들기** 대화 상자가 표시됩니다.

    ![ASP.NET 웹 프로젝트 만들기 대화 상자](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Azure 계정에 로그인하지 않은 경우, 로그인하라는 메시지가 표시됩니다.

3. 가상 컴퓨터에 대 한 다양 한 설정을 선택 하 고 **확인**을 선택 합니다. 자세한 내용은 [Virtual Machines](/azure/virtual-machines/)를 참조하세요.

    DNS 이름으로 입력한 이름이 가상 컴퓨터의 이름이 됩니다.

    ![Azure 대화 상자에 가상 컴퓨터 만들기](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure에서 가상 머신을 만든 다음, 원격 데스크톱 및 웹 배포와 같은 끝점을 프로 비전 하 고 구성 합니다.

4. 가상 머신을 완벽히 구현한 후에 서버 탐색기에서 가상 머신의 노드를 선택합니다.

5. 컨텍스트 메뉴를 열고 **디버깅 사용**을 선택합니다. 가상 머신 상에 디버깅 사용을 확인하는 메시지가 나오면 **예**를 선택합니다.

    디버깅을 사용할 수 있도록 Azure가 원격 디버깅 확장을 가상 컴퓨터에 설치합니다.

    ![가상 머신 디버깅 사용 명령](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure 활동 로그](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. [Visual Studio의 One-Click 게시를 사용하여 웹 프로젝트 배포 방법](https://msdn.microsoft.com/library/dd465337.aspx)을 따라 프로젝트를 게시합니다. 가상 컴퓨터에 디버그하려고 하므로 **웹 게시** 마법사의 **설정** 페이지에서 **디버그**를 구성으로 선택합니다. 이 작업은 디버깅하는 동안 코드 기호를 사용할 수 있게 해줍니다.

    ![게시 설정](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. 프로젝트를 이미 이전에 배포한 경우 **파일 게시 옵션**에서 **대상에서 추가 파일 제거**를 선택합니다.

8. 서버 탐색기의 가상 머신의 상황에 맞는 메뉴에서 프로젝트를 게시 한 후 **디버거 연결...**

    Azure에서는 가상 컴퓨터에 프로세스 목록을 가져와서 **프로세스에 연결** 대화 상자에 표시합니다.

    ![디버거 연결 명령](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. **프로세스에 연결** 대화 상자에서 디버그하려는 코드의 유형만 표시하도록 결과 목록 제한 **선택**을 선택합니다. 32비트 또는 64비트 관리 코드 및 네이티브 코드 또는 둘 다 디버그할 수 있습니다.

    ![코드 형식 선택 대화 상자](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. 가상 머신에서 디버깅할 프로세스를 선택한 다음 **연결**을 선택 합니다. 예를 들어, 가상 머신에서 웹앱을 디버그하려면 w3wp.exe 프로세스를 선택합니다. 자세한 내용은 [Visual Studio의 하나 이상의 프로세스 디버그](https://msdn.microsoft.com/library/jj919165.aspx) 를 참조하세요.

## <a name="next-steps"></a>다음 단계

* **IntelliTrace** 를 사용 하 여 릴리스 서버에서 호출 및 이벤트 로그를 수집 합니다. [IntelliTrace 및 Visual Studio를 사용하여 게시된 클라우드 서비스 디버깅](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md)을 참조하세요.

* **Azure Diagnostics**를 이용하여 개발 환경 또는 Azure에서 실행되는 역할 내에서 실행되는 코드의 자세한 내용을 기록합니다. [Azure Diagnostics를 사용하여 로깅 데이터 수집](/azure/cloud-services/cloud-services-dotnet-diagnostics)을 참조하세요.
