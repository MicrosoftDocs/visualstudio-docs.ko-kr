---
title: '방법: 복수화 설정 및 해제 (O-R 디자이너) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: afe8c8a4429efb83c09d80a5dd00dfe08b0d63e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665942"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>방법: 복수형 설정 및 해제(O/R 디자이너)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

기본적으로 **서버 탐색기**데이터베이스 탐색기에서 이름이 인 데이터베이스 개체를 / **Database Explorer** [Visual Studio의 LINQ to SQL 도구로](../data-tools/linq-to-sql-tools-in-visual-studio2.md)끌면 생성 된 엔터티 클래스의 이름이 복수형에서 단일로 변경 됩니다. 이렇게 하면 인스턴스화된 엔터티 클래스를 데이터의 단일 레코드에 매핑하는 것을 보다 정확하게 나타낼 수 있습니다. 예를 들어 Customers 테이블을 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]에 추가하면 단일 고객에 대한 데이터만 해당 클래스에 보유되므로 Customer라는 엔터티 클래스가 만들어집니다.

> [!NOTE]
> 복수 적용은 기본적으로 Visual Studio 영어 버전에만 적용됩니다.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>복수 적용을 설정 및 해제하려면

1. **도구** 메뉴에서 **옵션**을 클릭합니다.

2. **옵션** 대화 상자에서 **데이터베이스 도구**를 확장합니다.

> [!NOTE]
> **데이터베이스 도구** 노드가 표시되지 않은 경우에는 **모든 설정 표시**를 선택합니다.

1. **O/R 디자이너**를 클릭합니다.

2. **이름 복수화** 를 **사용**  =  **False** 로 설정 하 여 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 클래스 이름을 변경 하지 않도록 설정 합니다.

3. **이름 복수화** 를 **사용**True로 설정 하 여에  =  **True** 추가 된 개체의 클래스 이름에 복수화 규칙을 적용 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 합니다.

## <a name="see-also"></a>관련 항목
 Visual [studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [visual studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
