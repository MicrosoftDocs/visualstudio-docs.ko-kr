---
description: 잘못 된 유니코드 이스케이프 시퀀스를 만들었습니다.
title: 16 진수가 필요 합니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 107ce2dd4f9a65a0a04b8e2ec773367ffae4ce81
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570429"
---
# <a name="expected-hexadecimal-digit"></a>16진수가 필요합니다.
잘못 된 유니코드 이스케이프 시퀀스를 만들었습니다. 유니코드 이스케이프 시퀀스는 \u로 시작 하 고 그 다음에 정확히 4 개의 16 진수 숫자 (더 이상 및 더 작은 값)가 나옵니다. 유니코드 16 진수는 숫자 0-9, 대문자 a-f 및 소문자 a-f만 포함할 수 있습니다. 다음 예제에서는 올바른 형식의 유니코드 이스케이프 시퀀스를 보여 줍니다.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 유니코드 16 진수가 \u로 시작 하 고, 숫자 0-9, 대문자 a-f, 소문자 a-f를 포함 해야 합니다. 및는 4 자리로 그룹화 됩니다.  
  
    > [!NOTE]
    > 문자열에서 리터럴 텍스트 \u를 사용 하려면 두 개의 백슬래시 ( \\ \u)를 사용 하 여 첫 번째 백슬래시를 이스케이프 합니다.  
  
## <a name="see-also"></a>참조  
 [데이터 형식](https://developer.mozilla.org/docs/Web/JavaScript/Data_structures)
