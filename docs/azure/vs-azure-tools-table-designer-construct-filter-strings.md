---
title: 테이블 디자이너에 대한 필터 문자열 생성하기 | Microsoft Docs
description: 테이블 디자이너에 대한 필터 문자열 생성하기
author: ghogen
manager: jillfra
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: 13ca51a6c7b505605409cbb6bb2f17e618c45179
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72911652"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>테이블 디자이너에 대한 필터 문자열 생성하기
## <a name="overview"></a>개요
Visual Studio **테이블 디자이너**에 표시된 Azure 테이블에서 데이터를 필터링하려면 필터 문자열을 생성하고 필터 필드에 입력합니다. 필터 문자열 구문은 WCF Data Services에 의해 정의되며 SQL WHERE 절과 유사하지만 HTTP 요청을 통해 Table service에 전송됩니다. **테이블 디자이너** 는 적절한 인코딩을 처리하므로 원하는 속성 값을 필터링하려면 단순히 속성 이름, 비교 연산자, 조건 값 및 필요에 따라 부울 연산자를 필터 필드에 입력하면 됩니다. [Storage 서비스 REST API 참조](/rest/api/storageservices/)를 통해 테이블 쿼리에 대한 URL을 생성하는 경우 $filter 쿼리 옵션은 포함할 필요가 없습니다.

WCF Data Services는 [개방형 데이터 프로토콜](https://www.odata.org/) (OData)에 기반을 둡니다. 필터 시스템 쿼리 옵션 (**$filter**)에 대한 자세한 내용은 [OData URI 규칙 사양](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)을 참조하세요.

## <a name="comparison-operators"></a>비교 연산자
다음의 논리 연산자는 모든 속성 유형에 대해 지원됩니다.

| 논리 연산자 | 설명 | 필터 문자열의 예 |
| --- | --- | --- |
| eq |같음 |'Redmond'와 같은 도시 |
| gt |보다 큼 |20보다 큰 가격 |
| ge |보다 크거나 같음 |10보다 크거나 같은 가격 |
| lt |보다 작음 |20보다 적은 가격 |
| le |작거나 같음 |100보다 적거나 같은 가격 |
| ne |같지 않음 |'London'과 같지 않은 도시 |
| 및 |and |200보다 적거나 같은 가격 및 3.5보다 큰 가격 |
| 또는 |또는 |3.5보다 적거나 같은 가격 또는 200보다 큰 가격 |
| not |Not |not isAvailable |

필터 문자열을 생성할 때 다음의 규칙이 중요합니다.

* 논리 연산자를 사용하여 속성 값을 비교합니다. 참고로 동적 값에 속성을 비교할 수 있으며 식의 한쪽은 상수여야 합니다.
* 필터 문자열의 모든 부분은 대/소문자를 구분합니다.
* 상수 값은 유효한 결과를 반환하는 필터에 대한 속성과 동일한 데이터 형식이어야 합니다. 속성 형식에 대한 자세한 내용은 [테이블 서비스 데이터 모델 이해](/rest/api/storageservices/Understanding-the-Table-Service-Data-Model)를 참조하세요.

## <a name="filtering-on-string-properties"></a>문자열 속성 필터링
문자열 속성으로 필터링하는 경우 문자열 상수를 작은따옴표로 묶습니다.

다음의 예제는 **PartitionKey** 및 **RowKey** 속성으로 필터링하며, 추가적으로 키가 아닌 속성도 필터 문자열에 추가될 수 있습니다.

```
PartitionKey eq 'Partition1' and RowKey eq '00001'
```

필수는 아니지만 각 필터 식을 괄호로 묶을 수 있습니다.

```
(PartitionKey eq 'Partition1') and (RowKey eq '00001')
```

참고로 Table service는 와일드카드 쿼리를 지원하지 않으며 테이블 디자이너에서도 지원되지 않습니다. 그러나 원하는 접두사에서 비교 연산자를 사용하여 접두사를 일치시킬 수 있습니다. 다음의 예제는 문자 ‘A’로 시작하는 LastName 속성을 가진 엔터티를 반환합니다.

```
LastName ge 'A' and LastName lt 'B'
```

## <a name="filtering-on-numeric-properties"></a>숫자 속성 필터링
정수 또는 부동 소수점 숫자를 필터링하려면 따옴표 없이 숫자를 지정합니다.

이 예제는 값이 30보다 큰 Age 속성을 가진 모든 엔터티를 반환합니다.

```
Age gt 30
```

이 예제는 값이 100.25보다 작거나 같은 AmountDue 속성을 가진 모든 엔터티를 반환합니다.

```
AmountDue le 100.25
```

## <a name="filtering-on-boolean-properties"></a>부울 속성 필터링
부울 값을 필터링하려면 **true** 또는 **false** 를 인용 부호 없이 지정합니다.

다음의 예제는 IsActive 속성이 **true**로 설정된 모든 엔터티를 반환합니다.

```
IsActive eq true
```

논리 연산자 없이도 이 필터 식을 작성할 수도 있습니다. 다음의 예제에서는 Table service가 IsActive 속성이 **true**인 모든 엔터티를 반환합니다.

```
IsActive
```

IsActive가 false인 모든 엔터티를 반환하려면 not 연산자를 사용할 수 있습니다.

```
not IsActive
```

## <a name="filtering-on-datetime-properties"></a>DateTime 속성 필터링
DateTime 값을 필터링하려면 **datetime** 키워드를 지정하고 그 뒤에 날짜/시간 상수를 작은따옴표 안에 입력합니다. 날짜/시간 상수는 [DateTime 속성 값 형식 지정](/rest/api/storageservices/Formatting-DateTime-Property-Values)에 설명된 것처럼 결합된 UTC 형식이어야 합니다.

다음 예제는 CustomerSince 속성이 2008년 7월 10일과 같은 경우 엔터티를 반환합니다.

```
CustomerSince eq datetime'2008-07-10T00:00:00Z'
```
