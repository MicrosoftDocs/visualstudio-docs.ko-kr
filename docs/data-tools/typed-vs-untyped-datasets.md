---
title: 형식화된 데이터 세트 및 형식화되지 않은 데이터 세트
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 430e57713f1bfb01219ea1ac8123f321ba0f5680
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586109"
---
# <a name="typed-vs-untyped-datasets"></a>형식화된 데이터 세트 및 형식화되지 않은 데이터 세트
형식화 된 데이터 집합은 기본 클래스에서 처음 파생 된 데이터 집합이 며 <xref:System.Data.DataSet> .xsd 파일에 저장 된 **데이터 세트 디자이너**의 정보를 사용 하 여 강력한 형식의 새 데이터 집합 클래스를 생성 합니다. 스키마의 정보 (테이블, 열 등)가 생성 되 고 새 데이터 집합 클래스에 일련의 첫 번째 클래스 개체 및 속성으로 컴파일됩니다. 형식화 된 데이터 집합은 기본 클래스에서 상속 되므로 <xref:System.Data.DataSet> 형식화 된 클래스는 클래스의 모든 기능을 가정 <xref:System.Data.DataSet> 하 고 클래스의 인스턴스를 매개 변수로 사용 하는 메서드와 함께 사용할 수 있습니다 <xref:System.Data.DataSet> .

이와 달리 형식화 되지 않은 데이터 집합에는 해당 하는 기본 제공 스키마가 없습니다. 형식화 된 데이터 집합에서와 마찬가지로 형식화 되지 않은 데이터 집합은 테이블, 열 등을 포함 하지만 컬렉션 으로만 표시 됩니다. 그러나 형식화 되지 않은 데이터 집합에서 수동으로 테이블 및 기타 데이터 요소를 만든 후에는 데이터 집합의 메서드를 사용 하 여 데이터 집합의 구조를 스키마로 내보낼 수 있습니다 <xref:System.Data.DataSet.WriteXmlSchema%2A> .

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>형식화 된 데이터 집합 및 형식화 되지 않은 데이터 집합의 데이터 액세스 대비
형식화 된 데이터 집합에 대 한 클래스에는 테이블 및 열의 실제 이름을 사용 하는 개체 모델이 있습니다. 예를 들어 형식화 된 데이터 집합을 사용 하 여 작업 하는 경우 다음과 같은 코드를 사용 하 여 열을 참조할 수 있습니다.

[!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
[!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

이와 대조적으로 형식화 되지 않은 데이터 집합을 사용 하 여 작업 하는 경우 해당 코드는 다음과 같습니다.

[!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
[!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

형식화 된 액세스는 더 쉽게 읽을 수 있을 뿐만 아니라 Visual Studio **코드 편집기**에서 IntelliSense에 의해 완전히 지원 됩니다. 형식화 된 데이터 집합에 대 한 구문을 사용 하 여 보다 쉽게 작업할 수 있을 뿐만 아니라 컴파일 시간에 형식 검사를 제공 하므로 데이터 집합 멤버에 값을 할당할 때 오류가 발생할 가능성을 크게 줄일 수 있습니다. 클래스에서 열 이름을 변경한 <xref:System.Data.DataSet> 다음 응용 프로그램을 컴파일하면 빌드 오류가 발생 합니다. **작업 목록**에서 빌드 오류를 두 번 클릭 하면 이전 열 이름을 참조 하는 코드 줄로 바로 이동할 수 있습니다. 런타임에는 컬렉션이 아니라 컴파일 타임에 액세스를 결정 하기 때문에 형식화 된 데이터 집합의 테이블 및 열에 대 한 액세스도 약간 더 빠릅니다.

형식화 된 데이터 집합에는 많은 이점이 있지만 형식화 되지 않은 데이터 집합은 다양 한 상황에서 유용 합니다. 가장 명백한 시나리오는 데이터 집합에 사용할 수 있는 스키마가 없는 경우입니다. 이는 예를 들어 응용 프로그램이 데이터 집합을 반환 하는 구성 요소와 상호 작용 하지만 해당 구조를 미리 알 수 없는 경우에 발생할 수 있습니다. 마찬가지로 정적이 고 예측 가능한 구조가 없는 데이터로 작업 하는 경우도 있습니다. 이 경우 형식화 된 데이터 집합을 사용 하는 것은 적합 하지 않습니다. 데이터 구조를 변경 하 여 형식화 된 데이터 집합 클래스를 다시 생성 해야 하기 때문입니다.

더 일반적으로 스키마를 사용할 수 없는 상태에서 데이터 집합을 동적으로 만들 수 있는 경우가 많습니다. 이 경우 데이터를 관계형 방식으로 표현할 수 있는 경우 데이터 집합은 정보를 유지할 수 있는 편리한 구조입니다. 동시에 다른 프로세스에 전달할 정보를 직렬화 하거나 XML 파일을 작성 하는 기능과 같은 데이터 집합의 기능을 활용할 수 있습니다.

## <a name="see-also"></a>추가 정보

- [데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)
