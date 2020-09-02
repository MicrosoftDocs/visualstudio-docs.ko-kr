---
title: '방법: 기존 형식 보기(클래스 디자이너) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 925220d583695e0116fb5901d92626bfcfa7450f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670536"
---
# <a name="how-to-view-existing-types-class-designer"></a>방법: 기존 형식 보기(클래스 디자이너)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

기존 형식 및 해당 멤버를 보려면 클래스 다이어그램에 해당 모양을 추가합니다.

 로컬 및 참조 형식을 볼 수 있습니다. 로컬 형식은 현재 열린 프로젝트에 있으며 읽기/쓰기가 가능하고, 참조 형식은 다른 프로젝트나 참조 어셈블리에 있으며 읽기 전용입니다.

 클래스 다이어그램에서 새 형식을 디자인 하려면 [방법: 클래스 디자이너를 사용 하 여 형식 만들기](../ide/how-to-create-types-by-using-class-designer.md)를 참조 하세요.

### <a name="to-see-types-in-a-project-on-a-class-diagram"></a>클래스 다이어그램에서 프로젝트의 형식을 보려면

1. 솔루션 탐색기의 프로젝트에서 기존 클래스 다이어그램(.cd) 파일을 엽니다. 또는 클래스 다이어그램이 없으면 프로젝트에 새 클래스 다이어그램을 추가합니다. [방법: 프로젝트에 클래스 다이어그램 추가(클래스 디자이너)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)을 참조하세요.

2. 솔루션 탐색기의 프로젝트에서 소스 코드 파일을 클래스 다이어그램으로 끌어 놓습니다.

   > [!WARNING]
   > 여러 앱 간에 코드를 공유하는 프로젝트가 솔루션에 포함되어 있는 경우 다음 소스에서만 파일이나 코드를 클래스 다이어그램으로 끌어 올 수 있습니다.
   >
   > - 다이어그램을 포함하는 앱 프로젝트
   >   - 앱 프로젝트로 가져온 공유 프로젝트
   >   - 참조된 프로젝트
   >   - 어셈블리

    소스 코드 파일에 정의된 형식을 나타내는 모양은 다이어그램에서 파일을 끌어 놓은 위치에 표시됩니다.

   클래스 뷰의 프로젝트 노드에서 클래스 다이어그램으로 하나 이상의 형식을 끌어 놓아 프로젝트에 있는 형식을 볼 수도 있습니다.

> [!TIP]
> 클래스 뷰가 열려 있지 않으면 **보기** 메뉴에서 클래스 뷰를 엽니다. 클래스 뷰에 대한 자세한 내용은 [클래스 및 해당 멤버 보기](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333)를 참조하세요.

 다이어그램의 기본 위치에 형식을 표시 하려면 클래스 뷰에서 하나 이상의 형식을 선택 하 고 선택한 형식을 마우스 오른쪽 단추로 클릭 한 다음 **클래스 다이어그램 보기**를 선택 합니다.

> [!NOTE]
> 프로젝트에 있는 형식을 포함하는 클래스 다이어그램이 닫혀 있으면 해당 클래스 다이어그램이 열리고 형식 모양이 표시됩니다. 그러나 프로젝트에 있는 형식이 어떤 클래스 다이어그램에도 포함되어 있지 않으면 클래스 디자이너가 프로젝트에 새 다이어그램을 만들고 열어 형식을 표시합니다.

 다이어그램에 형식을 처음 표시하면 기본적으로 해당 모양이 축소되어 표시됩니다. 모양을 확장하여 내용을 볼 수 있습니다.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>클래스 다이어그램에서 프로젝트 내용을 표시하려면

1. 솔루션 탐색기 또는 클래스 뷰에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **보기**, **클래스 다이어그램 보기**를 차례로 선택 합니다.

     자동으로 채워진 클래스 다이어그램이 만들어집니다.

## <a name="see-also"></a>관련 항목
 [방법: 형식 간의 상속 보기 (클래스 디자이너)](../ide/how-to-view-inheritance-between-types-class-designer.md) [방법: 클래스 다이어그램 사용자 지정 (클래스 디자이너)](../ide/how-to-customize-class-diagrams-class-designer.md) [형식 및 관계 보기 (클래스 디자이너)](../ide/viewing-types-and-relationships-class-designer.md)
