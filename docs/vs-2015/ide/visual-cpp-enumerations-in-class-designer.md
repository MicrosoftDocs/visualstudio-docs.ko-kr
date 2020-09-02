---
title: 클래스 디자이너의 Visual C++ 열거형 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f967420e37d6337ce6d86cc56524f2751218f56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651658"
---
# <a name="visual-c-enumerations-in-class-designer"></a>클래스 디자이너의 Visual C++ 열거형
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

클래스 디자이너는 C++ `enum` 및 범위가 지정된 `enum class` 형식을 지원합니다. 다음은 예제입니다.

```
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

```

 클래스 다이어그램의 C++ 열거형 도형은 레이블이 **Enum** 또는 **Enum 클래스**로 표시되고, 파란색이 아니라 분홍색이며, 왼쪽 및 위쪽 여백에 색이 지정된 테두리가 있다는 점을 제외하고 구조체 도형과 모양 및 기능이 유사합니다. 열거형 도형과 구조체 도형에는 사각형 모서리가 있습니다.

 `enum` 형식을 사용하는 방법에 대한 자세한 내용은 [열거형](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3)을 참조하세요.

## <a name="see-also"></a>관련 항목
 [클래스 디자이너 (Visual C++ 코드)](../ide/working-with-visual-cpp-code-class-designer.md) [열거형](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3) 사용
