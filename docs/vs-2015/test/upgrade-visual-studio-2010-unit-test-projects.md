---
title: 단위 테스트 프로젝트 업그레이드
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f1502b51-d6db-4894-9fbf-4a5723e4bb1a
caps.latest.revision: 8
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 097193ea29f5f21aed09ed5ffa9f0cb331327b84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657271"
---
# <a name="upgrade-visual-studio-2010-unit-test-projects"></a>Visual Studio 2010 단위 테스트 프로젝트 업그레이드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에는 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 테스트 프로젝트에 대한 테스트 프로젝트 호환성이 포함됩니다. 예를 들어 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1에서 만든 테스트 프로젝트는 업그레이드 없이도 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]를 사용해서 열 수 있습니다. 따라서 팀에서 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 및 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]를 둘 다 사용해서 동일한 테스트 프로젝트를 진행할 수 있습니다. 자세한 내용은 [Visual Studio 2010에서 테스트 업그레이드](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)를 참조하세요.

 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에는 단위 테스트를 위해 몇 가지 변경 사항이 적용되었습니다. 이러한 변경 사항으로 인해 이전 버전의 Visual Studio와 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 사이의 호환성 문제를 이해하는 것이 중요합니다. 단위 테스트에 대한 변경 사항 중에서도 중요한 변경 사항은 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에 단위 테스트 프로젝트 템플릿을 포함해서 두 개 이상의 테스트 프로젝트 템플릿이 포함된다는 점입니다. 새로운 단위 테스트가 새로운 단위 테스트 프로젝트 템플릿에 추가되었습니다. 단위 테스트를 코딩된 UI 테스트 프로젝트 템플릿이라는 새로운 테스트 프로젝트 템플릿에 포함할 수도 있습니다. 새 테스트 프로젝트 템플릿에 대한 자세한 내용은 [이전 버전의 Visual Studio에서 테스트 업그레이드](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52)를 참조하세요. 새 단위 테스트 프로젝트에는 기본적으로 테스트 설정 파일이 더 이상 포함되지 않습니다. 테스트 설정 파일을 제외함으로써 단위 테스트의 성능이 향상되었습니다. 호환성의 경우, Visual Studio 2010을 사용해서 만든 기존 테스트 프로젝트를 계속 사용할 수 있습니다. 하지만 테스트 설정 파일이 특별히 필요한 경우가 아닌 한 성능을 위해 테스트 프로젝트와 연관된 테스트 설정 파일을 제거하는 것이 좋습니다. 예를 들어 단위 테스트가 분산 환경에서 실행되거나 특정 진단 데이터를 수집해야 할 경우에는 테스트 설정 파일을 보존하도록 선택할 수 있습니다. 새로운 단위 테스트 프로젝트 템플릿 또는 코딩된 UI 테스트 프로젝트 템플릿을 사용할 때 이와 비슷한 요구 사항이 있으면 여기에 테스트 설정 파일을 수동으로 추가할 수도 있습니다.

> [!NOTE]
> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 테스트 프로젝트에 있는 기존 단위 테스트는 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 및 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 사이에 문제 없이 작동합니다. 단위 테스트가 포함된 Visual Studio 2010 테스트 프로젝트를 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 열거나 그 반대로 할 때 테스트 프로젝트 파일은 변경되지 않습니다.

> [!CAUTION]
> Visual Studio 2010은 11.0 도구 집합을 대상으로 하는 C++/CLI 프로젝트(즉, Visual Studio 2012에서 만든 프로젝트)를 열 수 없습니다. 이러한 제한은 C++/CLI 단위 테스트 프로젝트 뿐만 아니라 모든 C++/CLI 프로젝트에 적용됩니다.

