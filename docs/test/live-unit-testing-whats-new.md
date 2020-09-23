---
title: Visual Studio 2017 Live Unit Testing의 새로운 기능
titleSuffix: ''
ms.date: 10/11/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
- Live Unit Testing What's New
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: cc6a7a25ebd2f7d07dcb887952b82bda34aaad35
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851465"
---
# <a name="whats-new-in-live-unit-testing-for-visual-studio-2017"></a>Visual Studio 2017 Live Unit Testing의 새로운 기능

이 항목에서는 Visual Studio 2017 버전 15.3부터 시작하는 Visual Studio의 각 버전에서 Live Unit Testing에 추가된 새 기능을 나열합니다. Live Unit Testing을 사용하는 방법의 개요는 [Visual Studio를 사용한 Live Unit Testing](live-unit-testing.md)을 참조하세요.

## <a name="version-154"></a>버전 15.4

Visual Studio 2017 버전 15.4부터 시작하는 Live Unit Testing은 다양한 영역에서 개선 사항 및 향상된 기능을 포함합니다.

- **향상된 검색 기능** Live Unit Testing이 존재하는지 알지 못하는 사용자의 경우 Visual Studio IDE는 사용자가 단위 테스트를 포함하지만 Live Unit Testing이 활성화되지 솔루션을 열 때마다 Live Unit Testing을 언급하는 금색 표시줄을 표시합니다. 금색 표시줄에 표시된 정보를 통해 사용자는 Live Unit Testing에 대해 자세히 알아보고 활성화할 수 있습니다. 또한 금색 표시줄은 Live Unit Testing 필수 구성 요소가 만족되지 않는 경우 정보를 표시합니다. 여기에는 다음이 포함됩니다.

  - 테스트 어댑터가 누락되어 있습니다.
  - 이전 버전의 테스트 어댑터가 있습니다.
  - 솔루션에서 참조하는 NuGet 패키지 복원이 필요합니다.

- **작업 센터 알림과 통합** Visual Studio IDE는 이제 사용자가 Live Unit Testing이 활성화되었을 때 발생하는 것을 쉽게 알 수 있도록 작업 센터에서 Live Unit Testing 후순위 처리 알림을 보여 줍니다. 이는 대규모 솔루션에서 Live Unit Testing을 시작하는 주요 문제를 해결합니다. 이전에 검사 아이콘이 표시될 때까지 몇 분 동안 사용자는 Live Unit Testing이 실제로 활성화되었는지 작동하고 있는지 여부를 결정할 수 없었습니다. 이제는 아닙니다!

- **MSTest 프레임워크 버전 1에 대한 지원**: Unit Testing은 가장 많이 사용되는 세 가지 단위 테스트 프레임워크인 xUnit, NUnit 및 MSTest와 함께 작동합니다. 이전에 Live Unit Testing은 MSTest 단위 테스트 프로젝트가 MS Test 버전 2를 사용하는 경우에만 작동했습니다. Visual Studio 2017 버전 15.4부터는 이제 MSTest 버전 1도 지원합니다.

- **안정성 및 성능**: Live Unit Testing은 이제 프로젝트가 로드를 완벽하지 완료하지 않은 경우 시스템에서 보다 효과적으로 검색할 수 있도록 하며 Live Unit Testing 충돌을 방지하도록 합니다. 빌드 성능 향상은 시스템이 프로젝트 파일에서 변경된 내용이 없다는 것을 아는 경우 MSBuild 프로젝트의 재평가를 방지합니다.

- **기타 사용자 인터페이스 구체화**:  마우스 오른쪽 단추를 클릭하는 제스처의 혼란스러운 **라이브 테스트 설정 - 포함/제외** 옵션 이름이 **Live Unit Testing 포함/제외**로 변경되었습니다. **테스트** > **Live Unit Testing** 메뉴의 **정리 다시 설정** 옵션이 제거되었습니다. 이제는 **도구** > **옵션** > **Live Unit Testing**을 선택하고 **보관된 데이터 삭제**를 선택하여 액세스할 수 있습니다.

## <a name="version-153"></a>버전 15.3

Visual Studio 2017 버전 15.3부터 시작하는 Live Unit Testing은 두 가지 주요 영역에서 개선 사항 및 향상된 기능을 포함합니다.

- .NET Core 및 .NET Standard에 대한 지원 C# 또는 Visual Basic으로 작성된 .NET Core 및 .NET Standard 솔루션에서 Live Unit Testing을 사용할 수 있습니다.

- 성능 향상 첫 번째 전체 빌드와 Live Unit Testing에서 테스트 실행 후에 성능이 매우 빨라졌음을 알 수 있습니다. 같은 솔루션에서 이후 Live Unit Testing을 시작할 때도 상당한 성능 향상을 확인할 수 있습니다. 이제 Live Unit Testing에서 생성된 데이터를 유지하고 최신 검사에서 최대한 많이 재사용합니다.

이러한 주요 추가 사항 외에 Live Unit Testing에서는 다음과 같은 사항도 개선되었습니다.

- 이제 테스트 메서드를 일반 메서드와 구분하기 위해 새 비커 아이콘이 사용됩니다. 빈 비커 아이콘은 특정 테스트가 Live Unit Testing에 포함되지 않음을 나타냅니다.

- Live Unit Testing 검사 아이콘의 UI 팝업 창에서 테스트 메서드를 클릭할 때 이제 코드 편집기를 나가지 않고 UI 창 내의 해당 컨텍스트에서 직접 테스트를 디버그할 수 있는 옵션이 있습니다. 이 기능은 실패한 테스트를 찾을 때 특히 유용합니다.

- [도구]/[옵션]/[Live Unit Testing]/[일반]에 구성 가능한 옵션이 여러 가지 더 추가되었습니다. Live Unit Testing에 사용되는 메모리를 제한할 수 있습니다. 열려 있는 솔루션의 지속형 Live Unit Testing 데이터에 대한 파일 경로도 지정할 수 있습니다.

- [테스트]/[Live Unit Testing]의 메뉴 모음 아래에 여러 가지 메뉴 항목이 더 추가되었습니다. **Reset Clean(정리 다시 설정)** 은 지속형 데이터를 삭제하고 다시 생성합니다. **옵션**을 선택하면 [도구]/[옵션]/[Live Unit Testing]/[일반]으로 이동합니다.

- 이제 다음 특성을 사용하여 Live Unit Testing에서 제외하려는 대상 테스트 메서드를 소스 코드에 지정할 수 있습니다.

  - xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
  - NUnit: `[Category("SkipWhenLiveUnitTesting")]`
  - MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>참조

- [Live Unit Testing 소개](live-unit-testing-intro.md)
- [Visual Studio를 사용한 Live Unit Testing](live-unit-testing.md)
