---
title: '방법: O-R 디자이너에서 생성 한 코드 확장 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1d60090ca16907e16bb58970d793124c5bb2dec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665953"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>방법: O/R 디자이너에서 생성된 코드 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]에서 생성한 코드는 디자이너 화면에서 엔터티 클래스 및 다른 개체를 변경하면 다시 생성됩니다. 이러한 코드의 다시 생성으로 인해 일반적으로 디자이너에서 코드를 다시 생성하면 생성된 코드에 추가한 모든 코드를 덮어씁니다. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]에서는 덮어쓸 수 없는 코드를 추가할 수 있는 partial 클래스 파일을 생성할 수 있는 기능을 제공합니다. 사용자 고유의 코드를 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]에서 생성한 코드에 추가하는 예는 데이터 유효성 검사를 LINQ to SQL(엔터티) 클래스에 추가하는 것입니다. 자세한 내용은 [방법: 엔터티 클래스에 유효성 검사 추가](../data-tools/how-to-add-validation-to-entity-classes.md)를 참조 하세요.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-code-to-an-entity-class"></a>엔터티 클래스에 코드 추가

#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Partial 클래스를 만들고 엔터티 클래스에 코드를 추가하려면

1. 에서 새 LINQ to SQL 클래스 파일 (**.dbml** 파일)을 열거나 만듭니다 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . ( **솔루션 탐색기** **.dbml** / 에서 .dbml 파일을 두 번 클릭 합니다. **데이터베이스 탐색기**)

2. 에서 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 유효성 검사를 추가 하려는 클래스를 마우스 오른쪽 단추로 클릭 한 다음 **코드 보기**를 클릭 합니다.

     선택한 엔터티 클래스의 partial 클래스와 함께 코드 편집기가 열립니다.

3. 엔터티 클래스의 partial 클래스 선언에 사용자 코드를 추가합니다.

## <a name="adding-code-to-a-datacontext"></a>DataContext에 코드 추가

#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Partial 클래스를 만들고 DataContext에 코드를 추가하려면

1. 에서 새 LINQ to SQL 클래스 파일 (**.dbml** 파일)을 열거나 만듭니다 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . ( **솔루션 탐색기** **.dbml** / 에서 .dbml 파일을 두 번 클릭 합니다. **데이터베이스 탐색기**)

2. 에서 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 디자이너의 빈 영역을 마우스 오른쪽 단추로 클릭 한 다음 **코드 보기**를 클릭 합니다.

     DataContext의 partial 클래스와 함께 코드 편집기가 열립니다.

3. DataContext의 partial 클래스 선언에 사용자 코드를 추가합니다.

## <a name="see-also"></a>관련 항목
 [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [연습: LINQ to SQL 클래스 만들기 (O-R 디자이너)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [연습: 엔터티 클래스에 유효성 검사 추가](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
