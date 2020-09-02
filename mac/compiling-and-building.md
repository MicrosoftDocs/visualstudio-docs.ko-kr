---
title: 컴파일 및 빌드
description: 이 문서에서는 Mac용 Visual Studio에서 프로젝트와 솔루션을 컴파일 및 빌드하는 방법을 설명합니다.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/29/2019
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.openlocfilehash: b4f1cfc3dfdffcc3dd4cb90cd7d29d4333578b9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71128413"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Mac용 Visual Studio에서 컴파일 및 빌드

Mac용 Visual Studio를 사용하면 프로젝트를 개발하는 동안 애플리케이션을 빌드하고 어셈블리를 만들 수 있습니다. 형식 불일치, 잘못된 구문, 철자가 틀린 키워드 및 기타 컴파일 시간 오류를 신속하게 식별할 수 있도록 코드를 자주 빌드해야 합니다. 디버깅을 빌드하면 논리, IO 및 0으로 나누기 오류와 같은 런타임 오류도 찾아 해결할 수 있습니다.

성공적인 빌드는 소스 코드에 올바른 구문이 포함되어 있고 라이브러리, 어셈블리 및 기타 구성 요소에 대한 모든 정적 참조를 확인하는 것을 나타냅니다. 빌드 프로세스는 애플리케이션 실행 파일을 생성 합니다. 다양한 종류의 수동 테스트와 자동화된 테스트를 통해 이 실행 파일을 테스트하여 코드 품질의 유효성을 검사할 수 있습니다. 애플리케이션이 완전히 테스트된 후에는 고객에게 배포할 릴리스 버전을 컴파일할 수 있습니다.

Mac에서 다음 방법 중 하나를 사용하여 애플리케이션을 빌드할 수 있습니다. Mac용 Visual Studio, MSBuild 명령줄 도구 또는 Azure Pipelines를 사용합니다.

| 빌드 방법 | 이점 |
| --- |--- | --- |
| Mac용 Visual Studio |- 즉시 빌드를 만들고 디버거에서 테스트할 수 있습니다.<br />- C# 프로젝트에 대해 다중 프로세서 빌드를 실행할 수 있습니다.<br />-   빌드 시스템의 다양한 측면을 사용자 지정할 수 있습니다. |
| MSBuild 명령줄| - Mac용 Visual Studio를 설치하지 않고도 프로젝트를 빌드할 수 있습니다.<br />- 모든 프로젝트 형식에 대해 다중 프로세서 빌드를 실행할 수 있습니다.<br />-   빌드 시스템의 영역 대부분을 사용자 지정할 수 있습니다.|
| Azure Pipelines | - 지속적인 통합/지속적인 업데이트 파이프라인의 일부로 빌드 프로세스를 자동화할 수 있습니다.<br />- 모든 빌드에서 자동화된 테스트를 적용할 수 있습니다.<br />- 빌드 프로세스에 사실상 제한 없는 클라우드 기반 리소스를 사용할 수 있습니다.<br />- 빌드 워크플로를 수정하고 빌드 작업을 만들어 사용자 지정 수준이 높은 작업을 수행할 수 있습니다.|

이 섹션의 문서에는 IDE 기반 빌드 프로세스에 대한 자세한 내용이 나와 있습니다. 명령줄을 통해 애플리케이션을 빌드하는 방법에 대한 자세한 내용은 [MSBuild](/visualstudio/msbuild/msbuild)를 참조하세요. Azure Pipelines를 사용하여 애플리케이션을 빌드하는 방법에 대한 자세한 내용은 [Azure Pipelines](/azure/devops/pipelines)를 참조하세요.


> [!NOTE]
> 이 토픽은 Mac용 Visual Studio에 적용됩니다. Windows용 Visual Studio는 [Visual Studio에서 컴파일 및 빌드](/visualstudio/ide/compiling-and-building-in-visual-studio)를 참조하세요.


## <a name="building-from-the-ide"></a>IDE에서 빌드

Mac용 Visual Studio를 사용하면 빌드 기능을 제어하는 동시에 즉시 빌드를 만들고 실행할 수 있습니다. 프로젝트를 만들 때 Mac용 Visual Studio는 빌드에 대한 컨텍스트를 설정하는 기본 빌드 구성을 정의합니다. 기본 빌드 구성을 편집하고 직접 만들 수도 있습니다. 구성을 만들거나 수정하면 프로젝트 파일이 자동으로 업데이트되며, MSBuild에서 프로젝트를 빌드하는 데 사용됩니다.

IDE에서 프로젝트와 솔루션을 빌드하는 방법에 대한 자세한 내용은 [프로젝트 및 솔루션 빌드 및 정리](building-and-cleaning-projects-and-solutions.md) 가이드를 참조하세요.

Mac용 Visual Studio를 사용하여 다음 작업을 수행할 수도 있습니다.

* 출력 경로 변경. 이 설정은 다음 프로젝트 옵션에서 편집합니다.

    ![출력 경로 변경](media/compiling-and-building-image4.png)

* 빌드 출력의 세부 정보 표시 변경:

    ![빌드 세부 정보 표시 변경](media/compiling-and-building-image5.png)

* 빌드나 정리 전후 또는 도중에 사용자 지정 명령 추가:

    ![사용자 지정 명령 추가](media/compiling-and-building-image6.png)


## <a name="see-also"></a>추가 정보

- [컴파일 및 빌드(Windows의 Visual Studio)](/visualstudio/ide/compiling-and-building-in-visual-studio)
