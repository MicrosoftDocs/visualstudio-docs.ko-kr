---
title: 프로젝트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b7a9299321d2aa80eebb564bf9b926f07ab0108
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706208"
---
# <a name="projects"></a>프로젝트
Visual Studio에서 프로젝트는 개발자가 **솔루션 탐색기**에 나타나는 소스 코드 파일 및 기타 리소스를 구성하는 데 사용하는 컨테이너입니다. 일반적으로 프로젝트는 소스 코드 파일 및 비트맵 파일과 같은 리소스에 대한 참조를 저장하는 파일(예: C# 프로젝트의 .csproj 파일)입니다. 프로젝트를 통해 소스 코드, 웹 서비스 및 데이터베이스에 대한 참조 및 기타 리소스를 구성, 빌드, 디버깅 및 배포할 수 있습니다. VSPackage는 *프로젝트 유형,* *프로젝트 하위 유형*및 사용자 지정 *도구의*세 가지 주요 방법으로 Visual Studio 프로젝트 시스템을 확장할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [프로젝트 유형](../../extensibility/internals/project-types.md)

 *프로젝트 유형은* 프로그래밍 언어와 같은 새로운 종류의 프로젝트에 대한 지원을 추가합니다. 예를 들어 Visual Studio에서 지원하는 각 언어에는 자체 프로젝트 유형이 있으며 IronPython 통합 샘플에는 IronPython 언어에 대한 프로젝트 유형이 포함됩니다. C# 또는 Visual Basic 이외의 언어에 대한 프로젝트 유형을 만들어 항목을 빌드, 디버깅, 배포 및 **솔루션 탐색기에서**표시하는 방법을 사용자 지정해야 합니다. 자세한 내용은 [프로젝트 유형을](../../extensibility/internals/project-types.md)참조하십시오.

- [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)

 *프로젝트 하위 유형은* 프로젝트 유형을 기반으로 하며 프로젝트를 빌드, 디버깅 및 배포하는 방법을 사용자 지정하는 데 사용할 수 있습니다. Visual Studio는 스마트 장치 프로젝트에서 프로젝트 하위 유형을 사용합니다. 새로 빌드된 프로그램을 개발 컴퓨터에서 대상 장치로 복사하여 배포를 사용자 지정합니다. C# 및 Visual Basic 프로젝트 형식은 프로젝트 하위 형식의 기준으로 사용할 수 있습니다. C++ 프로젝트 유형은 할 수 없습니다. 사용자 고유의 프로젝트 형식을 프로젝트 하위 형식의 기준으로 사용할 수도 있습니다. 자세한 내용은 [프로젝트 하위 유형을](../../extensibility/internals/project-subtypes.md)참조하십시오.

- [웹 프로젝트](../../extensibility/internals/web-projects.md)

 웹 프로젝트를 설명하여 웹 응용 프로그램을 만듭니다.

- [새로운 프로젝트 생성: 후드 아래, 1부](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) 및 [새로운 프로젝트 생성: 후드 아래, 2부](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 새 프로젝트를 만들 때 실제로 발생하는 현상에 대해 설명합니다.

- [VSSDK 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 프로젝트 및 솔루션을 처리하는 VSSDK의 샘플을 포함합니다.

## <a name="related-sections"></a>관련 단원
- [Visual Studio SDK 기본 사항](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Visual Studio 확장성의 다양한 측면을 설명합니다.
