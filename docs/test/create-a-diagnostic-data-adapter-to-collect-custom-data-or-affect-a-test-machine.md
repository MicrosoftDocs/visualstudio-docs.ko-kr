---
title: 테스트용 진단 데이터 어댑터 만들기
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2eadce12890e483f1b1c7aafccb61d9a6ee28e3a
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880301"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>진단 데이터 어댑터를 만들어 사용자 지정 데이터를 수집하거나 테스트 머신에 영향 주기

테스트를 실행할 때 진단 데이터 어댑터를 직접 만들어 데이터를 수집하거나, 테스트의 일부로 컴퓨터에 영향을 줄 수 있습니다. 예를 들어, 테스트 중인 애플리케이션에서 만든 로그 파일을 수집하고 테스트 결과에 연결하거나 컴퓨터에 남아 있는 디스크 공간이 제한적인 상황에서 테스트를 실행할 수 있습니다. Visual Studio Enterprise에서 제공하는 API를 사용하여 테스트 실행의 특정 지점에서 작업을 수행하는 코드를 작성할 수 있습니다. 예를 들어 테스트 실행을 시작할 때, 각 개별 테스트가 완료되기 전후, 그리고 테스트 실행이 완료될 때 작업을 수행할 수 있습니다.

::: moniker range="vs-2017"
구성 설정 파일을 사용하여 사용자 지정 진단 데이터 어댑터에 대한 기본 입력을 제공할 수 있습니다. 예를 들어 수집한 후 테스트 결과에 첨부할 파일의 위치 또는 시스템에 남겨 둘 디스크 공간에 대한 정보를 제공할 수 있습니다. 이 데이터는 만드는 각 테스트 설정에 대해 구성할 수 있습니다. Microsoft Test Manager에서 제공된 기본 편집기를 사용하여 이 데이터를 표시하고 편집하거나 편집기로 사용할 자체 사용자 정의 컨트롤을 만들 수 있습니다. 편집기에서 어댑터 구성에 대해 변경한 모든 내용은 테스트 설정과 함께 저장됩니다.
::: moniker-end

::: moniker range=">=vs-2019"
구성 설정 파일을 사용하여 사용자 지정 진단 데이터 어댑터에 대한 기본 입력을 제공할 수 있습니다. 예를 들어 수집한 후 테스트 결과에 첨부할 파일의 위치 또는 시스템에 남겨 둘 디스크 공간에 대한 정보를 제공할 수 있습니다. 이 데이터는 만드는 각 테스트 설정에 대해 구성할 수 있습니다. 편집기로 사용할 고유한 사용자 정의 컨트롤을 만들 수 있습니다. 편집기에서 어댑터 구성에 대해 변경한 모든 내용은 테스트 설정과 함께 저장됩니다.
::: moniker-end

Visual Studio에서 테스트를 실행하는 경우 이러한 테스트 설정을 활성으로 설정해야 합니다. 테스트 설정에 대한 자세한 내용은 [테스트 설정을 사용하여 진단 정보 수집](../test/collect-diagnostic-information-using-test-settings.md)을 참조하세요.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>작업

진단 데이터 어댑터를 만드는 데 도움이 되는 항목은 다음과 같습니다.

|작업|관련 항목|
|-|-----------------------|
|**진단 데이터 어댑터 만들기:** 클래스 라이브러리를 만들어 진단 데이터 어댑터를 만든 다음, 진단 데이터 어댑터 API를 사용하여 원하는 정보를 수집하거나 테스트를 실행하는 데 사용하는 테스트 시스템에 영향을 줄 수 있습니다.|-   [방법: 진단 데이터 어댑터 만들기](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**테스트 실행 시 사용할 사용자 지정 진단 데이터 어댑터 선택:** 테스트를 실행할 때 어댑터를 사용할 수 있도록 테스트 설정에 사용할 진단 데이터 어댑터를 선택할 수 있습니다.|-   [테스트하는 동안 진단 데이터 수집(Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)<br />-   [수동 테스트에서 진단 데이터 수집(Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|

## <a name="see-also"></a>참조

- [테스트 설정을 사용하여 진단 정보 수집](../test/collect-diagnostic-information-using-test-settings.md)
