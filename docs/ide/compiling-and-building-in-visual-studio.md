---
title: 컴파일 빌드
ms.date: 07/14/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c55f229550dfe74606f4dfb0880b4e91d689d5ad
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809035"
---
# <a name="compile-and-build-in-visual-studio"></a>Visual Studio에서 컴파일 및 빌드

IDE에서 빌드하는 방법에 대한 가장 기본적인 개요는 [연습: 애플리케이션 빌드](walkthrough-building-an-application.md)를 참조하세요.

Visual Studio IDE, MSBuild 명령줄 도구 및 Azure Pipelines와 같은 방법 중 하나를 사용하여 애플리케이션을 빌드할 수 있습니다.

| 빌드 방법 | 이점 |
| --- |--- | --- |
| IDE |- 즉시 빌드를 만들고 디버거에서 테스트할 수 있습니다.<br />- C++ 및 C# 프로젝트에 대해 다중 프로세서 빌드를 실행할 수 있습니다.<br />-   빌드 시스템의 다양한 측면을 사용자 지정할 수 있습니다. |
| CMake | - CMake 도구를 사용하여 프로젝트를 빌드할 수 있습니다.<br />- Linux 및 Windows 플랫폼에서 동일한 빌드 시스템을 사용할 수 있습니다. |
| MSBuild 명령줄| - Visual Studio를 설치하지 않고도 프로젝트를 빌드할 수 있습니다.<br />- 모든 프로젝트 형식에 대해 다중 프로세서 빌드를 실행할 수 있습니다.<br />-   빌드 시스템의 영역 대부분을 사용자 지정할 수 있습니다.|
| Azure Pipelines | - 지속적인 통합/지속적인 업데이트 파이프라인의 일부로 빌드 프로세스를 자동화할 수 있습니다.<br />- 모든 빌드에서 자동화된 테스트를 적용할 수 있습니다.<br />- 빌드 프로세스에 사실상 제한 없는 클라우드 기반 리소스를 사용할 수 있습니다.<br />- 빌드 워크플로를 수정하고 빌드 작업을 만들어 사용자 지정 수준이 높은 작업을 수행할 수 있습니다.|

이 섹션의 문서에는 IDE 기반 빌드 프로세스에 대한 자세한 내용이 나와 있습니다. 다른 방법에 대한 자세한 내용은 [MSBuild](../msbuild/msbuild.md) 및 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)를 각각 참조하세요.

> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio에서 컴파일 및 빌드](/visualstudio/mac/compiling-and-building)를 참조하세요.

## <a name="overview-of-building-from-the-ide"></a>IDE에서 빌드하는 방법에 대한 개요

사용자가 프로젝트를 만드는 경우 Visual Studio에서 해당 프로젝트와 프로젝트가 포함된 솔루션에 대해 기본 빌드 구성을 만듭니다.  이러한 구성은 솔루션 및 프로젝트를 빌드하고 배포하는 방법을 정의합니다. 특히 프로젝트 구성은 대상 플랫폼(예: Windows 또는 Linux) 및 빌드 형식(예: 디버그 또는 릴리스)에 대해 고유합니다. 사용자는 원하는 방식으로 이러한 구성을 편집할 수도 있고, 필요에 따라 고유한 구성을 만들 수도 있습니다.

IDE에서 빌드하는 방법에 대한 가장 기본적인 개요는 [연습: 애플리케이션 빌드](walkthrough-building-an-application.md)를 참조하세요.

그런 다음 [Visual Studio에서 프로젝트 및 솔루션 빌드 및 정리](building-and-cleaning-projects-and-solutions-in-visual-studio.md)를 참조하여 프로세스에 대해 수행할 수 있는 다양한 측면의 사용자 지정 작업에 대해 알아보세요. 사용자 지정 작업으로는 [출력 디렉터리 변경](how-to-change-the-build-output-directory.md), [사용자 지정 빌드 이벤트 지정](specifying-custom-build-events-in-visual-studio.md), [프로젝트 종속성 관리](how-to-create-and-remove-project-dependencies.md), [빌드 로그 파일 관리](how-to-view-save-and-configure-build-log-files.md) 및 [컴파일러 경고 표시 안 함](how-to-suppress-compiler-warnings.md)이 있습니다.

다음과 같은 다른 다양한 작업도 알아볼 수 있습니다.
- [빌드 구성 이해](understanding-build-configurations.md)
- [빌드 플랫폼 이해](understanding-build-platforms.md)
- [프로젝트 및 솔루션 속성 관리](managing-project-and-solution-properties.md)
- [C#](how-to-specify-build-events-csharp.md) 및 [Visual Basic](how-to-specify-build-events-visual-basic.md)에서 빌드 이벤트 지정
- [빌드 옵션 설정](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [병렬로 여러 프로젝트 빌드](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="see-also"></a>참고 항목

- [웹 사이트 프로젝트 빌드(컴파일)](/previous-versions/hwxa5aha(v=vs.140))
- [컴파일 및 빌드(Mac용 Visual Studio)](/visualstudio/mac/compiling-and-building)
- [Visual Studio의 CMake 프로젝트](/cpp/build/cmake-projects-in-visual-studio)