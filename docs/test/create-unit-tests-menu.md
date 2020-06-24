---
title: 단위 테스트 메서드 스텁 만들기
ms.date: 04/24/2020
ms.topic: how-to
helpviewer_keywords:
- unit testing, create unit tests
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b2712210d4761edb90414e2a27beba74a3bacbf
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288665"
---
# <a name="create-unit-test-method-stubs-with-the-create-unit-tests-command"></a>단위 테스트 만들기 명령을 사용하여 단위 테스트 메서드 스텁 만들기

**단위 테스트 만들기** 명령을 사용하면 단위 테스트 메서드 스텁이 생성됩니다. 이 기능을 사용하여 테스트 프로젝트, 테스트 클래스 및 클래스 내 테스트 메서드 스텁을 쉽게 구성할 수 있습니다.

::: moniker range="vs-2017"
> [!NOTE]
> **단위 테스트 만들기** 메뉴 명령은 .NET Framework(하지만 .NET Core 아님)를 대상으로 하는 C# 코드에서만 사용할 수 있습니다.
::: moniker-end
::: moniker range=">=vs-2019"
> [!NOTE]
> **단위 테스트 만들기** 메뉴 명령은 C# 코드에만 사용할 수 있습니다.
::: moniker-end

**단위 테스트 만들기** 메뉴 명령은 확장 가능하며 MSTest, MSTest V2, NUnit 및 xUnit에 대한 테스트를 생성하는 데 사용할 수 있습니다.

## <a name="get-started"></a>시작

시작하려면 테스트할 프로젝트의 코드 편집기에서 메서드, 형식 또는 네임스페이스를 선택하고 마우스 오른쪽 단추로 클릭한 다음, **단위 테스트 만들기**를 선택합니다. 테스트를 생성하는 방법을 구성할 수 있는 **단위 테스트 만들기** 대화 상자가 열립니다.

![단위 테스트 만들기 명령 사용](media/createunittestcommand.png)

## <a name="set-unit-test-traits"></a>단위 테스트 특성 설정

이러한 테스트를 테스트 자동화 프로세스의 일부로 실행하려면 다른 테스트 프로젝트에서 만들어진 테스트를 사용하고(위 대화 상자의 두 번째 옵션) 단위 테스트에 대한 단위 테스트 특성을 설정하는 방법을 고려할 수 있습니다. 이 방법으로 이러한 특정 테스트를 지속적인 통합 또는 지속적인 배포 파이프라인의 일부로 더 쉽게 포함하거나 제외할 수 있습니다. 다음과 같이 단위 테스트에 직접 메타데이터를 추가하여 특성을 설정합니다.

![단위 테스트 특성 설정](media/createunittest.png)

## <a name="use-third-party-unit-test-frameworks"></a>타사 단위 테스트 프레임워크 사용

NUnit 또는 xUnit에 대한 단위 테스트를 자동으로 생성하려면 Visual Studio Marketplace에서 다음 테스트 프레임워크 확장 중 하나를 설치합니다.

* [NUnit extension for test generators](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension)(테스트 생성기의 NUnit 확장)
* [xUnit.net extension for test generators](https://marketplace.visualstudio.com/items?itemName=BradWilson.xUnitnetTestExtensions)(테스트 생성기의 xUnit.net 확장)

## <a name="when-should-i-use-this-feature"></a>이 기능은 언제 사용해야 하나요?

이 기능은 단위 테스트를 만들어야 할 때마다 사용하지만, 특히 테스트 검사가 거의 없거나 문서가 없는 기존 코드를 테스트할 경우 사용합니다. 즉, 코드 사양이 제한되거나 없는 경우 사용합니다. 이 기능은 관찰된 코드 동작의 특징을 결정하는 [스마트 단위 테스트](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/)와 비슷한 방법을 효과적으로 구현합니다.

그러나 이 기능은 개발자가 일부 코드를 작성하여 시작한 다음, 이를 사용하여 단위 테스트를 부트스트랩하는 상황에도 동일하게 적용됩니다. 코딩 흐름 내에서 개발자는 특정 코드 조각에 대한 단위 테스트 메서드 스텁(적합한 테스트 클래스 및 적합한 테스트 프로젝트 사용)을 신속하게 만들 수 있습니다.

## <a name="see-also"></a>참조

- [Creating unit test method stubs with “Create Unit Tests”](https://devblogs.microsoft.com/devops/creating-unit-test-method-stubs-with-create-unit-tests/)(“유닛 테스트 만들기”를 사용하여 유닛 테스트 메서드 스텁 만들기)
- [유닛 테스트 블로그 게시물](https://devblogs.microsoft.com/devops/?s=unit+testing)
