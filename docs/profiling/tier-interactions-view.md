---
title: 계층 상호 작용 뷰 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.tierinteraction
helpviewer_keywords:
- Tier Interactions view
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d188d6c3268c8ee9f066eba1b6a57e469f34a78e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778143"
---
# <a name="tier-interactions-view"></a>계층 상호 작용 뷰

상호 작용 프로파일링은 [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]을 통해 데이터베이스와 통신하는 다중 계층 애플리케이션의 함수 실행 시간에 대한 추가 정보를 제공합니다. 동기 함수 호출에 대해서만 데이터가 수집됩니다.

**요구 사항**

- Visual Studio Enterprise

상호 작용 뷰에서는 두 개의 창에 계층 상호 작용 데이터가 표시됩니다.

- 마스터 창은 계층적 트리입니다. 최상위 행에는 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 페이지 또는 프로세스의 데이터베이스 연결에 대해 집계된 데이터가 포함됩니다. 자식 노드에는 부모의 데이터베이스 연결에 대해 집계된 데이터가 포함됩니다.

- 마스터 창에서 데이터베이스 호출 노드를 클릭하면 데이터베이스 호출 인스턴스에 대한 데이터가 세부 정보 창에 표시됩니다.

  시간은 밀리초 단위의 숫자 또는 CPU 클록 틱의 횟수로 표시됩니다. 표시되는 시간 단위를 변경하려면**도구** 메뉴를 클릭하고 **옵션**을 클릭한 후에 **시간 값 표시 단위** 옵션 중 하나를 선택합니다.

## <a name="master-pane"></a>마스터 창

|열|Description|
|------------|-----------------|
|**이름**|- 최상위 행의 경우 프로파일링된 프로세스 또는 웹 페이지의 이름입니다.<br />- 데이터베이스 연결 행의 경우 데이터베이스를 호스트하는 서버의 이름입니다.|
|**Database**|데이터베이스의 이름입니다(데이터베이스 연결 행에만 해당됨).|
|**Count**|프로세스, 웹 페이지 또는 데이터베이스 연결에 의해 생성된 요청의 총 수입니다.|
|**총 경과 시간**|프로세스, 웹 페이지 또는 데이터베이스 연결에서 단일 요청을 실행하는 데 소요된 총 시간입니다.|
|**최대 경과 시간**|프로세스, 웹 페이지 또는 데이터베이스 연결에서 단일 요청을 실행하는 데 소요된 최대 시간입니다.|
|**최소 경과 시간**|프로세스, 웹 페이지 또는 데이터베이스 연결에서 단일 요청을 실행하는 데 소요된 최소 시간입니다.|
|**평균 경과 시간**|프로세스, 웹 페이지 또는 데이터베이스 연결에서 단일 요청을 실행하는 데 소요된 평균 시간입니다.|

## <a name="database-connection-details-pane"></a>데이터베이스 연결 세부 정보 창

|열|Description|
|------------|-----------------|
|**명령 텍스트**|요청의 SQL 쿼리입니다.|
|**쿼리 개수**|쿼리가 실행된 횟수입니다.|
|**총 경과 시간**|쿼리 인스턴스를 실행하는 데 소요된 총 시간입니다.|
|**최대 경과 시간**|쿼리 인스턴스 하나를 실행하는 데 소요된 최대 시간입니다.|
|**최소 경과 시간**|쿼리 인스턴스 하나를 실행하는 데 소요된 최소 시간입니다.|
|**평균 경과 시간**|쿼리 인스턴스를 실행하는 데 소요된 평균 시간입니다.|
