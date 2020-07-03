---
title: 방법 - 웹 페이지에서 JavaScript 코드 프로파일링 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- JavaScript performance profiling
- Profiling Tools,JavaScript
- web site performance profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9c0af520502a0d6bb67d17786ab18fba920fcbbb
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328892"
---
# <a name="how-to-profile-javascript-code-in-web-pages"></a>방법: 웹 페이지에서 JavaScript 코드 프로파일링

Visual Studio 프로파일링 도구는 계측 프로파일링 방법을 사용하여 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션, 임의 웹 페이지 또는 JavaScript 애플리케이션에서 실행되는 JavaScript 코드에 대한 성능 데이터를 수집할 수 있습니다. Internet Explorer 8 이상이 필요합니다.

> [!WARNING]
> UWP에서 JavaScript를 프로파일링하려면 [JavaScript 메모리](../profiling/javascript-memory.md)를 참조하세요.

프로파일링 마법사를 사용하여 성능 세션을 만들 수 있습니다. 계측 방법을 지정한 다음 성능 세션에 대한 속성 대화 상자의 계측 페이지에서 JavaScript 프로파일링 옵션을 지정합니다.

JavaScript 프로파일링을 지정하면 브라우저에서 실행되는 JavaScript 코드 및 서버에서 실행되는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 코드가 둘 다 프로파일링됩니다.

- [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 애플리케이션의 경우 브라우저에서 실행되는 JavaScript 코드 및 서버에서 실행되는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 코드가 둘 다 프로파일링됩니다.

- 임의 웹 페이지의 경우 브라우저에서 실행되는 JavaScript 코드가 프로파일링됩니다.

## <a name="to-profile-javascript-in-an-aspnet-web-application-project"></a>ASP.NET 웹 애플리케이션 프로젝트에서 JavaScript를 프로파일링하려면

1. Visual Studio에서 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 웹 프로젝트를 엽니다.

2. **분석** 메뉴에서 **성능 마법사 시작**을 클릭합니다.

3. 성능 마법사의 첫 페이지에서 **계측** 프로 파일링 방법을 지정하고 **다음**을 클릭합니다.

4. 마법사의 두 번째 페이지에서 현재 프로젝트가 대상 목록에서 선택되었는지 확인하고 **다음**을 클릭합니다.

5. 마법사의 세 번째 페이지에서 **JavaScript 프로파일링** 확인란을 선택하고 **다음**을 클릭합니다.

6. 마법사의 네 번째 페이지에서 **마침**을 클릭하여 브라우저에서 웹 애플리케이션을 시작합니다.

7. 프로파일링하려는 기능을 실행합니다.

8. 프로파일링 세션을 종료하려면 브라우저를 닫습니다.

### <a name="to-profile-javascript-in-individual-web-pages-or-a-javascript-applications"></a>개별 웹 페이지 또는 JavaScript 애플리케이션에서 JavaScript를 프로파일링하려면

1. Visual Studio를 엽니다.

2. **분석** 메뉴에서 **성능 마법사 시작**을 클릭합니다.

3. 성능 마법사의 첫 페이지에서 **계측** 프로 파일링 방법을 지정하고 **다음**을 클릭합니다.

4. 마법사의 두 번째 페이지에서 ASP.NET 또는 JavaScript 애플리케이션을 클릭한 후 **다음**을 클릭합니다.

5. 마법사의 세 번째 페이지에서 다음을 수행합니다.

    1. **애플리케이션을 실행할 URL 또는 경로** 상자에 페이지의 URL을 입력합니다.

    2. **JavaScript 프로파일링** 확인란을 선택하고 **다음**을 클릭합니다.

6. 마법사의 네 번째 페이지에서 **마침** 을 클릭하여 브라우저에서 웹 페이지를 시작합니다.

7. 프로파일링하려는 기능을 실행합니다.

8. 프로파일링 세션을 종료하려면 브라우저를 닫습니다.
