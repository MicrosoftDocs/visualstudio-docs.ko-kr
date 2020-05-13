---
title: '방법: 웹 사이트에 대한 성능 데이터 수집 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8b5cacba328c48b682fe9069d8ab4a9ee21635db
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79307186"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>방법: 웹 사이트에 대한 성능 데이터 수집

**웹 애플리케이션에 대한 성능 데이터를 수집하려면**성능 마법사[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]를 사용할 수 있습니다. Visual Studio에 열려 있는 웹 애플리케이션을 프로파일링하거나, 로컬 컴퓨터에 있고 Visual Studio IDE에 열려 있지 않은 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 사이트를 프로파일링할 수 있습니다.

> [!NOTE]
> **성능 마법사** 에서는 계층 상호 작용(TIP) 데이터, JScript 성능 데이터 또는 둘 모두를 수집된 프로파일링 데이터에 추가할 수 있습니다. TIP 옵션은 서버 쪽 프로세스에서 데이터를 수집합니다. JScript 프로파일링은 로컬 또는 원격 웹 사이트에서 실행 중인 스크립트에서 데이터를 수집합니다. 대부분의 경우 옵션을 하나만 선택해야 합니다.

 관리자가 사용 가능하도록 설정한 사용자 액세스 권한 설정에 따라 개별 사용자는 ASP.NET 프로세스를 호스트하는 컴퓨터에서 프로파일러 세션을 만들 수 있는 보안 권한을 갖거나 갖지 못할 수 있습니다. 다음 예제에서는 사용자 간에 가능한 차이점을 보여 줍니다.

- 관리자가 드라이버 및 서비스를 시작하도록 설정한 경우 일부 사용자는 고급 프로파일링 기능에 액세스할 수 있습니다.

- 도메인 사용자는 샘플 프로파일링에만 액세스가 가능할 수 있습니다.

- 일부 사용자는 다른 모든 사용자에 대한 프로파일링에 액세스하지 못할 수 있습니다.

  자세한 내용은 [프로파일링 및 Windows Vista 보안](../profiling/profiling-and-windows-vista-security.md) 및 [VSPerfCmd](../profiling/vsperfcmd.md)의 ADMIN 옵션을 참조하세요.

## <a name="to-profile-a-web-site-project"></a>웹 사이트 프로젝트를 프로파일링하려면

1. Visual Studio에서 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 프로젝트를 엽니다.

2. **분석** 메뉴에서 **성능 프로파일러**를 선택하고 **성능 탐색기**를 선택한 다음 **시작**을 선택합니다.

3. 마법사의 첫 번째 페이지에서 프로파일링 방법을 선택하고 **다음**을 클릭합니다. 프로파일링 방법에 대한 자세한 내용은 [성능 컬렉션 메서드 이해](../profiling/understanding-performance-collection-methods.md)를 참조하세요. 동시성 시각화 도우미 프로파일링 방법은 웹 애플리케이션에 사용할 수 없습니다.

4. **다음 애플리케이션 중 프로파일링할 대상을 선택하세요.** 드롭다운 목록에서 현재 프로젝트가 선택되어 있는지 확인하고 **다음**을 클릭합니다.

5. 마법사의 세 번째 페이지에서 TIP(계층 상호 작용 프로파일링) 데이터, 웹 페이지에서 실행 중인 JavaScript의 데이터 또는 둘 모두를 선택할 수 있습니다.

    - 계층 상호 작용을 수집하려면 **계층 상호 작용 프로파일링 사용** 확인란을 선택합니다.

    - 웹 페이지에서 실행 중인 JavaScript에서 데이터를 수집하려면 **JavaScript 프로파일링** 확인란을 선택합니다.

6. **다음**을 클릭합니다.

7. 마법사의 네 번째 페이지에서 **마침**을 클릭합니다.

8. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 애플리케이션에 대해 성능 세션이 만들어지고 브라우저에서 웹 사이트가 시작됩니다. 프로파일링을 수행할 기능을 실행하고 브라우저를 닫습니다.

     프로파일러는 데이터 파일을 생성하고 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 주 창에 데이터의 요약 보기를 표시합니다.

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Visual Studio에서 프로젝트를 열지 않고 웹 사이트를 프로파일링하려면

1. Visual Studio를 엽니다.

2. **분석** 메뉴에서 **성능 프로파일러**를 선택하고 **성능 탐색기**를 선택한 다음 **시작**을 선택합니다.

3. 마법사의 첫 번째 페이지에서 프로파일링 방법을 선택하고 **다음**을 클릭합니다. 자세한 내용은 [성능 컬렉션 메서드 이해](../profiling/understanding-performance-collection-methods.md)를 참조하세요.

4. 마법사의 두 번째 페이지에서 **ASP.NET 또는 JavaScript 애플리케이션 프로파일링** 옵션을 선택하고 **다음**을 클릭합니다.

5. 마법사의 세 번째 페이지에서 **웹 애플리케이션이 실행될 URL 또는 경로** 상자에 애플리케이션 홈 페이지에 대한 URL을 입력하고 **다음**을 클릭합니다.

   - 서버(IIS) 기반 웹 사이트의 경우 **<`http://localhost/MySite/default.aspx`>** 와 같은 URL을 입력합니다. 이렇게 하면 MySite의 애플리케이션 루트에서 로컬 컴퓨터의 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 애플리케이션이 프로파일링되며, 해당 사이트의 default.aspx 페이지가 Internet Explorer에서 시작되어 세션이 시작됩니다.

   - 파일 기반 웹 사이트에는 file///**c:\WebSites\MySite\default.aspx**같은 경로를 입력합니다. 이렇게 하면 c:\webSites\MySite에 있는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 애플리케이션이 프로파일링되고 `http://localhost:nnnn/MySite/default.aspx` 페이지가 Internet Explorer에서 시작되어 세션이 시작됩니다.

   - JavaScript 데이터를 수집할 외부 사이트에는 `http://www.contoso.com`과 같은 URL을 입력합니다.

     자세한 내용은 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 대상 이진에 대한 속성 페이지를 참조하세요.

6. 마법사의 세 번째 페이지에서 TIP(계층 상호 작용 프로파일링) 데이터, 웹 페이지에서 실행 중인 JavaScript의 데이터 또는 둘 모두를 선택할 수 있습니다.

    - 계층 상호 작용을 수집하려면 **계층 상호 작용 프로파일링 사용** 확인란을 선택합니다.

    - 웹 페이지에서 실행 중인 JavaScript에서 데이터를 수집하려면 **JavaScript 프로파일링** 확인란을 선택합니다.

7. **다음**을 클릭합니다.

8. 마법사의 네 번째 페이지에서 **마침**을 클릭합니다.

9. ASP.NET 앱에 대한 성능 세션이 만들어지고 브라우저에서 웹 사이트가 시작됩니다. 프로파일링을 수행할 기능을 실행하고 브라우저를 닫습니다.

     프로파일러는 데이터 파일을 생성하고 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 주 창에 데이터의 요약 보기를 표시합니다.

## <a name="see-also"></a>참고 항목

[개요](../profiling/overviews-performance-tools.md)
[성능 세션 구성](../profiling/configuring-performance-sessions.md)
[계측 데이터 값 이해](../profiling/understanding-instrumentation-data-values.md)
[샘플링 데이터 값 이해](../profiling/understanding-sampling-data-values.md)
