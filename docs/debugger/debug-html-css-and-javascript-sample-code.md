---
title: HTML 및 CSS 샘플 코드 디버그 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 51893967-98c8-4141-ba40-03646f221760
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 460419d976211747c44f156a5821b88b75aa2e6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745540"
---
# <a name="debug-html-and-css-sample-code"></a>HTML 및 CSS 샘플 코드 디버그

이 항목의 코드는 다음 항목에 대한 샘플 파일입니다. [빠른 시작: HTML 및 CSS 디버그](../debugger/quickstart-debug-html-and-css.md). QuickStart에서 의도적으로 제공되는 오류는 이 버전의 코드에서 수정됩니다.

## <a name="sample-code"></a>샘플 코드
다음 HTML 코드는 빠른 시작의 \<body> 태그에서 사용됩니다.

```html
<div id="flipTemplate" data-win-control="WinJS.Binding.Template"
         style="display:none">
    <div class="fixedItem" >
        <img src="#" data-win-bind="src: flipImg" />
    </div>
</div>
<div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{
    itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">
</div>
```

다음 CSS에서는 default.css에 추가된 내용을 보여 줍니다.

```css
#fView {
    background-color:#0094ff;
    height: 500px;
    margin: 25px;
}
```

다음 코드 예제에서는 default.js의 전체 JavaScript 코드를 보여 줍니다. 이 코드의 WinJS 네임스페이스에 대한 참조는 템플릿의 default.html 파일에 있습니다.

```javascript
(function () {
    "use strict";

    var app = WinJS.Application;
    var activation = Windows.ApplicationModel.Activation;

    var myData = [];
    for (var x = 0; x < 3; x++) {
        myData[x] = { flipImg: "/images/logo.png" }
    };

    var pages = new WinJS.Binding.List(myData, { proxy: true });

    app.onactivated = function (args) {
        if (args.detail.kind === activation.ActivationKind.launch) {
            if (args.detail.previousExecutionState !==
            activation.ApplicationExecutionState.terminated) {
                // TODO: . . .
            } else {
                // TODO: . . .
            }
            args.setPromise(WinJS.UI.processAll());

            updateImages();
        }
    };

    function updateImages() {

        pages.setAt(0, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-76.jpg" });
        pages.setAt(1, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-77.jpg" });
        pages.setAt(2, { flipImg: "http://public-domain-photos.com/free-stock-photos-1/flowers/cactus-78.jpg" });
    };

    app.oncheckpoint = function (args) {
    };

    app.start();

    var publicMembers = {
        items: pages
    };

    WinJS.Namespace.define("Data", publicMembers);

})();
```

## <a name="see-also"></a>참조
- [빠른 시작: HTML 및 CSS 디버그](../debugger/quickstart-debug-html-and-css.md)
