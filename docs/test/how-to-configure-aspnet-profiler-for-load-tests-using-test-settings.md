---
title: 부하 테스트에 대한 ASP.NET 프로파일러 구성
ms.date: 10/13/2016
ms.topic: conceptual
helpviewer_keywords:
- test settings, ASP.NET
ms.assetid: 6832fe39-04d5-4d94-8a18-3e2730bad423
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 07df32104394dffcd61d1561309b77e61593f6e6
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880236"
---
# <a name="how-to-configure-aspnet-profiler-for-load-tests-using-test-settings-in-visual-studio"></a>방법: Visual Studio에서 테스트 설정을 사용하여 부하 테스트에 대한 ASP.NET 프로파일러 구성

ASP.NET 프로파일러 진단 데이터 어댑터를 사용하여 ASP.NET 프로파일러 정보를 수집할 수 있습니다. 이 진단 데이터 어댑터는 ASP.NET 애플리케이션에 대한 성능 데이터를 수집합니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Microsoft Test Manager(Visual Studio 2017에서 더 이상 사용되지 않음)를 사용하여 실행되는 테스트에는 이 진단 데이터 어댑터를 사용할 수 없습니다. ASP.NET 프로파일러 진단 데이터 어댑터는 Visual Studio Enterprise가 필요한 웹 사이트를 사용하는 부하 테스트에만 사용할 수 있습니다.

ASP.NET 프로파일러 진단 데이터 어댑터를 사용하여 부하 테스트를 실행할 때 애플리케이션 계층에서 ASP.NET 프로파일러 데이터를 수집할 수 있습니다. 실행 시간이 1시간 이상인 부하 테스트와 같이 오랜 시간이 걸리는 부하 테스트의 경우에는 이 프로파일러를 실행하면 안 됩니다. 프로파일러 파일이 수백 메가바이트까지 커질 수 있기 때문입니다. 대신 보다 짧은 부하 테스트에 ASP.NET 프로파일러를 사용해도 성능 문제를 깊이 있게 진단할 수 있습니다.

> [!NOTE]
> ASP.NET 프로파일러 진단 데이터 어댑터에서는 IIS(Internet Information Services) 프로세스를 프로파일링합니다. 따라서 개발 웹 서버에서는 이 진단 데이터 어댑터가 작동하지 않습니다. 부하 테스트에서 웹 사이트를 프로파일링하려면 IIS가 실행 중인 컴퓨터에 테스트 에이전트를 설치해야 합니다. 이 테스트 에이전트는 부하를 생성하지 않으며, 수집만을 위한 에이전트가 됩니다. 자세한 내용은 [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)을 참조하세요.

자세한 내용은 [방법: 분산 부하 테스트를 위한 테스트 설정 만들기](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)를 참조하세요.

## <a name="configure-the-aspnet-profiler-for-your-test-settings"></a>테스트 설정에 대한 ASP.NET 프로파일러 구성

이 절차의 단계를 수행하려면 먼저 Visual Studio에서 테스트 설정을 연 다음, **데이터 및 진단** 페이지를 선택해야 합니다.

1. ASP.NET 프로파일러 데이터를 수집하는 데 사용할 역할을 선택합니다.

    > [!WARNING]
    > 이 역할은 웹 서버여야 합니다.

2. **ASP.NET 프로파일러**를 선택하여 ASP.NET 프로파일링 데이터 수집을 활성화한 다음, **구성**을 선택합니다.

     ASP.NET 프로파일링 데이터 컬렉션을 구성하는 데 사용할 대화 상자가 나타납니다.

3. **프로파일러 샘플링 간격**에 각 ASP.NET 프로파일링 샘플을 수집하기 전에 대기할 중단되지 않은 CPU 클록 주기 수를 나타내는 값을 입력합니다.

4. 계층 상호 작용 프로파일링을 사용하려면 **계층 상호 작용 프로파일링 사용**을 선택합니다.

     계층 상호 작용 프로파일링에서는 각 아티팩트(예: *MyPage.aspx* 또는 *CompanyLogo.gif*)에 대해 웹 서버로 전송되는 요청 수와 각 요청을 처리하는 데 걸린 시간을 계산합니다. 또한 계층 상호 작용 프로파일링에서는 페이지 요청의 일부로 사용된 ADO.NET 연결과 해당 요청을 처리할 때 실행된 쿼리 및 저장 프로시저 호출 수를 수집합니다.

     다음과 같은 두 가지 타이밍 정보 집합이 수집됩니다.

    - 각 웹 요청을 처리하는 데 관련된 타이밍 정보(최소값, 최대값, 평균 및 합계)

    - 각 쿼리를 실행하는 데 관련된 타이밍 정보(최소값, 최대값, 평균 및 합계)

이제 테스트 설정에 구성된 ASP.NET 프로파일러 진단 데이터 어댑터를 사용하여 ASP.NET 웹 애플리케이션에 대한 ASP.NET 프로파일링 데이터를 수집할 수 있습니다.

## <a name="see-also"></a>참조

- [테스트 설정을 사용하여 진단 정보 수집](../test/collect-diagnostic-information-using-test-settings.md)
- [방법: 분산 부하 테스트를 위한 테스트 설정 만들기](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [테스트 컨트롤러 및 테스트 에이전트](configure-test-agents-and-controllers-for-load-tests.md)