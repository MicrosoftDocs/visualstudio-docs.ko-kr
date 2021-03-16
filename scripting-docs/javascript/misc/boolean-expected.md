---
description: 부울이 아닌 다른 형식의 개체에 대해 valueOf 메서드를 호출 하려고 한 경우.
title: 부울이 필요 합니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5010
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ceaddc9341d67ac60326fa7121c32655ab6a3f6
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571443"
---
# <a name="boolean-expected"></a>부울이 필요합니다.
가 아닌 형식의 개체에 대해 **valueOf** **메서드를 호출** 하려고 한 경우를 `Boolean` 말합니다. 이 호출 형식의 개체는 형식 이어야 합니다 `Boolean` . 예를 들어:

```JavaScript
var o = new Object;
o.f = Boolean.prototype.toString;
o.f();
```

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- **부울** 형식의 개체에 대해서만 **valueOf** **메서드를 호출 합니다.**

## <a name="see-also"></a>참조

- [Boolean 개체](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- [데이터 형식](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
- [프로그램 흐름 제어](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [데이터 복사, 전달 및 비교](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Functions)