> [!NOTE]
> 명령줄에서 vstest.console.exe를 사용해서 새 단위 테스트를 실행할 수 있습니다. vstest.console.exe 사용에 대한 자세한 내용은 [VSTest.Console.exe 명령줄 옵션](https://msdn.microsoft.com/library/52e1689d-b1a8-4589-bd98-99a55acd0a11)을 참조하거나 도움말 스위치 **vstest.console.exe /?** 를 사용해서 명령을 실행합니다. MStest.exe를 사용해서 기존 단위 테스트를 계속 실행할 수 있습니다. 자세한 내용은 [MSTest를 사용하여 명령줄에서 자동화된 테스트 실행](https://msdn.microsoft.com/library/39b61ad0-0055-44b5-963f-25d8a6b51581) 및 [MSTest.exe 명령줄 옵션](https://msdn.microsoft.com/library/8813ba7f-e790-4e92-9f91-7080508a1c36)을 참조하세요.

 또 다른 중요한 변경 사항은 새로운 테스트 탐색기입니다. [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서는 테스트 뷰 창과 같이 이전 버전의 Visual Studio에서 익숙하게 사용하던 일부 테스트 창이 더 이상 사용되지 않습니다. 테스트 탐색기는 소프트웨어 개발 방법에 유닛 테스트를 포함하는 개발자 및 팀을 보다 효과적으로 지원하도록 설계되었습니다. 자세한 내용은 [테스트 탐색기를 사용 하 여 단위 테스트 실행](../test/run-unit-tests-with-test-explorer.md)을 참조 하세요.

## <a name="compatibility-issues-between-visual-studio-2010-sp1-and-visual-studio-2012"></a>Visual Studio 2010 SP1과 Visual Studio 2012 사이의 호환성 문제
 Visual Studio 2010 SP1과 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] 사이에 단위 테스트를 마이그레이션할 때는 주의해야 할 문제는 다음과 같습니다.

|단위 테스트 기능|문제|해결 방법|
|-----------------------------|-----------|--------------|
|테스트 목록(.vsmdi files)은 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 사용되지 않습니다.|더 이상 Visual Studio에서 새 테스트 목록(.vsmdi 파일)을 만들거나 테스트 목록을 실행할 수 없습니다. **팁:**  테스트 범주를 사용하면 이전 버전의 Microsoft Visual Studio에서 테스트 목록 기능을 사용할 때보다 더 유연하게 테스트를 관리할 수 있습니다. 테스트 범주에 논리 연산자를 사용하여 여러 범주의 테스트를 함께 실행할 수도 있고 여러 범주에 속한 테스트 중 실제로 실행할 테스트를 제한할 수도 있습니다. 뿐만 아니라 테스트 메서드를 만들 때 테스트 범주를 쉽게 추가할 수 있으므로 테스트 메서드를 만들고 난 후 테스트 목록을 따로 유지 관리할 필요가 없습니다. 테스트 범주를 사용 하면 테스트 목록을 유지 관리 하는 ** \<solution name> vsmdi** 파일을 체크 인 및 체크 아웃할 필요가 없습니다. 자세한 내용은 [테스트 범주를 정의하여 테스트 그룹화](https://msdn.microsoft.com/library/2c26a648-f068-4d60-99b6-b9747b7bdbc9)를 참조하세요.|-   테스트 목록을 사용하는 기존 테스트 프로젝트와의 호환성 유지를 위해, Visual Studio를 사용해서 여전히 .vsmdi 파일을 편집할 수 있습니다.<br />-   Visual Studio에서 마이그레이션된 테스트 목록을 실행할 수 없더라도 명령줄에서 mstest.exe를 사용해서 계속 실행할 수 있습니다. 자세한 내용은 [MSTest를 사용하여 명령줄에서 자동화된 테스트 실행](https://msdn.microsoft.com/library/39b61ad0-0055-44b5-963f-25d8a6b51581)을 참조하세요.<br />-   빌드 정의에서 테스트 목록을 사용 중이었다면 해당 테스트 목록을 계속 사용할 수 있습니다. 자세한 내용은 [방법: 애플리케이션을 빌드한 후 예약된 테스트 구성 및 실행](https://msdn.microsoft.com/32acfeb1-b1aa-4afb-8cfe-cc209e6183fd) 및 [빌드 프로세스에서 테스트 실행](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)을 참조하세요.|
|전용 접근자는 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 사용되지 않습니다.<br /><br /> 이전 버전의 Visual Studio에서는 Publicize를 사용해서 내부 API(애플리케이션 프로그래밍 인터페이스)를 지정하고 테스트에서 호출한 후 제품의 내부 API로 호출될 수 있는 공용 API를 만들 수 있었습니다. 그런 다음 코드 생성을 사용해서 테스트 스텁을 만들고 해당 스텁 내에서 코드 조각을 생성할 수 있었습니다.|전용 접근자는 더 이상 만들 수 없습니다.|<ul><li>Visual Studio 2010 테스트 프로젝트는 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 컴파일 및 작동됩니다. 빌드에는 출력 경고가 포함됩니다.</li><li>내부 API를 계속 테스트해야 할 경우에는 다음과 같은 옵션이 있습니다.<br /><br /> <ul><li><xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> 클래스를 사용해서 코드에서 내부 및 전용 API에 대한 액세스를 지원합니다. 이 클래스는 Microsoft.VisualStudio.QualityTools.UnitTestFramework.dll 어셈블리에 있습니다.</li><li>내부 또는 전용 API에 액세스하기 위해 코드를 반영할 수 있는 리플렉션 프레임워크를 만듭니다.</li><li>액세스하려는 코드가 내부 코드인 경우 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>를 사용해서 API에 액세스할 수 있으므로 테스트 코드가 내부 API에 액세스할 수 있습니다.</li></ul></li></ul>|
|테스트 영향 제거|||
|테스트 탐색기에서 TRX 로그를 통해 실행 결과를 공유합니다.||TRX 로그는 명령줄 및 팀 빌드에서 가져올 수 있습니다.|

## <a name="see-also"></a>관련 항목
 [Visual Studio 프로젝트 포팅, 마이그레이션 및 업그레이드](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [코드 테스트 코드 테스트](../test/unit-test-your-code.md) [이전 버전의 Visual Studio에서 테스트 업그레이드](https://msdn.microsoft.com/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) [Visual studio 2010에서 코딩 된 UI 테스트 업그레이드](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)