---
title: RequireJS 용 IntelliSense 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 279ac7737460c90f86918ae673e8f64ef1215546
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665891"
---
# <a name="customizing-intellisense-for-requirejs"></a>RequireJS용으로 IntelliSense 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2013 업데이트 4부터는 널리 사용되는 RequireJS JavaScript 파일 및 모듈식 로더가 지원됩니다. RequireJS를 사용하면 코드 모듈 간의 종속성을 더 쉽게 정의하고 필요할 때만 동적으로 모듈을 로드할 수 있습니다. RequireJS가 사용되는 JavaScript 코드를 작성할 때는 코드 내에서 `require()` 호출을 통해 참조하거나 모듈 정의에서 참조한 모듈에 대해 IntelliSense 제안 사항이 제공됩니다.

 기본적으로 Visual Studio는 RequireJS를 지원하기 위한 매우 기본적인 구성을 지원하지만 일반적으로는 사용자 지정 구성 설정을 지정(라이브러리에 대한 별칭을 정의)합니다. 이 항목에서는 프로젝트의 고유한 설정을 사용하도록 Visual Studio를 사용자 지정하는 여러 가지 방법을 설명합니다.

 이 항목에서는 이러한 방법에 대해 설명합니다.

- ASP.NET 프로젝트에서 RequireJS 사용자 지정

- Apache Cordova 앱, Windows 스토어 앱 및 LightSwitch HTML 앱을 빌드하는 데 사용되는 JSProj 프로젝트에서 RequireJS 사용자 지정

## <a name="customize-requirejs-in-aspnet-projects"></a>ASP.NET 프로젝트에서 RequireJS 사용자 지정
 현재 JavaScript 파일에서 require.js 파일을 참조할 때는 RequireJS 지원이 자동으로 설정됩니다. 자세한 내용은 [JavaScript IntelliSense](../ide/javascript-intellisense.md)의 IntelliSense 컨텍스트 확인 섹션을 참조하세요. ASP.NET 프로젝트에서 require.js 참조는 일반적으로 \<reference/> _references.js 파일 내에서///지시어를 사용 하 여 수행 됩니다.

### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>ASP.NET 프로젝트에서 data-main 특성 구성
 앱이 실행 할 때 작동하는 방식을 정확하게 시뮬레이트하려면 JavaScript 편집기에서 require.js를 설정할 때 처음으로 로드할 파일을 알고 있어야 합니다. 일반적으로는 아래에 나와 있는 것처럼 require.js를 참조하는 스크립트 요소에 대해 `data-main` 특성을 사용하여 애플리케이션 HTML 파일에서 이 파일을 구성합니다.

```html
<script src="js/require.js" data-main="js/app.js"></script>
```

 이 예제에서는 data-main이 참조하는 스크립트(js/app.js)는 require.js 바로 다음에 로드됩니다. 즉시 로드 되는 파일은를 사용 하 여 먼저 RequireJS 사용을 구성 하는 것이 가장 좋은 장소입니다 `require.config()` . 응용 프로그램에서에 사용할 파일을 JavaScript 편집기에 게 지시 하려면 `data-main` 특성을 추가한 `data-main` 다음 \<reference/> 응용 프로그램에서 require.js를 참조 하는///지시문을 수정 합니다. 예를 들어 다음 지시문을 사용할 수 있습니다.

```javascript
/// <reference path="js/require.js" data-main="js/app.js" />
```

### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>ASP.NET 프로젝트에서 애플리케이션 시작 페이지 구성
 앱이 실행 될 때 RequireJS는 파일에 대 한 상대 경로 (예: "... \\ " 경로)가 require.js 라이브러리를 로드 한 HTML 파일에 상대적인 것으로 가정 합니다. Visual Studio 편집기에서 ASP.NET 프로젝트용 코드를 작성할 때는 이 시작 페이지를 알 수 없으므로 상대 파일 경로 사용 시 사용할 시작 페이지를 편집기에서 지정해야 합니다. 이렇게 하려면 `start-page` ///지시문에 특성을 추가 \<reference/> 합니다.

```javascript
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />
```

 `start-page` 특성은 앱 실행 시 브라우저에서 표시되는 페이지의 URL을 지정합니다.

## <a name="customize-requirejs-in-jsproj-projects"></a>JSProj 프로젝트에서 RequireJS 사용자 지정
 .jsproj 확장명으로 끝나는 프로젝트 파일인 JSProj 프로젝트는 Apache Cordova용 앱, HTML 기반 Windows 스토어 앱 또는 LightSwitch HTML 앱을 빌드할 때 사용됩니다. ASP.NET 프로젝트와는 달리 이러한 프로젝트는 프로젝트에 있는 HTML 파일에서 .js 파일에 대한 참조를 읽습니다. 따라서 JSProj 프로젝트에서 JavaScript를 편집할 때 현재 편집 중인 JavaScript 파일이 require.js를 참조하는 다른 HTML 파일에서도 참조되는 경우에는 RequireJS 지원이 설정된 것으로 표시됩니다.

 ASP.NET 프로젝트에 대해 수행해야 하는 사용자 지정 단계를 JSProj 프로젝트 파일에서는 수행하지 않아도 됩니다. 즉, require.js를 참조하는 스크립트 태그의 `data-main` 특성에 사용되는 스크립트 파일은 자동으로 로드되어 require.js를 구성합니다. require.js를 참조하는 HTML 파일도 애플리케이션의 시작 페이지로 사용됩니다.

## <a name="see-also"></a>관련 항목
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
