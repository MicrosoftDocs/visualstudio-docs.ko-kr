---
description: 문자열을 URI로 인코드 하려고 했지만 잘못 된 문자가 포함 되어 있습니다.
title: 인코딩할 URI에 잘못 된 문자가 포함 되어 있습니다. | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5024
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a3f0fdbb-8d4b-41ae-a396-43dfc9483760
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 73ed9a814c5d608df1a9686c2b61166d664115f7
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570663"
---
# <a name="the-uri-to-be-encoded-contains-an-invalid-character"></a>인코딩할 URI에 잘못된 문자가 들어 있습니다.
문자열을 URI (Uniform Resource Identifier)로 인코드 하려고 했지만 잘못 된 문자가 포함 되어 있습니다. 대부분의 문자는 Uri로 변환할 문자열 내에서 유효 하지만 일부 유니코드 문자 시퀀스는 올바르지 않습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
- 인코딩할 문자열이 유효한 유니코드 시퀀스만 포함 하는지 확인 합니다. 전체 URI는 구성 요소 및 구분 기호의 시퀀스로 구성 됩니다. 꺾쇠 괄호 안의 이름은 구성 요소를 나타내고, ":", "/", ";" 및 "?"는 구분 기호로 사용 되는 예약 된 문자입니다. 일반적인 형식은 다음과 같습니다.  
  
    ```JavaScript  
    <Scheme>:<first>/<second>;<third>?<fourth>  
    ```  
  
## <a name="see-also"></a>참조  
 [encodeURI 함수](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuri)   
 [encodeURIComponent 함수](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/encodeuricomponent)
