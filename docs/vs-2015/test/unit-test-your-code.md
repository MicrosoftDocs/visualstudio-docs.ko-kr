---
title: 코드 단위 테스트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a8b9a4b52fce5fb838c12ccf057fd0e80619cd7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851255"
---
# <a name="unit-test-your-code"></a>코드 단위 테스트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

개발자와 테스터는 단위 테스트를 통해 [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)], [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] 및 [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)] 프로젝트에서 클래스의 메서드에 있는 논리 오류를 빠르게 찾을 수 있습니다.

 단위 테스트 도구는 다음과 같습니다.

1. **테스트 탐색기.** 테스트 탐색기에서는 단위 테스트를 실행하고 그 결과를 볼 수 있습니다. 테스트 탐색기에서는 타사 프레임워크를 비롯하여 탐색기용 어댑터가 있는 모든 단위 테스트 프레임워크를 사용할 수 있습니다.

2. **관리 코드용 Microsoft 단위 테스트 프레임워크.** 관리 코드용 Microsoft 단위 테스트 프레임워크는 Visual Studio와 함께 설치되며 .NET 코드 테스트용 프레임워크를 제공합니다.

3. **C++용 Microsoft 단위 테스트 프레임워크.** C++용 Microsoft 단위 테스트 프레임워크는 Visual Studio와 함께 설치되며 네이티브 코드 테스트용 프레임워크를 제공합니다.

4. **코드 검사 도구.** 단위 테스트가 테스트 탐색기의 명령 하나에서 실행하는 제품 코드의 양을 결정할 수 있습니다.

5. **Microsoft Fakes 격리 프레임워크.** Microsoft Fakes 격리 프레임워크는 테스트 중인 코드에서 종속성을 만드는 프로덕션 및 시스템 코드에 대한 대체 클래스 및 메서드를 만들 수 있습니다. 함수에 대한 모조 위임을 구현하여 종속성 개체의 동작과 출력을 제어할 수 있습니다.

   [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md)를 사용하면 .NET 코드를 탐색하여 테스트 데이터 및 단위 테스트 도구 모음을 생성할 수도 있습니다. 코드의 모든 문에 대해 해당 문을 실행할 테스트 입력이 생성됩니다. 코드의 모든 조건부 분기에 대해 사례 분석이 수행됩니다.

## <a name="key-tasks"></a>주요 작업
 다음 항목은 단위 테스트를 이해하고 만드는 데 유용합니다.

