---
title: '방법: 저장 프로시저 및 함수에 매핑된 DataContext 메서드 만들기 (O-R 디자이너) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70053b74a4dd2ad569e1e8195f4c9b2e7b214440
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665976"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>방법: 저장 프로시저 및 함수에 매핑된 DataContext 메서드 만들기(O/R 디자이너)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

저장 프로시저 및 함수를에 메서드로 추가할 수 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 있습니다 <xref:System.Data.Linq.DataContext> . 메서드를 호출하여 필요한 매개 변수에 전달하면 데이터베이스의 저장 프로시저 또는 함수가 실행되어 <xref:System.Data.Linq.DataContext> 메서드의 반환 형식으로 데이터를 반환합니다. 메서드에 대 한 자세한 내용은 <xref:System.Data.Linq.DataContext> [DataContext 메서드 (O/R 디자이너)](../data-tools/datacontext-methods-o-r-designer.md)를 참조 하세요.

> [!NOTE]
> 또한 변경 내용을 엔터티 클래스에서 데이터베이스로 저장한 경우 저장 프로시저를 사용하여 삽입, 업데이트 및 삭제를 수행하는 기본 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 런타임 동작을 재정의할 수 있습니다. 자세한 내용은 [방법: 저장 프로시저를 할당 하 여 업데이트, 삽입 및 삭제 수행 (O/R 디자이너)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)을 참조 하세요.

## <a name="creating-datacontext-methods"></a>DataContext 메서드 만들기
 <xref:System.Data.Linq.DataContext> **서버 탐색기/데이터베이스 탐색기** 에서 저장 프로시저 또는 함수를로 끌어 메서드를 만들 수 있습니다 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

> [!NOTE]
> 생성된 <xref:System.Data.Linq.DataContext> 메서드의 반환 형식은 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]에서 저장 프로시저 또는 함수를 드롭하는 위치에 따라 달라집니다. drop항목을 기존 엔터티 클래스에 직접 드롭하면 엔터티 클래스의 반환 형식을 갖는 <xref:System.Data.Linq.DataContext> 메서드가 만들어집니다. 항목을 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]의 빈 영역에 놓으면 자동으로 생성된 형식을 반환하는 <xref:System.Data.Linq.DataContext> 메서드가 만들어집니다. <xref:System.Data.Linq.DataContext>메서드 창에 추가한 후 메서드의 반환 형식을 변경할 수 있습니다. <xref:System.Data.Linq.DataContext> 메서드의 반환 형식을 검사하거나 변경하려면 해당 메서드를 선택하고 **속성** 창에서 **반환 형식** 속성을 검사합니다. 자세한 내용은 [방법: DataContext 메서드의 반환 형식 변경 (O/R 디자이너)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)을 참조 하세요.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>자동으로 생성된 형식을 반환하는 DataContext 메서드를 만들려면

1. **서버 탐색기** / **데이터베이스 탐색기**에서 작업 중인 데이터베이스의 **저장 프로시저** 노드를 확장 합니다.

2. 원하는 저장 프로시저를 찾아 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]의 빈 영역으로 끌어 옵니다.

     자동으로 생성된 반환 형식을 갖는 <xref:System.Data.Linq.DataContext> 메서드가 만들어지고 **메서드** 창에 나타납니다.

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>엔터티 클래스의 반환 형식을 갖는 DataContext 메서드를 만들려면

1. **서버 탐색기** / **데이터베이스 탐색기**에서 작업 중인 데이터베이스의 **저장 프로시저** 노드를 확장 합니다.

2. 원하는 저장 프로시저를 찾아 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]의 기존 엔터티 클래스로 끌어 옵니다.

     선택한 엔터티 클래스의 반환 형식을 갖는 <xref:System.Data.Linq.DataContext> 메서드가 만들어지고 **메서드** 창에 나타납니다.

> [!NOTE]
> 기존 반환 형식을 변경 하는 방법은 <xref:System.Data.Linq.DataContext> 메서드 참조 [방법: DataContext 메서드의 반환 형식 변경(O/R 디자이너)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>관련 항목
 [Visual Studio DataContext 메서드의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [(o/r 디자이너)](../data-tools/datacontext-methods-o-r-designer.md) [연습: LINQ to SQL 클래스 만들기 (o-r 디자이너)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Linq 소개 Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984) [방법: c #에서 linq 쿼리 작성](https://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)
