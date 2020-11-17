---
title: 프로젝트 및 솔루션
description: 이 문서에서는 Mac용 Visual Studio의 프로젝트 및 솔루션에 대한 개요를 제공합니다.
ms.topic: overview
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 8254505D-D96E-48BD-8A5E-CF6A917897EA
ms.openlocfilehash: c52b8513937505b40d17f7cd9fc05d9cf6a47941
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493402"
---
# <a name="projects-and-solutions-in-visual-studio-for-mac"></a>Mac용 Visual Studio의 프로젝트 및 솔루션

이 문서는 Mac용 Visual Studio에서 *프로젝트* 및 *솔루션* 에 대한 개요를 제공합니다.

> [!NOTE] 
> 이 토픽은 Mac용 Visual Studio에 적용됩니다. Windows 기반 Visual Studio는 [Visual Studio의 프로젝트 및 솔루션](/visualstudio/ide/solutions-and-projects-in-visual-studio)을 참조하세요.

## <a name="projects"></a>프로젝트

Mac용 Visual Studio에서 새 애플리케이션, 웹 사이트 등을 만드는 경우 프로젝트에서 시작합니다. 프로젝트에는 실행 파일, 라이브러리 또는 웹 사이트로 컴파일하는 데 필요한 모든 필수 요소(소스 코드, 이미지, 데이터 파일 등)가 포함됩니다.

프로젝트는 파일과 폴더 계층 구조, 파일 경로, 빌드 설정 등의 프로젝트 특정 설정을 정의하는 xml이 포함된 파일(예: C#의 경우 `.csproj`)로 정의됩니다.

Mac용 Visual Studio에서 프로젝트가 로드되면 솔루션 창은 프로젝트 파일을 사용하여 프로젝트에 파일 및 폴더를 표시합니다. 컴파일 중 MSBuild는 프로젝트 파일에서 설정을 읽어 실행 파일을 만듭니다.

## <a name="solutions"></a>솔루션

*솔루션* 은 하나 이상의 관련된 프로젝트를 함께 그룹화하는 컨테이너입니다. 솔루션은 고유한 형식을 가진 텍스트 파일(`.sln` 확장명)로 설명되고 직접 편집할 수 없습니다.

## <a name="managing-projects-in-the-solution-window"></a>솔루션 창에서 프로젝트 관리

프로젝트를 만들거나 로드한 다음 솔루션 창을 사용하여 프로젝트 또는 솔루션은 물론 내부에 포함된 파일을 보고 관리할 수 있습니다. 다음 그림에서는 두 프로젝트가 포함된 .NET Core 솔루션이 있는 솔루션 창을 보여 줍니다.

![여러 프로젝트가 포함된 샘플 솔루션](media/solution-example.png)

프로젝트 또는 솔루션 이름을 두 번 클릭하거나, 마우스 오른쪽 단추를 클릭하고 **옵션** 을 선택하여 프로젝트 및 솔루션 모두의 속성을 관리할 수 있습니다.

이러한 옵션에 대한 자세한 내용은 [솔루션 및 프로젝트 속성 관리](managing-solutions-and-project-properties.md) 문서를 참조하세요.

## <a name="see-also"></a>참조

- [Visual Studio의 솔루션 및 프로젝트(Windows)](/visualstudio/ide/solutions-and-projects-in-visual-studio)
