---
title: Visual Studio 버전 Side-by-Side 설치 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1ef2d51e35a198dbe6da3c1a034dd7c8d1bf8922
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851021"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Visual Studio 버전 병렬 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이전 버전이 설치된 컴퓨터에 이 버전의 Visual Studio를 설치할 수 있습니다. 설치 오류가 발생할 경우 문제를 직접 디버그할 수 있도록 [로그 수집 도구](https://www.microsoft.com/download/details.aspx?id=12493) 를 사용하여 오류에 대한 정보를 수집할 수 있습니다.

> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 버전은 출시 순서대로 설치하는 것이 좋습니다. 예를 들어 Visual Studio 2015를 설치하기 전에 Visual Studio 2013을 설치합니다.

 여러 버전을 함께 설치하기 전에 다음과 같은 조건을 검토해야 합니다.

- Visual Studio 2015를 사용하여 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]에서 만든 솔루션을 여는 경우 Visual Studio 2015 특정 기능을 구현하지 않았다면 나중에 이전 버전에서 다시 솔루션을 열어 수정할 수 있습니다.

- Visual Studio 2015를 사용하여 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] 이전 버전에서 만든 솔루션을 열려면 Visual Studio 2015와 호환되도록 프로젝트와 파일을 수정해야 할 수 있습니다. 자세한 내용은 [Visual Studio 프로젝트 포트, 마이그레이션 및 업그레이드](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015) 페이지를 참조 하세요.

- 둘 이상의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 버전이 설치된 컴퓨터에서 한 버전을 제거할 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 의 파일 연결이 모든 버전에 대해 제거됩니다. **옵션** 대화 상자의 **환경**, **일반** 페이지에 있는 [파일 연결 복원](../ide/reference/general-environment-options-dialog-box.md) 단추를 사용하여 이 파일 연결을 다시 매핑할 수 있습니다.

- 모든 확장이 호환되는 것은 아니므로 Visual Studio에서는 확장을 자동으로 업그레이드하지 않습니다. [Visual Studio Marketplace](https://visualstudiogallery.msdn.microsoft.com/) 또는 소프트웨어 게시자에서 확장을 다시 설치해야 합니다.

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework 버전 및 Side-by-Side 설치

- Visual Basic, Visual C# 및 Visual F# 프로젝트에는 **프로젝트 디자이너** 의 **대상 프레임워크** 옵션을 사용하여 프로젝트에 사용할 .NET Framework 버전을 지정합니다. C++ 프로젝트의 경우 .vcxproj 파일을 수정하여 수동으로 대상 프레임워크를 변경할 수 있습니다. 자세한 내용은 [버전 호환성](https://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f)을 참조하세요.

     프로젝트를 만들 때 **새 프로젝트** 대화 상자의 **.NET Framework** 목록에서 프로젝트 대상으로 사용할 .NET Framework 버전을 지정할 수 있습니다.

     언어별 정보는 다음 테이블에서 해당 항목을 참조하세요.

    |언어|항목|
    |--------------|-----------|
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[프로젝트 디자이너, 애플리케이션 페이지(Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|
    |Visual C#|[프로젝트 디자이너, 애플리케이션 페이지(C#)](../ide/reference/application-page-project-designer-csharp.md)|
    |Visual F#|[프로젝트 구성](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|
    |C++|[방법: 대상 프레임워크 및 플랫폼 도구 세트 수정](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[이전 버전의 공용 언어 런타임에서 JScript 애플리케이션 실행](https://msdn.microsoft.com/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|

## <a name="see-also"></a>관련 항목

- [Visual Studio 설치](../install/install-visual-studio-2015.md)
- [Visual Studio 프로젝트 포트, 마이그레이션 및 업그레이드](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015)
- [C/C++ 격리된 애플리케이션 및 side-by-side 어셈블리 빌드](https://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)
- [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)
