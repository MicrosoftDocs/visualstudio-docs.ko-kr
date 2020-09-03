---
title: 디자이너에 추가 된 개체는 다른 데이터 연결을 사용 합니다.
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 38fa361536f9e99c013f9a13330fe1a68e53641a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281411"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer"></a>디자이너에 추가 하려는 개체가 디자이너와 다른 데이터 연결을 사용 합니다.

디자이너에 추가하려는 개체가 디자이너에서 현재 사용 중인 데이터 연결이 아닌 다른 데이터 연결을 사용합니다. 디자이너에서 사용 중인 연결을 바꾸시겠습니까?

**개체 관계형 디자이너** (**O/R 디자이너**)에 항목을 추가 하는 경우 모든 항목은 하나의 공유 데이터 연결을 사용 합니다. 디자인 화면은 <xref:System.Data.Linq.DataContext> 표면의 모든 개체에 대해 단일 연결을 사용 하는를 나타냅니다. 디자이너에서 현재 사용 중인 데이터 연결과 다른 데이터 연결을 사용 하는 디자이너에 개체를 추가 하는 경우이 메시지가 나타납니다. 이 오류를 해결하려면 기존 연결 유지를 선택하세요. 이 항목을 선택하면 선택한 개체가 추가되지 않습니다. 또는 개체 추가를 선택하고 <xref:System.Data.Linq.DataContext> 연결을 새 연결로 다시 설정할 수 있습니다.

## <a name="connection-options"></a>연결 옵션

- 기존 연결을 선택한 개체에서 사용 하는 연결로 바꾸려면 **예**를 클릭 합니다.

   선택한 개체는 **O/R 디자이너**에 추가 되 고 *DataContext. 연결은* 새 연결로 설정 됩니다.

   > [!NOTE]
   > **예**를 클릭 하면 **O/R 디자이너** 의 모든 엔터티 클래스가 새 연결에 매핑됩니다.

- 기존 연결을 계속 사용 하 고 선택한 개체의 추가를 취소 하려면 **아니요**를 클릭 합니다.

   작업이 취소됩니다. *DataContext.Connection*이 기존 연결로 설정되어 있습니다.

## <a name="see-also"></a>추가 정보

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
