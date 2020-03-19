---
title: 코딩된 UI 테스트에 대한 구성 및 플랫폼
ms.date: 10/04/2015
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e18e50537f35080f9796f4a090b3806953ae5170
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75845804"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>코딩된 UI 테스트 및 작업 기록에 지원되는 구성 및 플랫폼

아래의 표에는 Visual Studio Enterprise의 코딩된 UI 테스트에 지원되는 구성 및 플랫폼이 나와 있습니다. 이러한 구성은 [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)]를 사용하여 만든 작업 기록에도 적용됩니다.

> [!NOTE]
> 코딩된 UI 테스트 프로세스는 테스트 대상 응용 프로그램으로 동일한 권한이 있어야 합니다.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**요구 사항**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>지원되는 구성

| 구성 | 지원됨 |
|-| - |
| 운영 체제 | [!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> 윈도우 10 |
| 32비트/64비트 지원 | 32비트 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 를 실행하는 32비트 Windows에서 32비트 애플리케이션을 테스트할 수 있습니다.<br /><br /> 32비트 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 를 실행하는 64비트 Windows에서 UI 동기화 기능이 있는 32비트 WOW 애플리케이션을 테스트할 수 있습니다.<br /><br /> 32비트 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 를 실행하는 64비트 Windows에서 UI 동기화 기능이 없는 64비트 Windows Forms 및 WPF 애플리케이션을 테스트할 수 있습니다. |
| Architecture | x86 및 x64 **참고:**  Internet Explorer는 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 이상 버전에서 실행하는 경우를 제외하고는 64비트 모드에서 지원되지 않습니다. |
| .NET | .NET 2.0, 3.0, 3.5, 4 및 4.5. **참고:** [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 및 Visual Studio를 작동하려면 .NET 4가 필요합니다. 그러나 여기 나열된 .NET 버전을 사용하여 개발한 애플리케이션은 모두 지원됩니다. |

> [!NOTE]
> *UI 동기화* 는 각 컨트롤의 메시지 큐에서 재생을 확인할 수 있는 기능입니다. 컨트롤에 이벤트를 보내도 컨트롤이 응답하지 않으면 이벤트가 다시 전달됩니다.

## <a name="platform-support"></a>플랫폼 지원

| 플랫폼 | 지원 수준 |
|-| - |
| Windows Phone 앱 | WinRT-XAML 기반 휴대폰 앱만 지원됩니다. |
| UWP 앱 | XAML 기반 UWP 앱만 지원됩니다. |
| 유니버설 Windows 앱 | 휴대폰 및 데스크톱의 XAML 기반 유니버설 Windows 앱만 지원됩니다. |
| Microsoft Edge | 작업 단계를 기록하거나 작성기를 사용하여 개체 속성을 보는 것은 지원되지 않습니다. 테스트는 [코딩된 UI 브라우저 간 테스트 확장](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting)을 통해 Visual Studio 2015 업데이트 2 이상 버전을 사용하여 Microsoft Edge 브라우저에서 재생할 수 있습니다. |
| Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **중요:** Internet Explorer 10은 데스크톱에서만 지원됩니다. <br /><br /> Internet Explorer 11 **중요:** Internet Explorer 11은 데스크톱에서만 지원됩니다. | 완전하게 지원됨<br /><br /> -   **Internet Explorer 9 및 Internet Explorer 10에서 HTML5 지원:** 코딩된 UI 테스트는 HTML5 컨트롤: Audio, Video, ProgressBar 및 Slider의 기록, 재생 및 유효성 검사를 지원합니다. 자세한 내용은 [코딩된 UI 테스트에서 HTML5 컨트롤 사용](../test/using-html5-controls-in-coded-ui-tests.md)을 참조하세요. **경고:**      Internet Explorer 10에서 코딩된 UI 테스트를 만드는 경우 Internet Explorer 9 또는 Internet Explorer 8을 사용하여 실행하지 못할 수 있습니다. Internet Explorer 10에는 오디오, 비디오, 진행률 표시줄 및 슬라이더와 같은 HTML5 컨트롤이 포함되기 때문입니다. 이러한 HTML5 컨트롤은 Internet Explorer 9 또는 Internet Explorer 8로 인식되지 않습니다. 마찬가지로, Internet Explorer 9를 사용하여 코딩된 UI 테스트는 Internet Explorer 8에서 인식되지 않는 일부 HTML5 컨트롤을 포함할 수 있습니다.<br />-   **Internet Explorer 10 맞춤법 검사 지원:** Internet Explorer 10은 모든 텍스트 상자의 맞춤법 검사 기능을 포함합니다. 이렇게 하면 추천 단어 목록에서 선택할 수 있습니다. 코딩된 UI 테스트는 다른 철자 제안 선택하기와 같은 사용자 작업을 무시합니다. 텍스트 상자에 입력한 마지막 텍스트만 기록됩니다.<br />     다음 작업은 맞춤법 검색 컨트롤(사전에 추가, 복사, 모두 선택, 사전에 추가 및 무시)을 사용하는 코딩된 UI 테스트에 대해 기록됩니다.<br />-   **Windows 8을 실행하는 64비트 Internet Explorer 지원:** 이전에는 64비트 버전의 Internet Explorer는 기록과 재생을 지원하지 않았습니다. [!INCLUDE[win8](../debugger/includes/win8_md.md)] 및 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]에서는 64비트 버전의 Internet Explorer에 대해 코딩된 UI 테스트를 사용하도록 설정되었습니다. **경고:**      Internet Explorer에 대한 64비트 지원은 [!INCLUDE[win8](../debugger/includes/win8_md.md)] 이상이 실행 중일 때에만 적용됩니다.<br />-   **Internet Explorer 9 사이트 고정에 대한 지원:** Internet Explorer 9에는 고정된 사이트 기능이 도입되었습니다. 고정된 사이트를 사용하여 Internet Explorer를 먼저 열지 않고도 Windows 작업 표시줄을 통해 직접 즐겨 찾는 사이트를 방문할 수 있습니다. 이제 코딩된 UI 테스트가 고정된 사이트에서 의도 인식 작업을 생성할 수 있습니다. 고정된 사이트에 대한 자세한 내용은 [고정된 사이트](https://support.microsoft.com/hub/4230784/internet-explorer-help)를 참조하세요.<br />-   **Internet Explorer 9 의미 태그 지원:** Internet Explorer 9는 section, nav, article, aside, hgroup, header, footer, figure, figcaption 및 mark 같은 의미 태그를 소개했습니다. 코딩된 UI 테스트는 기록하는 동안 이러한 의미 태그를 모두 무시합니다. 코딩된 UI 테스트 빌더를 사용해서 이러한 태그에 어설션을 추가할 수 있습니다. 코딩된 UI 테스트 빌더에서 탐색 다이얼을 사용하여 이러한 요소를 탐색하고 해당 속성을 볼 수 있습니다.<br />-   **Internet Explorer 버전 간에 공백 문자의 완벽한 처리:** Internet Explorer 8, Internet Explorer 9 및 Internet Explorer 10 사이에 공백 문자를 처리하는 데 차이점이 있습니다. 코딩된 UI 테스트는 이러한 차이를 원활하게 처리합니다. 따라서, 예를 들어 Internet Explorer 8에서 만든 코딩된 UI 테스트는 Internet Explorer 9 및 Internet Explorer 10에서 성공적으로 재생됩니다.<br />-   **Internet Explorer의 알림 영역이 “오류 발생 시 계속” 특성 집합으로 기록됨:** Internet Explorer의 알림 영역에서 모든 작업이 “오류 발생 시 계속” 특성 집합으로 기록됩니다. 재생하는 동안 알림 표시줄이 나타나지 않는 경우 여기에서의 작업은 무시되고 코딩된 UI 테스트가 다음 작업을 계속합니다. |
| Windows Forms 및 WPF 타사 컨트롤 | 완전하게 지원됨<br /><br /> Windows Forms 및 WPF 애플리케이션에서 타사 컨트롤을 사용하려면 참조 및 코드를 추가해야 합니다. 자세한 내용은 [컨트롤의 자동화된 UI 테스트 사용](../test/enable-coded-ui-testing-of-your-controls.md)을 참조하세요. |
| Internet Explorer 6<br /><br /> Internet Explorer 7 | 지원되지 않습니다. |
| Chrome<br /><br /> Firefox | 작업 단계 기록은 지원되지 않습니다. 코딩된 UI 테스트는 Visual Studio 2012 Update 4 이상에서 Chrome 및 Firefox 브라우저로 재생할 수 있습니다. 자세한 내용을 보려면 [여기](using-different-web-browsers-with-coded-ui-tests.md) 로 이동하세요. |
| Opera<br /><br /> Safari | 지원되지 않습니다. |
| Silverlight | 지원되지 않습니다.<br /><br /> 그러나 Visual Studo 2013의 경우 Visual Studio 갤러리에서 [Silverlight용 Microsoft Visual Studio 2013 코딩된 UI 테스트 플러그 인](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudio2013CodedUITestPluginforSilve)을 다운로드할 수 있습니다. |
| Flash/Java | 지원되지 않습니다. |
| Windows Forms 2.0 이상 | 완전하게 지원됨 **참고:** NetFx 컨트롤은 완전하게 지원되지만 일부 타사 컨트롤은 지원되지 않습니다. |
| WPF 3.5 이상 | 완전하게 지원됨<br /><br /> **참고** NetFx 컨트롤은 완전하게 지원되지만 일부 타사 컨트롤은 지원되지 않습니다. |
| Windows Win32 | 작동은 하지만 일부 알려진 문제가 있을 수 있으며, 공식적으로는 지원되지 않습니다. |
| MFC | 부분적으로 지원됩니다. 지원되는 기능에 대한 자세한 내용은 [UITest 프레임워크](https://blogs.msdn.microsoft.com/vstsqualitytools/2010/04/15/uitest-framework-mfc-support-in-vs-2010/)를 참조하세요. |
| SharePoint | 완전하게 지원됨 |
| Office 클라이언트 애플리케이션 | 지원되지 않습니다. |
| 동적 CRM 웹 클라이언트 | 완전하게 지원됨 |
| Dynamics (Ax) 2012 클라이언트 | 작업 기록 및 재생이 부분적으로 지원됩니다. 자세한 내용은 [Microsoft Dynamics에 대한 Visual Studio 10 코딩된 UI/작업 기록 지원](https://blogs.msdn.microsoft.com/dave_froslie/2011/09/01/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012/)을 참조하세요. |
| SAP | 지원되지 않습니다. |
| Citrix/터미널 서비스 | 터미널 서버에는 작업을 기록하지 않는 것이 좋습니다. 레코더에서는 동시에 여러 인스턴스를 실행할 수 없습니다. |
| PowerBuilder | 부분적으로 지원됩니다.<br /><br /> 지원 범위는 PowerBuilder 컨트롤에서 액세스할 수 있는 범위까지입니다. |

다른 플랫폼을 지원하기 위한 확장을 만드는 방법에 대한 자세한 내용은 [컨트롤의 코딩된 UI 테스트 사용](../test/enable-coded-ui-testing-of-your-controls.md) 및 [코딩된 UI 테스트 및 작업 기록 확장](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [UI 자동화를 사용하여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)
