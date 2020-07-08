---
title: 컴파일 및 빌드
description: 이 문서에서는 Mac용 Visual Studio에서 프로젝트와 솔루션을 컴파일 및 빌드하는 방법을 설명합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: FB253757-DB00-4889-A6BF-E44722E25BD1
ms.topic: overview
ms.openlocfilehash: 532a245b8e217ea278bf5a3424a194ce87ae43f4
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85950038"
---
# <a name="compiling-and-building-in-visual-studio-for-mac"></a>Mac용 Visual Studio에서 컴파일 및 빌드

Mac용 Visual Studio를 사용하면 프로젝트를 개발하는 동안 애플리케이션을 빌드하고 어셈블리를 만들 수 있습니다. 형식 불일치 및 기타 컴파일 시간 오류를 식별할 수 있도록 조기에 자주 코드를 컴파일 및 빌드하는 것이 중요합니다.

## <a name="building-from-the-ide"></a>IDE에서 빌드

Mac용 Visual Studio를 사용하면 빌드 기능을 제어하는 동시에 즉시 빌드를 만들고 실행할 수 있습니다. Mac용 Visual Studio는 MSBuild를 기본 빌드 시스템으로 사용합니다.

IDE에서 만든 모든 프로젝트와 솔루션에는 빌드 컨텍스트를 정의하는 기본 빌드 구성이 있습니다. 이러한 구성을 편집하거나 직접 만들 수 있습니다. 구성을 만들거나 수정하면 프로젝트 파일이 자동으로 업데이트되며, MSBuild에서 프로젝트를 빌드하는 데 사용됩니다.

IDE에서 프로젝트와 솔루션을 빌드하는 방법에 대한 자세한 내용은 [프로젝트 및 솔루션 빌드 및 정리](building-and-cleaning-projects-and-solutions.md) 가이드를 참조하세요.

Mac용 Visual Studio를 사용하여 다음 작업을 수행할 수도 있습니다.

* 출력 경로 변경. 이 설정은 다음 프로젝트 옵션에서 편집합니다.

    ![출력 경로 변경](media/compiling-and-building-image4.png)

* 빌드 출력의 세부 정보 표시 변경:

    ![빌드 세부 정보 표시 변경](media/compiling-and-building-image5.png)

* 빌드나 정리 전후 또는 도중에 사용자 지정 명령 추가:

    ![사용자 지정 명령 추가](media/compiling-and-building-image6.png)

## <a name="building-from-command-line"></a>명령줄에서 빌드

MSBuild 빌드 엔진을 사용하여 명령줄을 통해 애플리케이션을 빌드할 수 있습니다.

MSBuild 사용 방법에 대한 자세한 내용은 [MSBuild](/visualstudio/msbuild/msbuild) 콘텐츠를 참조하세요.

## <a name="building-from-azure-pipelines"></a>Azure Pipelines에서 빌드

* [Xamarin 앱 빌드](/vsts/pipelines/apps/mobile/xamarin?view=vsts&tabs=vsts)
* [Xamarin과의 연속 통합](https://developer.xamarin.com/guides/cross-platform/ci/)

## <a name="see-also"></a>참고 항목

- [컴파일 및 빌드(Windows의 Visual Studio)](/visualstudio/ide/compiling-and-building-in-visual-studio)