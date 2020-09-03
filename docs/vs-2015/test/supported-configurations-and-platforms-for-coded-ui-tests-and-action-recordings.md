---
title: 코딩된 UI 테스트 및 작업 기록에 지원되는 구성 및 플랫폼 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
ms.assetid: 544742b5-4ec1-4d51-b941-72b2f6ff17bc
caps.latest.revision: 108
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 946373cc304e4eddb9f724941d583ab653cfe140
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851749"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>코딩된 UI 테스트 및 작업 기록에 지원되는 구성 및 플랫폼
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

아래의 표에는 Visual Studio Enterprise의 코딩된 UI 테스트에 지원되는 구성 및 플랫폼이 나와 있습니다. 이러한 구성은 [!INCLUDE[MTRlong](../includes/mtrlong-md.md)]를 사용하여 만든 작업 기록에도 적용됩니다.

> [!NOTE]
> 코딩된 UI 테스트 프로세스는 테스트 대상 응용 프로그램으로 동일한 권한이 있어야 합니다.

 **요구 사항**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>지원되는 구성

|구성|지원됨|
|-------------------|---------------|
|운영 체제|[!INCLUDE[win7](../includes/win7-md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]<br /><br /> [!INCLUDE[win8](../includes/win8-md.md)]<br /><br /> 윈도우 10|
|32비트/64비트 지원|32비트 [!INCLUDE[TCMext](../includes/tcmext-md.md)] 를 실행하는 32비트 Windows에서 32비트 애플리케이션을 테스트할 수 있습니다.<br /><br /> 32비트 [!INCLUDE[TCMext](../includes/tcmext-md.md)] 를 실행하는 64비트 Windows에서 UI 동기화 기능이 있는 32비트 WOW 애플리케이션을 테스트할 수 있습니다.<br /><br /> 32비트 [!INCLUDE[TCMext](../includes/tcmext-md.md)] 를 실행하는 64비트 Windows에서 UI 동기화 기능이 없는 64비트 Windows Forms 및 WPF 애플리케이션을 테스트할 수 있습니다.|
|Architecture|x86 및 x64 **참고:**  Internet Explorer는 [!INCLUDE[win8](../includes/win8-md.md)] 이상 버전에서 실행하는 경우를 제외하고는 64비트 모드에서 지원되지 않습니다.|
|.NET|.NET 2.0, 3.0, 3.5, 4 및 4.5. **참고:** [!INCLUDE[TCMext](../includes/tcmext-md.md)] 및 Visual Studio를 작동하려면 .NET 4가 필요합니다. 그러나 여기 나열된 .NET 버전을 사용하여 개발한 애플리케이션은 모두 지원됩니다.|

> [!NOTE]
> *UI 동기화* 는 각 컨트롤의 메시지 큐에서 재생을 확인할 수 있는 기능입니다. 컨트롤에 이벤트를 보내도 컨트롤이 응답하지 않으면 이벤트가 다시 전달됩니다.

## <a name="platform-support"></a>플랫폼 지원

|플랫폼|지원 수준|
|--------------|----------------------|
|Windows Phone 앱|WinRT-XAML 기반 휴대폰 앱만 지원됩니다.|
|Windows 스토어 앱|XAML 기반 스토어 앱에서만 지원됩니다.|
|유니버설 Windows 앱|휴대폰 및 데스크톱의 XAML 기반 유니버설 Windows 앱만 지원됩니다.|
|Microsoft Edge|Visual Studio 2015 업데이트 2 이상에서 [코딩된 UI 브라우저 간 테스트 확장](https://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d)을 사용하여 지원됩니다.|
|Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **중요:** Internet Explorer 10은 데스크톱에서만 지원됩니다. <br /><br /> Internet Explorer 11 **중요:** Internet Explorer 11은 데스크톱에서만 지원됩니다.|완전하게 지원됨<br /><br /> -   **Internet explorer 9 및 Internet explorer 10에서 HTML5 지원:** 코딩 된 UI 테스트는 HTML5 컨트롤: Audio, Video, ProgressBar 및 Slider의 기록, 재생 및 유효성 검사를 지원 합니다. 자세한 내용은 [코딩 된 UI 테스트에서 HTML5 컨트롤 사용](../test/using-html5-controls-in-coded-ui-tests.md)을 참조 하세요. **경고:**      Internet Explorer 10에서 코딩된 UI 테스트를 만드는 경우 Internet Explorer 9 또는 Internet Explorer 8을 사용하여 실행하지 못할 수 있습니다. Internet Explorer 10에는 오디오, 비디오, 진행률 표시줄 및 슬라이더와 같은 HTML5 컨트롤이 포함되기 때문입니다. 이러한 HTML5 컨트롤은 Internet Explorer 9 또는 Internet Explorer 8로 인식되지 않습니다. 마찬가지로, Internet Explorer 9를 사용하여 코딩된 UI 테스트는 Internet Explorer 8에서 인식되지 않는 일부 HTML5 컨트롤을 포함할 수 있습니다.<br />-   **Internet Explorer 10 맞춤법 검사에 대 한 지원:** Internet Explorer 10에는 모든 텍스트 상자의 맞춤법 검사 기능이 포함 되어 있습니다. 이렇게 하면 추천 단어 목록에서 선택할 수 있습니다. 코딩된 UI 테스트는 다른 철자 제안 선택하기와 같은 사용자 작업을 무시합니다. 텍스트 상자에 입력한 마지막 텍스트만 기록됩니다.<br />     다음 작업은 맞춤법 검색 컨트롤(사전에 추가, 복사, 모두 선택, 사전에 추가 및 무시)을 사용하는 코딩된 UI 테스트에 대해 기록됩니다.<br />-   **Windows 8에서 실행 되는 64 비트 Internet Explorer에 대 한 지원:** 이전에는 64 비트 버전의 Internet Explorer가 기록 및 재생을 지원 하지 않았습니다. [!INCLUDE[win8](../includes/win8-md.md)] 및 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서는 64비트 버전의 Internet Explorer에 대해 코딩된 UI 테스트를 사용하도록 설정되었습니다. **경고:**      Internet Explorer에 대한 64비트 지원은 [!INCLUDE[win8](../includes/win8-md.md)] 이상이 실행 중일 때에만 적용됩니다.<br />-   **Internet Explorer 9 사이트 고정에 대한 지원:** Internet Explorer 9에서는 고정된 사이트가 소개됩니다. 고정된 사이트를 사용하여 Internet Explorer를 먼저 열지 않고도 Windows 작업 표시줄을 통해 직접 즐겨 찾는 사이트를 방문할 수 있습니다. 이제 코딩된 UI 테스트가 고정된 사이트에서 의도 인식 작업을 생성할 수 있습니다. 고정된 사이트에 대한 자세한 내용은 [고정된 사이트](https://windows.microsoft.com/en-US/internet-explorer/products/ie-9/features/pinned-sites)를 참조하세요.<br />-   **Internet Explorer 9 의미 태그 지원:** Internet Explorer 9에는 section, nav, article, 이외, hgroup, header, footer, figure, 위치 캡션 및 mark와 같은 의미 태그가 도입 되었습니다. 코딩된 UI 테스트는 기록하는 동안 이러한 의미 태그를 모두 무시합니다. 코딩된 UI 테스트 빌더를 사용해서 이러한 태그에 어설션을 추가할 수 있습니다. 코딩된 UI 테스트 빌더에서 탐색 다이얼을 사용하여 이러한 요소를 탐색하고 해당 속성을 볼 수 있습니다.<br />-   **Internet Explorer 버전 간에 공백 문자를 원활 하 게 처리:** Internet explorer 8, Internet Explorer 9 및 Internet Explorer 10 사이에 공백 문자를 처리할 때 차이가 있습니다. 코딩된 UI 테스트는 이러한 차이를 원활하게 처리합니다. 따라서, 예를 들어 Internet Explorer 8에서 만든 코딩된 UI 테스트는 Internet Explorer 9 및 Internet Explorer 10에서 성공적으로 재생됩니다.<br />-   **Internet Explorer의 알림 영역이 "오류 발생 시 계속" 특성 집합으로 기록됨:** Internet Explorer의 알림 영역에서 모든 작업이 "오류 발생 시 계속" 특성 집합으로 기록됩니다. 재생하는 동안 알림 표시줄이 나타나지 않는 경우 여기에서의 작업은 무시되고 코딩된 UI 테스트가 다음 작업을 계속합니다.|
|Windows Forms 및 WPF 타사 컨트롤|완전하게 지원됨<br /><br /> Windows Forms 및 WPF 애플리케이션에서 타사 컨트롤을 사용하려면 참조 및 코드를 추가해야 합니다. 자세한 내용은 [컨트롤의 코딩 된 UI 테스트 사용](../test/enable-coded-ui-testing-of-your-controls.md)을 참조 하세요.|
|Internet Explorer 6<br /><br /> Internet Explorer 7|지원 안 됨|
|Chrome<br /><br /> Firefox|작업 단계 기록은 지원되지 않습니다. 코딩된 UI 테스트는 Visual Studio 2012 Update 4 이상에서 Chrome 및 Firefox 브라우저로 재생할 수 있습니다. 자세한 내용을 보려면 [여기](https://msdn.microsoft.com/library/jj835758.aspx) 로 이동하세요.|
|Opera<br /><br /> Safari|지원 안 됨|
|Silverlight|지원 안 됨<br /><br /> 그러나 Visual Studo 2013의 경우 Visual Studio 갤러리에서 [Silverlight 용 Microsoft Visual Studio 2013 코딩 된 UI 테스트 플러그 인](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudio2013CodedUITestPluginforSilve) 을 다운로드할 수 있습니다.|
|Flash/Java|지원 안 됨|
|Windows Forms 2.0 이상|완전하게 지원됨 **참고:** NetFx 컨트롤은 완전하게 지원되지만 일부 타사 컨트롤은 지원되지 않습니다.|
|WPF 3.5 이상|완전하게 지원됨<br /><br /> **참고** NetFx 컨트롤은 완전 하 게 지원 되지만 일부 타사 컨트롤은 지원 되지 않습니다.|
|Windows Win32|작동은 하지만 일부 알려진 문제가 있을 수 있으며, 공식적으로는 지원되지 않습니다.|
|MFC|부분적으로 지원됩니다. 지원 기능에 대한 자세한 내용은 다음 [Microsoft 웹 사이트](https://blogs.msdn.com/b/vstsqualitytools/archive/2010/04/15/uitest-framework-mfc-support-in-vs-2010.aspx) 를 참조하세요.|
|SharePoint|완전하게 지원됨|
|Office 클라이언트 애플리케이션|지원 안 됨|
|동적 CRM 웹 클라이언트|완전하게 지원됨|
|Dynamics (Ax) 2012 클라이언트|작업 기록 및 재생이 부분적으로 지원됩니다. 자세한 내용은 다음 [Microsoft 웹 사이트](https://blogs.msdn.com/b/dave_froslie/archive/2011/09/01/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012.aspx) 를 참조하세요.|
|SAP|지원 안 됨|
|Citrix/터미널 서비스|터미널 서버에는 작업을 기록하지 않는 것이 좋습니다. 레코더에서는 동시에 여러 인스턴스를 실행할 수 없습니다.|
|PowerBuilder|부분적으로 지원됩니다.<br /><br /> 지원 범위는 PowerBuilder 컨트롤에서 액세스할 수 있는 범위까지입니다.|

 다른 플랫폼을 지원하기 위한 확장을 만드는 방법에 대한 자세한 내용은 [컨트롤의 코딩된 UI 테스트 사용](../test/enable-coded-ui-testing-of-your-controls.md) 및 [Microsoft Excel을 지원하도록 코딩된 UI 테스트 및 작업 기록 확장](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)을 참조하세요.

## <a name="see-also"></a>관련 항목
 [UI 자동화를 사용 하](../test/use-ui-automation-to-test-your-code.md) 여 [기존 작업 기록에서 코딩 된 UI 테스트를 생성 하는](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) 코드 테스트
