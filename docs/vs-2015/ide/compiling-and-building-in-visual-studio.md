---
title: 컴파일 및 빌드
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d8ec7d6508ec025a2b2005754da03bdd4db38943
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74300258"
---
# <a name="compiling-and-building-in-visual-studio"></a>Visual Studio에서 컴파일 및 빌드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio를 사용하여 개발 주기 동안 잦은 간격으로 애플리케이션을 빌드하고 어셈블리 및 실행 가능 프로그램을 만들 수 있습니다. 코드를 자주 빌드하면 잘못된 구문, 맞춤법 오류가 있는 키워드 및 형식 불일치와 같은 컴파일 타임 오류를 조기에 식별할 수 있습니다. 디버그 버전의 코드를 자주 빌드하고 실행하면 논리 오류 및 의미 오류와 같은 런타임 오류도 찾아 해결할 수 있습니다.

 프로젝트 또는 솔루션을 완전히 개발하고 충분히 디버깅한 후에는 릴리스 빌드에서 해당 구성 요소를 컴파일할 수 있습니다. 기본적으로 릴리스 빌드는 디버그 버전보다 작고 빠르게 실행되도록 최적화 및 디자인됩니다. 자세한 내용은 [연습: 애플리케이션 빌드](../ide/walkthrough-building-an-application.md)를 참조하세요.

## <a name="choosing-a-build-method"></a>빌드 방법 선택
 IDE에서 기본 빌드 옵션을 사용하거나, 명령 프롬프트를 사용하거나, Team Foundation Build를 사용하여 애플리케이션을 빌드할 수 있습니다. 이러한 각 옵션은 MSBuild를 기본 기술로 사용하며, 각 접근 방식에는 다음 표에 나와 있는 것과 같은 혜택이 있습니다.

|빌드 방법|이점|참조 항목|
|------------------|--------------|--------------------------|
|IDE 사용|-   보다 쉽게 즉시 빌드를 만들고 실행할 수 있습니다.<br />-   C++ 및 C# 프로젝트에 대해 다중 프로세서 빌드를 실행할 수 있습니다.<br />-   빌드 시스템의 일부 측면을 사용자 지정할 수 있습니다.|[Visual Studio에서 프로젝트 및 솔루션 빌드 및 정리](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|MSBuild 명령줄 실행|-   Visual Studio를 설치하지 않고도 프로젝트를 빌드할 수 있습니다.<br />-   모든 프로젝트 형식에 대해 다중 프로세서 빌드를 실행할 수 있습니다.<br />-   빌드 시스템의 영역 대부분을 사용자 지정할 수 있습니다.|[MSBuild](../msbuild/msbuild.md)|
|Team Foundation Build 사용|-   빌드 프로세스를 자동화할 수 있습니다. 예를 들어 밤마다 또는 코드를 체크 인할 때마다 하나 이상의 프로젝트를 빌드할 수 있습니다. 개발 컴퓨터 대신 공유 빌드 서버에서 프로젝트를 빌드할 수도 있습니다.<br />-   빌드하려는 코드, 실행하려는 테스트 및 기타 공통 옵션을 빠르게 지정할 수 있습니다.<br />-   빌드 워크플로를 수정하고 필요에 따라 빌드 작업을 만들어 사용자 지정 수준이 높은 작업을 수행할 수 있습니다.|[애플리케이션 빌드](/azure/devops/pipelines/index)|

## <a name="building-from-the-ide"></a>IDE에서 빌드
 프로젝트를 만들면 기본 빌드 구성이 정의되고 빌드에 대한 컨텍스트를 제공하기 위해 솔루션 빌드 구성이 할당됩니다. 솔루션 구성은 솔루션의 프로젝트가 빌드 및 배포되는 방법을 정의합니다. 프로젝트 구성은 플랫폼 및 빌드 형식(예: 릴리스 Win32)에 대해 고유한 프로젝트 속성 집합입니다. 이러한 기본 구성을 편집하고 자신만의 구성을 만들 수 있습니다. 자세한 내용은 [프로젝트 디자이너 소개](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7) 및 [NIB 방법: 프로젝트 속성 및 구성 설정 수정](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)을 참조하세요.

 IDE 내에서 수행할 수 있는 추가 작업은 다음과 같습니다.

- [빌드 출력 디렉터리를 변경](../ide/how-to-change-the-build-output-directory.md)합니다.

- [올바른 빌드를 위해 다른 프로젝트의 출력에 의존하는 프로젝트 식별](../ide/how-to-create-and-remove-project-dependencies.md)

- [빌드 로그 또는 빌드의 출력 창에 포함되는 정보의 양 변경](../ide/how-to-view-save-and-configure-build-log-files.md)

- [Visual C#, Visual C++ 또는 Visual Basic에 대한 특정 컴파일러 경고 숨기기](../ide/how-to-suppress-compiler-warnings.md)

- [빌드에 대한 사용자 지정 사전 컴파일 및 사후 컴파일 작업 지정](../ide/specifying-custom-build-events-in-visual-studio.md)

- 병렬 빌드를 사용하여 빌드 성능 개선. 자세한 내용은 [병렬로 여러 프로젝트 빌드](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) 또는 블로그 게시물 [Tuning C++ build parallelism](https://blogs.msdn.microsoft.com/msbuild/2010/03/07/tuning-c-build-parallelism-in-vs2010/)(C++ 빌드 병렬 처리 조정)을 참조하세요.

## <a name="see-also"></a>관련 항목
 [연습: 애플리케이션 빌드](../ide/walkthrough-building-an-application.md) [빌드 구성 이해](../ide/understanding-build-configurations.md) [빌드 플랫폼 이해](../ide/understanding-build-platforms.md) [(컴파일) 웹 사이트 프로젝트 빌드](https://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [ 어떻게: 프로젝트 종속성 만들기 및 제거](../ide/how-to-create-and-remove-project-dependencies.md)
