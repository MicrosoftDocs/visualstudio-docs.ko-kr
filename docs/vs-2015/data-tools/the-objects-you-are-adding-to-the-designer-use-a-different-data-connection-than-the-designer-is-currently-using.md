---
title: 디자이너에 추가 하려는 개체가 디자이너에서 현재 사용 하 고 있는 것과 다른 데이터 연결을 사용 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9ec76446aff930475ea5e3ca0133e11b3798b0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672299"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>디자이너에 추가하려는 개체가 현재 디자이너가 사용 중인 것과 다른 데이터 연결을 사용합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

디자이너에 추가하려는 개체가 디자이너에서 현재 사용 중인 데이터 연결이 아닌 다른 데이터 연결을 사용합니다. 디자이너에서 사용 중인 연결을 바꾸시겠습니까?

 ()에 항목을 추가 하는 경우 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 모든 항목은 하나의 공유 데이터 연결을 사용 합니다. 디자인 화면은 <xref:System.Data.Linq.DataContext> 표면의 모든 개체에 대해 단일 연결을 사용 하는를 나타냅니다. 디자이너에서 현재 사용 중인 데이터 연결과 다른 데이터 연결을 사용 하는 디자이너에 개체를 추가 하는 경우이 메시지가 나타납니다. 이 오류를 해결하려면 기존 연결 유지를 선택하세요. 이 항목을 선택하면 선택한 개체가 추가되지 않습니다. 또는 개체 추가를 선택하고 <xref:System.Data.Linq.DataContext> 연결을 새 연결로 다시 설정할 수 있습니다.

> [!NOTE]
> **예**를 클릭 하면의 모든 엔터티 클래스가 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] 새 연결에 매핑됩니다.

### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>기존 연결을 선택한 개체에서 사용하는 연결로 대체하려면

- **예**를 클릭합니다.

     선택한 개체가 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]에 추가되고 DataContext.Connection이 새 연결로 설정됩니다.

### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>기존 연결을 계속 사용하고 선택한 개체 추가를 취소하려면

- **아니요**를 클릭합니다.

     작업이 취소됩니다. DataContext.Connection이 기존 연결로 설정됩니다.

## <a name="see-also"></a>관련 항목
 [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)