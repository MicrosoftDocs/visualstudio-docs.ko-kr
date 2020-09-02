---
title: 클래스 디자이너의 Visual C++ 구조체 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc9c09c5f92c4193d3d3f58c819f4bc0fc9aaebf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646760"
---
# <a name="visual-c-structures-in-class-designer"></a>클래스 디자이너의 Visual C++ 구조체
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

클래스 디자이너는 `struct` 키워드로 선언된 C++ 구조체를 지원합니다. 다음은 예제입니다.

```
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

 `struct` 형식을 사용하는 방법에 대한 자세한 내용은 [구조체](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)를 참조하세요.

 레이블이 **구조체**를 읽고 둥근 모서리 대신 사각형 모서리를 갖고 있다는 점을 제외하고, 클래스 다이어그램에서 C++ 구조체 모양은 클래스 모양처럼 보이고 실제 그러한 작용을 합니다.

|Code 요소|클래스 디자이너 보기|
|------------------|-------------------------|
|`struct StructureName {};`|**StructureName**<br /><br /> 구조체|

## <a name="see-also"></a>관련 항목
 [클래스 디자이너 (Visual C++ 코드)](../ide/working-with-visual-cpp-code-class-designer.md) [클래스 및 구조체](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873) [구조체](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6) 사용
