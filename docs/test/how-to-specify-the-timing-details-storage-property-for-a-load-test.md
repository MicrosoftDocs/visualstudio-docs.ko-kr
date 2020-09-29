---
title: 타이밍 정보 스토리지 속성(부하 테스트 실행 설정)
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 867a9c21-0909-4963-bc02-d41e9393008c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 132c55b4cd6f716d8983358064f749eabeb9ba88
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810564"
---
# <a name="how-to-specify-the-timing-details-storage-property-for-a-load-test-run-setting"></a>방법: 부하 테스트 실행 설정에 대한 타이밍 정보 스토리지 속성 지정

**부하 테스트 새로 만들기 마법사**를 사용하여 부하 테스트를 만든 다음, **부하 테스트 편집기**를 사용하여 테스트 요구 사항 및 목표에 맞게 설정을 변경할 수 있습니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**속성** 창에서 실행 설정의 **타이밍 정보 스토리지** 속성 값을 편집할 수 있습니다. **타이밍 정보 스토리지** 속성은 다음 옵션 중 하나로 설정할 수 있습니다.

- **모든 개인 정보:** 테스트 중에 생성된 각 테스트, 트랜잭션 및 페이지에 대한 개별 타이밍 데이터를 수집하여 저장합니다.

  > [!NOTE]
  > 부하 테스트 결과에서 가상 사용자 데이터 정보를 사용하려면 **모든 개인 정보** 옵션을 선택해야 합니다. 자세한 내용은 [세부 정보 뷰에서 가상 사용자 동작 분석](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)을 참조하세요.

- **없음:** 개별 타이밍 정보를 수집하지 않습니다. 그러나 이 경우에도 평균값은 사용할 수 있습니다.

- **통계만:** 개별 타이밍 데이터를 백분위수 데이터로만 저장합니다. 따라서 공간 리소스가 절약됩니다.

  **타이밍 정보 스토리지 속성에 대한 고려 사항**

  **타이밍 정보 스토리지** 속성을 사용하면 부하 테스트 도중 개별 테스트, 트랜잭션 및 페이지를 실행하는 데 각각 걸리는 시간이 부하 테스트 결과 리포지토리에 저장됩니다. 그러면 **부하 테스트 분석기**의 **테스트**, **트랜잭션** 및 **페이지** 테이블에 90번째 및 95번째 백분위수 데이터가 표시됩니다.

  **타이밍 정보 스토리지** 속성을 사용할 경우 해당 값을 **StatisticsOnly** 또는 **AllIndividualDetails**로 설정하면 모든 개별 테스트, 페이지 및 트랜잭션의 시간이 측정되고 개별 타이밍 데이터에서 백분위수 데이터가 계산됩니다. 하지만 **StatisticsOnly** 옵션을 선택하면 백분위수 데이터가 계산된 후 리포지토리에서 개별 타이밍 데이터가 삭제된다는 차이점이 있습니다. 그러면 타이밍 정보가 사용될 때 리포지토리에 필요한 공간이 감소합니다. 그러나 SQL 도구를 사용하여 다른 방법으로 타이밍 정보 데이터를 처리하기를 원할 수도 있습니다. 이 경우에는 타이밍 정보 데이터를 해당 처리에 사용할 수 있도록 **AllIndividualDetails** 옵션을 사용해야 합니다. 또한 속성을 **AllIndividualDetails**로 설정하면 부하 테스트 실행이 완료된 후에 **부하 테스트 분석기**의 **가상 사용자 작업 차트**를 사용하여 가상 사용자 작업을 분석할 수 있습니다. 자세한 내용은 [세부 정보 뷰에서 가상 사용자 동작 분석](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)을 참조하세요.

  특히 부하 테스트가 긴 경우 부하 테스트 결과 리포지토리에서 타이밍 정보 데이터를 저장하는 데 필요한 공간이 매우 클 수 있습니다. 또한, 이 데이터는 부하 테스트 실행이 완료되어 데이터를 리포지토리에 저장할 시점이 될 때까지 부하 테스트 에이전트에 저장되므로 부하 테스트가 끝날 때 부하 테스트 결과 리포지토리에 이 데이터를 저장하는 시간이 오래 걸립니다. **타이밍 정보 스토리지** 속성은 기본적으로 사용됩니다. 이것이 문제가 되는 테스트 환경의 경우 **타이밍 정보 스토리지**를 **없음**으로 설정할 수도 있습니다.

  타이밍 정보 데이터는 테스트 실행 중에 *LoadTestItemResults.dat* 파일에 저장되며, 부하 테스트가 완료된 후에는 컨트롤러로 보내집니다. 오랜 시간 동안 실행되는 부하 테스트의 경우에는 파일 크기가 큽니다. 따라서 에이전트 컴퓨터에 디스크 공간이 충분하지 않으면 문제가 발생합니다.

  이전 버전의 Visual Studio 부하 테스트에서 프로젝트를 업그레이드할 경우 다음 절차를 수행하여 전체 정보 수집을 사용하도록 설정합니다.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>부하 테스트에서 타이밍 정보 스토리지 속성을 구성하려면

1. 부하 테스트 편집기에서 부하 테스트를 엽니다.

2. 부하 테스트에서 **실행 설정** 노드를 확장합니다.

3. 구성할 실행 설정(예: **Run Settings1[Active]** )을 선택합니다.

4. **속성** 창을 엽니다. **보기** 메뉴에서 **속성 창**을 선택합니다.

5. **결과** 범주에서 **타이밍 정보 스토리지** 속성을 선택하고 **모든 개인 정보**를 선택합니다.

     **타이밍 정보 스토리지** 속성에 대해 **모든 개인 정보** 설정을 구성하면 부하 테스트를 실행하고 **가상 사용자 작업 차트**를 볼 수 있습니다. 자세한 내용은 [방법: 부하 테스트 중에 가상 사용자가 수행하는 작업 분석](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [세부 정보 뷰에서 가상 사용자 동작 분석](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [연습: 가상 사용자 작업 차트를 사용하여 문제 격리](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)
