---
title: 설치 및 업그레이드 문제 해결
description: 때로는 무엇인가 잘못될 수도 있습니다. Visual Studio 설치 또는 업그레이드에 실패할 경우 이 페이지가 도움이 될 수 있습니다.
ms.date: 06/24/2020
ms.custom: seodec18
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 418cc9f75842cb4f3e9d8c0c0753084e2f0633c2
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350812"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Visual Studio 설치 및 업그레이드 문제 해결

> [!IMPORTANT]
> 설치하는 데 문제가 있나요? 도와드리겠습니다. [**설치 채팅**](https://visualstudio.microsoft.com/vs/support/#talktous)(영어만 가능) 지원 옵션도 제공됩니다.

이 문제 해결 가이드에는 대부분의 설치 문제를 해결할 수 있는 단계별 지침이 포함되어 있습니다.

## <a name="online-installations"></a>온라인 설치

다음 단계는 일반적인 온라인 설치에 최적화되어 있습니다. 오프라인 설치에 영향을 주는 문제의 경우 [오프라인 설치 문제를 해결하는 방법](#offline-installations)을 참조하세요.

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>1단계 - 이 문제가 알려진 문제인지 확인

::: moniker range="vs-2017"

Microsoft에서 수정을 진행하고 있는 Visual Studio 설치 관리자에 관련된 몇 가지 알려진 문제가 있습니다. 문제에 대한 해결 방법이 있는지 확인하려면 [릴리스 정보의 알려진 문제 섹션](/visualstudio/releasenotes/vs2017-relnotes#-known-issues)을 확인하세요.

::: moniker-end

::: moniker range="vs-2019"

Microsoft에서 수정을 진행하고 있는 Visual Studio 설치 관리자에 관련된 몇 가지 알려진 문제가 있습니다. 문제에 대한 해결 방법이 있는지 확인하려면 [릴리스 정보의 알려진 문제 섹션](/visualstudio/releases/2019/release-notes#-known-issues)을 확인하세요.

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>2단계 - Visual Studio 복구 시도

복구가 일반적인 업데이트 문제를 해결합니다. Visual Studio에서 복구 기능을 사용하는 시기 및 방법에 관한 자세한 내용은 [Visual Studio 복구](repair-visual-studio.md)를 참조하세요.

### <a name="step-3---check-with-the-developer-community"></a>3단계 - 개발자 커뮤니티에서 확인

[Visual Studio 개발자 커뮤니티](https://developercommunity.visualstudio.com/spaces/8/index.html)를 사용하여 오류 메시지를 검색합니다. 커뮤니티의 다른 멤버가 문제에 대한 해결책을 문서화했을 수 있습니다.

### <a name="step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>4단계 - Visual Studio 설치 관리자 디렉터리를 삭제하여 업그레이드 문제 해결

Visual Studio 설치 관리자 부트스트래퍼는 나머지 Visual Studio 설치 관리자를 설치하는 최소한의 간단한 실행 파일입니다. Visual Studio 설치 관리자 파일을 삭제하고 부트스트래퍼를 다시 실행하면 몇 가지 업데이트 실패가 해결될 수 있습니다.

> [!NOTE]
> 다음 작업을 수행하여 Visual Studio 설치 관리자 파일을 다시 설치하고 설치 메타데이터를 다시 설정합니다.

::: moniker range="vs-2017"

1. Visual Studio 설치 관리자를 닫습니다.
2. Visual Studio 설치 관리자 디렉터리를 삭제합니다. 일반적으로 디렉터리는 `C:\Program Files (x86)\Microsoft Visual Studio\Installer`입니다.
3. Visual Studio 설치 관리자 부트스트래퍼를 실행합니다. Downloads 폴더에서 `vs_[Visual Studio edition]__*.exe` 패턴을 따르는 파일 이름을 사용하는 부트스트래퍼를 찾을 수 있습니다. 해당 애플리케이션을 찾을 수 없으면 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하고 해당 버전의 Visual Studio에 대한 **다운로드**를 클릭하여 부트스트래퍼를 다운로드할 수 있습니다. 그런 다음, 실행 파일을 실행하여 설치 메타데이터를 다시 설정합니다.
4. Visual Studio를 다시 설치하거나 업데이트해 보세요. 설치 관리자가 계속 실패하면 다음 단계로 이동합니다.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 설치 관리자를 닫습니다.
2. Visual Studio 설치 관리자 디렉터리를 삭제합니다. 일반적으로 디렉터리는 `C:\Program Files (x86)\Microsoft Visual Studio\Installer`입니다.
3. Visual Studio 설치 관리자 부트스트래퍼를 실행합니다. Downloads 폴더에서 `vs_[Visual Studio edition]__*.exe` 패턴을 따르는 파일 이름을 사용하는 부트스트래퍼를 찾을 수 있습니다. 해당 애플리케이션을 찾을 수 없으면 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하고 해당 버전의 Visual Studio에 대한 **다운로드**를 클릭하여 부트스트래퍼를 다운로드할 수 있습니다. 그런 다음, 실행 파일을 실행하여 설치 메타데이터를 다시 설정합니다.
4. Visual Studio를 다시 설치하거나 업데이트해 보세요. 설치 관리자가 계속 실패하면 다음 단계로 이동합니다.

::: moniker-end

### <a name="step-5---report-a-problem"></a>5단계 - 문제 보고

경우에 따라 손상된 파일에 관련된 문제인 경우 문제를 사례별로 확인해야 할 수 있습니다. 도움을 받으려면 다음을 수행하세요.

::: moniker range="vs-2017"

1. 설치 로그를 수집합니다. 자세한 내용은 [Visual Studio 설치 로그를 가져오는 방법](#installation-logs)을 참조하세요.
2. Visual Studio 설치 관리자를 열고 **문제 보고**를 클릭하여 Visual Studio 피드백 도구를 엽니다.
![[피드백 제공] 단추를 탭하여 피드백 도구를 열 수 있음](media/report-a-problem.png)
3. 문제 보고서의 제목을 지정하고 관련 세부 정보를 제공합니다. **다음**을 클릭하여 **첨부 파일** 섹션으로 이동하고 생성된 로그 파일을 첨부합니다. 일반적으로 파일은 `%TEMP%\vslogs.zip`에 있습니다.
4. **다음**을 클릭하여 문제 보고서를 검토하고 **제출**을 클릭합니다.

::: moniker-end

::: moniker range="vs-2019"

1. 설치 로그를 수집합니다. 자세한 내용은 [Visual Studio 설치 로그를 가져오는 방법](#installation-logs)을 참조하세요.
2. Visual Studio 설치 관리자를 열고 **문제 보고**를 클릭하여 Visual Studio 피드백 도구를 엽니다.
![[피드백 제공] 단추를 탭하여 피드백 도구를 열 수 있음](media/vs-2019/vs-installer-report-problem.png)
3. 문제 보고서의 제목을 지정하고 관련 세부 정보를 제공합니다. **다음**을 클릭하여 **첨부 파일** 섹션으로 이동하고 생성된 로그 파일을 첨부합니다. 일반적으로 파일은 `%TEMP%\vslogs.zip`에 있습니다.
4. **다음**을 클릭하여 문제 보고서를 검토하고 **제출**을 클릭합니다.

::: moniker-end

### <a name="step-6---run-installcleanupexe-to-remove-installation-files"></a>6단계 - InstallCleanup.exe를 실행하여 설치 파일 제거

마지막 수단으로 [Visual Studio를 제거](remove-visual-studio.md)하여 모든 설치 파일 및 제품 정보를 제거합니다.

1. [Visual Studio 제거](remove-visual-studio.md)의 지침을 따릅니다.
2. [4단계 - Visual Studio 설치 관리자 디렉터리를 삭제하여 업그레이드 문제 해결](#step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems)에 설명된 부트스트래퍼를 다시 실행하세요.
3. Visual Studio를 다시 설치하거나 업데이트해 보세요.

### <a name="step-7---contact-us-optional"></a>7단계 - 문의(선택 사항)

이전 단계가 Visual Studio를 설치하거나 업그레이드하는 데 도움이 되지 않는 경우 [**라이브 채팅**](https://visualstudio.microsoft.com/vs/support/#talktous) 지원 옵션(영어로만 제공)을 사용하여 추가 지원을 받으세요.

## <a name="offline-installations"></a>오프라인 설치

다음은 [오프라인 설치](create-an-offline-installation-of-visual-studio.md)를 생성한 후 로컬 레이아웃에서 설치할 때 도움이 되는 알려진 문제 및 몇 가지 해결 방법의 표입니다.

| 문제점       | 항목                   | 솔루션 |
| ----------- | ---------------------- | -------- |
| 사용자에게 파일에 액세스할 수 있는 권한이 없습니다. | 권한(ACL) | 오프라인 설치를 공유하기 *전에* 먼저 다른 사용자에게 읽기 액세스 권한을 부여하도록 권한(ACL)을 조정해야 합니다. |
| 새 작업, 구성 요소 또는 언어가 설치되지 않습니다.  | `--layout`  | 부분 레이아웃에서 설치하고 해당 부분 레이아웃에서 이전에 다운로드하지 않은 워크로드, 구성 요소 또는 언어를 선택하는 경우 인터넷에 액세스할 수 있는지 확인합니다. |

[네트워크 설치](create-a-network-installation-of-visual-studio.md)와 관련된 문제를 해결하는 방법에 대한 자세한 내용은 [Visual Studio를 설치하거나 사용할 때 네트워크 관련 오류 문제 해결](troubleshooting-network-related-errors-in-visual-studio.md)을 참조하세요.

## <a name="installation-logs"></a>설치 로그

대부분의 설치 문제 해결에는 설치 로그가 필요합니다. Visual Studio 설치 관리자에서 [문제 보고](../ide/how-to-report-a-problem-with-visual-studio.md)를 사용하여 문제를 제출하는 경우 이러한 로그는 보고서에 자동으로 포함됩니다.

Microsoft 지원에 문의하는 경우 [Microsoft Visual Studio 및 .NET Framework 로그 컬렉션 도구](https://www.microsoft.com/download/details.aspx?id=12493)를 사용하여 이러한 설치 로그를 제공해야 할 수 있습니다. 로그 컬렉션 도구는 .NET Framework, Windows SDK 및 SQL Server를 포함하여 Visual Studio에 의해 설치된 모든 구성 요소에서 설치 로그를 수집합니다. 또한 컴퓨터 정보, Windows Installer 인벤토리는 물론 Visual Studio 설치 관리자, Windows Installer 및 시스템 복원에 대한 Windows 이벤트 로그 정보도 수집합니다.

로그를 수집하려면

1. [도구를 다운로드합니다](https://www.microsoft.com/download/details.aspx?id=12493).
2. 관리자 명령 프롬프트를 엽니다.
3. 도구를 저장한 디렉터리에서 `Collect.exe`를 실행합니다.
4. `%TEMP%` 디렉터리에서 결과 `vslogs.zip` 파일을 찾습니다(예: `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`).

> [!NOTE]
> 이 도구는 실패한 설치가 실행되었던 동일한 사용자 계정으로 실행되어야 합니다. 다른 사용자 계정에서 이 도구를 실행하는 경우 `–user:<name>` 옵션을 설정하여 실패한 설치가 실행된 사용자 계정을 지정합니다. 추가 옵션 및 사용법 정보를 보려면 관리자 명령 프롬프트에서 `Collect.exe -?`를 실행합니다.

## <a name="live-help"></a>라이브 도움말

이 문제 해결 가이드에 나열된 솔루션이 Visual Studio를 성공적으로 설치하거나 업그레이드하는 데 도움이 되지 않는 경우 [**라이브 채팅**](https://visualstudio.microsoft.com/vs/support/#talktous) 지원 옵션(영어로만 제공)을 사용하여 추가 지원을 받으세요.

## <a name="see-also"></a>참조

* [Visual Studio 복구](repair-visual-studio.md)
* [Visual Studio 제거](remove-visual-studio.md)
* [방화벽 또는 프록시 서버 배후에서 Visual Studio와 Azure 서비스 설치 및 사용](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio 인스턴스 검색 및 관리 도구](tools-for-managing-visual-studio-instances.md)
* [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
