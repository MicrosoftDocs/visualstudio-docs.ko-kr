---
title: 배열 길이는 유한 양의 정수 여야 합니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5029
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa8b9a85c0c7457cb06d36fd3cd849ce48484b46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817088"
---
# <a name="array-length-must-be-a-finite-positive-integer"></a>배열 길이는 유한 양의 정수여야 합니다.
정수가 아닌 인수를 사용 하 여 **배열** 생성자를 호출 하 고 있습니다. 정수는 0과 양의 정수 집합으로 구성 됩니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 새 개체를 만들 때만 양의 정수를 사용 `Array` 합니다. 정수가 아닌 단일 요소를 사용 하 여 배열을 만들려면 2 단계 프로세스에서 수행 합니다. 먼저 요소가 하나인 배열을 만든 다음 첫 번째 요소 (array [0])에 값을 넣습니다. 다음은이 오류를 생성 하는 예제입니다.  
  
    ```JavaScript  
    var piArray = new Array(3.14159);  
    ```  
  
     다음 예제에서는 단일 숫자 요소를 사용 하 여 배열을 지정 하는 올바른 방법을 보여 줍니다.  
  
    ```JavaScript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     최대 정수 값 (약 40억)이 아닌 배열의 크기에 대 한 상한이 없습니다.  
  
## <a name="see-also"></a>추가 정보  
 [배열 사용](../../javascript/advanced/using-arrays-javascript.md)