---
title: C++용 CTest 사용 방법
ms.date: 01/23/2020
ms.topic: how-to
ms.author: corob
manager: jillfra
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: c429c9e676ead54bb9f168e3220bf2d4791fac63
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287235"
---
# <a name="how-to-use-ctest-for-c-in-visual-studio-2017-and-later"></a>Visual Studio 2017 이상에서 C++용 CTest를 사용하는 방법 | Microsoft Docs

CMake(CTest 포함)는 **C++를 통한 데스크톱 개발** 워크로드의 구성 요소로 기본적으로 Visual Studio IDE에 통합되어 있습니다. 머신에 설치해야 하는 경우 Visual Studio 설치 관리자 프로그램을 열고 **C++를 사용한 데스크톱 개발** 단추를 클릭한 다음, **수정**을 클릭합니다. 워크로드 구성 요소 목록 아래에서 **Windows용 C++ CMake 도구**를 선택합니다.

## <a name="to-write-tests"></a>테스트를 작성하려면

Visual Studio의 CMake 지원은 Visual Studio 프로젝트 시스템과 관련이 없습니다. 따라서 다른 CMake 환경에서와 마찬가지로 CTest 테스트를 작성 및 구성합니다. `enable_testing()` 명령을 사용하여 테스트를 사용하도록 설정하고 `add_test()` 또는 `gtest_discover_tests()` 명령을 사용하여 새 테스트를 추가합니다. CTest에 대한 자세한 내용은 [CMake 설명서](https://gitlab.kitware.com/cmake/community/wikis/doc/ctest/Testing-With-CTest)를 참조하세요. 

Visual Studio에서 CMake를 사용하는 방법에 대한 자세한 내용은 [Visual Studio의 CMake 프로젝트](/cpp/build/cmake-projects-in-visual-studio)를 참조하세요.

## <a name="to-run-tests"></a>테스트를 실행하려면

CTest는 **테스트 탐색기**와 완전히 통합되어 있고 Google 및 Boost 단위 테스트 프레임워크를 모두 지원합니다. 이러한 프레임워크는 기본적으로 **C++를 통한 데스크톱 개발** 워크로드의 구성 요소로 포함됩니다. 그러나 이전 버전의 Visual Studio에서 프로젝트를 업그레이드하는 경우 Visual Studio 설치 관리자 프로그램을 사용하여 해당 프레임워크를 설치해야 할 수 있습니다.

다음 그림은 Google Test 프레임워크를 사용하여 실행되는 CTest의 결과를 보여줍니다.

![Visual Studio의 Google Test 프레임워크를 사용한 CTest](media/ctest-test-explorer.png)

CTest를 사용하지만 Google 또는 Boost 어댑터를 사용하지 않는 경우 개별 테스트 메서드 수준 대신 CTest 수준에서 결과가 표시됩니다. CTest 전용 실행 파일을 디버그하고 단계별로 실행할 수 있지만 개별 테스트에 대한 스택 추적은 지원되지 않습니다.

## <a name="see-also"></a>참고 항목

- [C/C++에 대한 단위 테스트 작성](writing-unit-tests-for-c-cpp.md)
