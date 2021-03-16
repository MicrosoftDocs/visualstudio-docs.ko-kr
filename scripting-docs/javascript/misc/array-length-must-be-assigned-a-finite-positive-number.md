---
description: 기존 배열 개체의 length 속성을 설정할 때 양수 또는 0이 아닌 배열 길이를 지정 했습니다.
title: 배열 길이는 유한한 양수로 할당 해야 합니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3938f240580564112915ab0ba3036b63dc96cd8f
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103572145"
---
# <a name="array-length-must-be-assigned-a-finite-positive-number"></a>배열의 길이는 유한한 양수로 할당해야 합니다.
기존 **배열** 개체의 **length** 속성을 설정할 때 양수 또는 0이 아닌 배열 길이를 지정 했습니다. 이 오류는 음수가 아니거나 숫자가 아닌 개체의 **length** 속성에 값을 할당 하는 경우에 발생 `Array` `NaN` 합니다 (). 는 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 자동으로 소수 자릿수를 정수로 변환 합니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- Length 속성에 양의 정수를 할당 합니다. 최대 정수 값 (약 40억)이 아닌 배열의 크기에 대 한 상한이 없습니다. 다음 예제에서는 **배열** 개체의 **length** 속성을 설정 하는 올바른 방법을 보여 줍니다.  
  
    ```JavaScript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## <a name="see-also"></a>참조  
 [배열 사용](https://developer.mozilla.org/docs/Learn/JavaScript/First_steps/Arrays)