|작업|관련 항목|
|-----------|-----------------------|
|**빠른 시작 및 연습:** 다음 항목을 사용하여 코드 예제에서 Visual Studio의 단위 테스트에 대해 알아봅니다.|-   [연습: 관리 코드에 대한 단위 테스트 만들기 및 실행](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [빠른 시작: 테스트 탐색기를 사용한 테스트 기반 개발](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [기존 c + + 응용 프로그램에 단위 테스트 추가](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [테스트 탐색기를 사용 하 여 네이티브 코드 단위 테스트](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|
|**테스트 탐색기를 사용한 단위 테스트:** 테스트 탐색기를 통해 보다 다 생산적이고 효율적인 단위 테스트를 만드는 방법에 대해 알아봅니다.|-   [단위 테스트 기본 사항](../test/unit-test-basics.md)<br />-   [단위 테스트 프로젝트 만들기](../test/create-a-unit-test-project.md)<br />-   [테스트 탐색기를 사용 하 여 단위 테스트 실행](../test/run-unit-tests-with-test-explorer.md)<br />-   [타사 단위 테스트 프레임 워크 설치](../test/install-third-party-unit-test-frameworks.md)<br />-   [Visual Studio 2010에서 단위 테스트 업그레이드](https://msdn.microsoft.com/9bb75856-f68a-4de2-a084-b08a947a1172)|
|**관리 코드 단위 테스트:**|-   [관리 코드용 Microsoft 단위 테스트 프레임워크를 사용하여 .NET Framework용 단위 테스트 작성](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|
|**C++ 코드 단위 테스트**|-   [C + + 용 Microsoft 단위 테스트 프레임 워크를 사용 하 여 C/c + +에 대 한 단위 테스트 작성](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**단위 테스트 격리**|-   [Microsoft Fakes를 사용 하 여 테스트 중인 코드 격리](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**코드 검사를 사용하여 프로젝트의 코드 중 단위 테스트로 테스트되는 부분 식별:**[!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)]테스트 도구의 코드 검사 기능에 대해 알아보세요.|-   [코드 검사를 사용 하 여 테스트할 코드 범위 결정](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**단위 테스트에 대한 부하 테스트를 사용하여 스트레스 및 성능 분석 수행:** 애플리케이션에서 성능 및 스트레스 문제를 격리하기 위해 부하 테스트를 만들고 여기에 단위 테스트를 추가할 수 있습니다. **참고:**  부하 테스트를 만들고 사용하려면 Visual Studio Enterprise가 필요합니다.|-   [부하 테스트 만들기 및 편집](https://msdn.microsoft.com/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [방법: 부하 테스트 시나리오에 웹 성능 테스트 및 단위 테스트 추가](https://msdn.microsoft.com/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [방법: 부하 테스트 시나리오에서 웹 성능 테스트 및 단위 테스트 제거](https://msdn.microsoft.com/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|
|**품질 게이트 설정 및 적용:** 코드의 품질을 확인하기 위해 코드를 체크 인하기 전에 테스트가 실행되도록 품질 게이트를 만들 수 있습니다.|-   [품질 게이트 설정 및 적용](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**단위 테스트 형식 확장:** 단위 테스트 프레임워크에 없을 수도 있는 테스트에 기능을 추가할 수 있습니다. 예를 들어 테스트를 일반 사용자로 실행할지 여부를 지정하는 테스트 속성을 추가할 수 있습니다. 또는 프레임워크를 확장하여 메서드에 행 특성을 추가하고 테스트에서 이 행의 데이터를 사용할 수 있습니다.|단위 테스트 프레임워크를 확장하는 방법에 대한 예제 코드는 다음 [Microsoft 웹 사이트](https://msdn.microsoft.com/vstudio/ff420671.aspx)를 참조하세요.|
|**테스트 옵션 설정:** 예를 들면 테스트 결과가 저장되는 위치를 지정할 수 있습니다.|[.runsettings 파일을 사용하여 단위 테스트 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="related-tasks"></a>관련 작업
 [Microsoft Test Manager에서 테스트 결과 검토](https://msdn.microsoft.com/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)

 테스트 결과에 대해 설명하고, 테스트 결과 보기, 저장 및 삭제 방법을 비롯하여 테스트 결과의 사용 방법에 대해 설명합니다.

 [Microsoft Visual Studio를 사용 하 여 시스템 테스트 실행](https://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)

 Visual Studio를 사용하여 자동화된 테스트를 실행하는 방법을 [!INCLUDE[TCMext](../includes/tcmext-md.md)]를 사용할 경우와 비교하여 설명하는 항목에 대한 링크를 제공합니다.

## <a name="reference"></a>참조
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> 특성, 예외, 어설션 및 단위 테스트를 지 원하는 기타 클래스를 제공 하는 UnitTesting 네임 스페이스에 대해 설명 합니다.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> 및 웹 서비스 단위 테스트에 대 한 지원을 제공 하 여 UnitTesting 네임 스페이스를 확장 하는 UnitTesting 네임 스페이스에 대해 설명 합니다 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .

## <a name="external-resources"></a>외부 리소스

### <a name="videos"></a>동영상
 [채널 9: XAML을 사용하여 빌드한 Windows 스토어 앱 유닛 테스트](https://channel9.msdn.com/Events/BUILD/BUILD2011/TOOL-529T)

### <a name="forums"></a>포럼
 [Visual Studio 유닛 테스트](https://social.msdn.microsoft.com/Forums/en/vsunittest/threads)

### <a name="guidance"></a>지침
 [Visual Studio 2012를 사용한 연속 배달 테스트 - 2장: 단위 테스트: 내부 테스트](https://msdn.microsoft.com/library/jj159340.aspx)

### <a name="reference"></a>참조
 [단위 테스트에 대한 콘텐츠 인덱스](https://blogs.msdn.com/b/mathew_aniyan/archive/2012/05/17/content-index-for-unit-test.aspx)

## <a name="see-also"></a>관련 항목
 [응용 프로그램 테스트](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) [코드 품질 향상](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)
