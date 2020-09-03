---
title: 식별자에 대 한 문 완성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f5e52bf174e5a41d79fa23bfca39121db668e40e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72643854"
---
# <a name="statement-completion-for-identifiers"></a>식별자 문 완성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript에서는 변수 선언에 대 한 명시적 형식화를 허용 하지 않습니다. 따라서 IntelliSense는 항상 개체에 대 한 완성 목록을 제공할 수 없습니다. 이는 다양 한 상황에서 발생할 수 있습니다. 다음은 몇 가지 일반적인 것입니다.

- 다음 예제와 같이 매개 변수가 선언 되었지만 활성 문서의 다른 위치에서 호출 되지 않았습니다.

  ```javascript
  function illuminate(light) {
           light.  // Accurate statement completion is not available
                   // unless illuminate is called elsewhere with a
                   // parameter that has a value. If it is called only
                   // in a function that is a sibling to
                   // illuminate(light) in the call hierarchy, the
                   // IntelliSense engine also cannot determine the
                   // parameter type.
       }

  // Sibling function. No statement completion for light
  // object in preceding code.
  function lightLamp() {
      var x = illuminate(1);
  }

  // Uncomment the next line to obtain statement completion for
  // light object in preceding code.
  // var x = illuminate(1);
  ```

- 개체는 이벤트에 대 한 응답으로 호출 되는 함수에 있습니다. 디자인 타임에 IntelliSense 엔진은이 상황에서 사용 되는 개체의 형식을 확인할 수 없습니다.

   IntelliSense 엔진이 일반적으로 활성 문서의 이벤트에 대해를 사용 하 여 이벤트를 호출 해야 함을 결정할 수 있는 경우 `addEventListener` 보다 정확한 IntelliSense 정보가 제공 됩니다.

  IntelliSense에서 개체를 식별할 수 없는 경우 IntelliSense 엔진은 활성 문서에 있는 명명 된 엔터티 또는 식별자를 사용 하 여 완성 목록을 채웁니다. 완성 목록에 이러한 식별자가 포함 되어 있으면 해당 식별자 옆에 정보 아이콘이 표시 됩니다. 또한 각 식별자에 대 한 도구 설명은 식을 알 수 없음을 나타냅니다. 다음 그림에서는 `light` 개체와 해당 속성이 정의 되어 있지 않기 때문에 식별할 수 없는 형식의 개체에 대 한 문 완성 옵션을 보여 줍니다. 그러나 속성은 `intensity` 함수에서 사용 되기 때문에 식별자 목록에서 사용할 수 있습니다 `illuminate` .

  **식별할 수 없는 개체에 대 한 완료 옵션**

  ![식별자에 대한 JavaScript IntelliSense](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")

  XML 문서 주석 또는 JavaScript IntelliSense 확장성 기능을 사용 하 여 개체에 대 한 완성 목록을 재정의할 수 있습니다. 이러한 기능을 사용 하면 형식 정보를 제공 하 고, 다른 방법으로는 사용 하지 못할 수 있는 경우 보다 설명적인 IntelliSense 정보를 제공할 수 있습니다. 자세한 내용은 [JavaScript IntelliSense 확장](../ide/extending-javascript-intellisense.md) 및 [XML 문서 주석 만들기](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)를 참조 하세요.

## <a name="see-also"></a>관련 항목
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
