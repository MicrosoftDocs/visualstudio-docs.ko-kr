---
title: 코딩 된 UI 테스트 업그레이드
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 35
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3a29e531ca9b2a74e67abf80a0e3017a0f5b0b07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297994"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Visual Studio 2010에서 코딩된 UI 테스트 업그레이드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1에서 만든, 코딩된 UI 테스트를 포함하는 테스트 프로젝트는 Visual Studio 2012에서 열 때 자동으로 복구됩니다. 테스트 프로젝트를 소스 제어로 체크 인하면 프로젝트 파일은 복구를 위해 체크 아웃됩니다. 복구된 다음에는 코딩된 UI 테스트를 포함하는 이러한 테스트 프로젝트를 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1과 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 모두 사용할 수 있습니다.

 **요구 사항**

- Visual Studio Enterprise

> [!NOTE]
> Visual Studio에는 둘 이상의 테스트 프로젝트 형식이 있습니다. 코딩된 UI 테스트를 새로 만드는 경우 코딩된 UI 테스트 프로젝트 형식으로 만들어집니다. 자세한 내용은 [이전 버전의 Visual Studio에서 테스트 업그레이드](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)를 참조하세요.

> [!WARNING]
> 코딩된 UI 테스트를 포함하는[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 테스트 프로젝트는 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 에서 열거나 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 와 함께 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 여는 경우 다시 작성해야 합니다.

> [!WARNING]
> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 에서 만들고 단위 테스트만 포함하는 테스트 프로젝트는 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 여는 경우 코딩된 UI 테스트를 추가할 수 없습니다. 마찬가지로 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 만든 단위 테스트 프로젝트에는 코딩된 UI 테스트를 추가할 수 없습니다.

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Visual Studio 2010과 Visual Studio 2012 간의 호환성 문제
 다음 표에서는 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 과 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]간에 코딩된 UI 테스트를 마이그레이션하는 경우 주의해야 할 문제에 대해 설명합니다.

> [!CAUTION]
> 솔루션 탐색기에 나타나지 않는 코딩된 UI 테스트 프로젝트의 참조와 관련된 알려진 문제가 있습니다. 자세한 내용은 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 설치 미디어에 포함된 추가 정보 파일을 참조하세요.

|코딩된 UI 기능|문제|해결 방법|
|----------------------------|-----------|--------------|
|[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**빌드가 실패합니다.**<br /><br /> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 기능 팩 2가 있고 Silverlight 애플리케이션에 대한 코딩된 UI 테스트 프로젝트를 만든 경우 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 이러한 프로젝트를 열 수 없습니다.|이러한 프로젝트는 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 기능 팩 2에서만 관리하는 것이 좋습니다.|
|[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**빌드는 성공하지만 테스트 실행이 실패합니다.**<br /><br /> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 기능 팩 2가 있고 Firefox에서 웹 애플리케이션에 대한 코딩된 UI 테스트 프로젝트를 만든 경우 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 이러한 프로젝트를 열 수 없습니다.|이러한 프로젝트는 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] 기능 팩 2에서만 관리하는 것이 좋습니다.|
|새 UI 코드 테스트 API가 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]추가되었습니다.|**빌드가 실패합니다.**<br /><br /> [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 새 UI 테스트 API를 사용하여 코딩된 UI 테스트를 만드는 경우 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]에서 이러한 프로젝트를 열 수 없습니다.|새 API를 사용하는 프로젝트는 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서만 관리해야 합니다.|
|[!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]에서 참조가 csproj 파일의 'Choose' 문 내부에 추가되었습니다. [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서는 코딩된 UI 테스트 어셈블리 참조를 포함하는 피드백 대상 파일이 사용됩니다.|[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서는 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] (또는 SP1)에서 만든, 코딩된 UI 테스트를 포함하지 않는 테스트 프로젝트에 코딩된 UI 테스트를 추가할 수 없습니다.<br /><br /> 복구 프로세스에서 대상 파일 및 Choose 문을 추가합니다. 코딩된 UI 테스트가 테스트 프로젝트에 없는 경우 프로젝트가 복구됨으로 표시되면 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 코딩된 UI 테스트를 추가할 때 적절한 참조가 추가되지 않습니다.|동일한 솔루션에서 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 를 사용하여 새 테스트 프로젝트를 만들고 새 코딩된 UI 테스트를 추가해야 합니다. 또는 코딩된 UI 테스트를 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1의 테스트 프로젝트에 추가하고 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 해당 프로젝트를 열 수 있습니다.|

## <a name="visual-studio-2010-sp1-update"></a><a name="UpgradingCodedUIFromVS2010_Update"></a> Visual Studio 2010 SP1 업데이트
 Visual Studio 2012 및 Windows 8에 대한 호환성 지원이 있는 [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 업데이트는 [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=34677) 에서 다운로드할 수 있으며 Visual Studio 업데이트로도 사용할 수 있습니다.

 업데이트를 적용하면 다음과 같은 [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1 코딩된 UI 테스트 도구 기능이 Windows 8에 맞게 개선됩니다.

- Windows 8을 실행하는 컴퓨터에서 Microsoft.NET Framework 4.5 기반 WPF(Windows Presentation Foundation) 컨트롤에 대한 코딩된 UI 테스트를 실행할 수 있습니다.

- Windows 8을 실행하는 컴퓨터에서 64비트(x64) Internet Explorer 10에 대한 코딩된 UI 테스트를 실행할 수 있습니다.

  업데이트에는 다음과 같은 문제에 대한 수정 사항도 포함되어 있습니다.

- **코드 검사:** Visual Studio 2012에서 만든 코드 검사 파일(.coverage)은 [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1에서 열 수 없습니다.

- **잘못 할당된 테스트 아티팩트:** TFS(Team Foundation Server) 2010에서 잘못된 사용자에게 할당된 테스트 아티팩트가 팀에 있습니다. 예를 들어 사용자가 퇴사했지만 이 사용자에게 할당된 테스트 사례가 계속 있습니다. TFS 2010을 TFS 2012로 업그레이드합니다. [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010을 사용하여 업그레이드된 TFS 서버에 연결합니다. [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010을 사용하여 TFS 사용자에게 테스트 아티팩트를 할당할 수 없습니다.

- **부하 테스트:** Windows 8을 실행하는 컴퓨터에서 LAN(Local Area Network) 프로필이 아닌 다른 네트워크 형식과 함께 부하 테스트를 실행하는 경우 네트워크 에뮬레이터 드라이버로 인해 운영 체제가 충돌합니다. 자세한 내용은 [기술 자료 문서 2736182](https://support.microsoft.com/help/2736182/a-gdr-update-for-visual-studio-2010-sp1-is-available-to-add-compatibil)를 참조하세요.

## <a name="see-also"></a>관련 항목
 [Visual Studio 프로젝트 포팅, 마이그레이션 및 업그레이드](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [이전 버전의 Visual studio에서 테스트 업그레이드](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) 는 [ui 자동화를 사용 하](../test/use-ui-automation-to-test-your-code.md) 여 코딩 된 Ui [테스트를 생성 하는](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) 코드를 테스트 합니다. 코딩 된 [ui 테스트 및 작업 기록에 대해 지원 되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) 을 기록 합니다.
