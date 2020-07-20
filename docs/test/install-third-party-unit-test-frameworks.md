---
title: 타사 단위 테스트 프레임워크 설치
ms.date: 07/09/2020
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c274f203b9bf2746716c0625c61141aaa332977a
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387189"
---
# <a name="install-unit-test-frameworks"></a>단위 테스트 프레임워크 설치

Visual Studio 테스트 탐색기는 어댑터 인터페이스를 개발한 단위 테스트 프레임워크에서 테스트를 실행할 수 있습니다. 프레임워크를 설치하면 이진 파일을 복사하고, 지원하는 언어에 대한 Visual Studio 프로젝트 템플릿이 추가됩니다. 템플릿으로 프로젝트를 만들면 프레임워크가 테스트 탐색기에 등록됩니다.

Visual Studio 솔루션에는 다양한 프레임워크를 사용하고 다양한 언어로 대상이 지정되는 단위 테스트 프로젝트가 포함될 수 있습니다.

::: moniker range=">=vs-2019"
.NET의 경우 [MSTest, NUnit 및 xUnit](getting-started-with-unit-testing.md)은 Visual Studio에서 제공되며 기본적으로 설치되는 테스트 프레임워크입니다.
::: moniker-end
::: moniker range="vs-2017"
[MSTest](getting-started-with-unit-testing.md)는 Visual Studio에서 제공하는 테스트 프레임워크이며 기본적으로 설치됩니다.
::: moniker-end

## <a name="acquire-frameworks"></a>프레임워크 취득

**NuGet 패키지 관리자**를 사용하여 타사 단위 테스트 프레임워크를 설치합니다.

1. 테스트 코드가 포함될 프로젝트를 마우스 오른쪽 단추로 클릭하고 **NuGet 패키지 관리**를 선택합니다.

2. **NuGet 패키지 관리자**에서 설치할 테스트 프레임워크를 검색한 다음, **설치**를 클릭합니다.

   ![Visual Studio의 NuGet 패키지 관리자](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>최신 테스트 어댑터로 업데이트

테스트 검색 및 실행을 향상하려면 안정적인 최신 테스트 어댑터로 업데이트합니다. MSTest, NUnit 및 xUnit 테스트 어댑터의 업데이트에 대한 자세한 내용은 [Visual Studio 블로그](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/)를 참조하세요.

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>안정적인 최신 테스트 어댑터 버전으로 업데이트하려면

1. **도구** > **NuGet 패키지 관리자** > **솔루션에 대한 NuGet 패키지 관리**로 이동하여 솔루션에 대한 NuGet 패키지 관리자를 엽니다.

2. **업데이트** 탭을 클릭하고 설치된 MSTest, NUnit 또는 xUnit 테스트 어댑터를 검색합니다.

3. 각 테스트 어댑터를 선택한 다음, 드롭다운 메뉴에서 안정적인 최신 버전을 선택합니다.

4. **설치** 단추를 선택합니다.

   ![테스트 어댑터 업그레이드](media/install-adapter-upgrade.png)

## <a name="see-also"></a>참조

- [코드 단위 테스트](../test/unit-test-your-code.md)
