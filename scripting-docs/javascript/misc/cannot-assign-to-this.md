---
title: "' This '에 할당할 수 없습니다. | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5c52153da64ff477d89b09d4af17169da18e4e1
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817322"
---
# <a name="cannot-assign-to-this"></a>'this'에 할당할 수 없습니다.
**이**에 값을 할당 하려고 했습니다. **this** [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 다음 중 하나를 참조 하는 키워드입니다.

- 현재 메서드를 실행 하는 개체입니다.

- 현재 메서드가 없거나 메서드가 다른 개체에 속하지 않는 경우 전역 개체입니다.

메서드는 개체를 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 통해 호출 되는 함수입니다. 메서드 내에서 this 키워드는 메서드가 호출 된 개체에 대 한 참조입니다. **이** 는 **new** 연산자를 사용 하 여 클래스 생성자를 호출 하 여 만든 개체입니다.

메서드 내에서 **이** 를 사용 하 여 현재 개체를 참조할 수 있지만 **이**에 새 값을 할당할 수는 없습니다.

## <a name="to-correct-this-error"></a>이 오류를 해결하려면

- **이**에 할당 하려고 하지 않습니다. 인스턴스화된 개체의 속성 또는 메서드에 액세스 하려면 점 연산자 (예: **circle. radius**)를 사용 합니다.

  > [!NOTE]
  > 사용자가 **만든 변수의 이름을**지정할 수 없습니다. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]예약어입니다.

## <a name="see-also"></a>참고 항목

- [this 문](../../javascript/reference/this-statement-javascript.md)
- [스크립트 문제 해결](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)