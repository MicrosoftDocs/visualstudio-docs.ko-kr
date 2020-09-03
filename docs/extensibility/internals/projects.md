---
title: 프로젝트 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706208"
---
# <a name="projects"></a>프로젝트
Visual Studio에서 프로젝트는 개발자가 소스 코드 파일 및 **솔루션 탐색기**에 표시 되는 기타 리소스를 구성 하는 데 사용 하는 컨테이너입니다. 일반적으로 프로젝트는 소스 코드 파일에 대 한 참조 및 비트맵 파일 같은 리소스에 대 한 참조를 저장 하는 파일 (예: c # 프로젝트용 .csproj 파일)입니다. 프로젝트를 사용 하 여 소스 코드, 웹 서비스 및 데이터베이스에 대 한 참조 및 기타 리소스를 구성, 빌드, 디버그 및 배포할 수 있습니다. Vspackage는 *프로젝트 형식*, *프로젝트 하위*형식 및 *사용자 지정 도구*와 같은 세 가지 주요 방법으로 Visual Studio 프로젝트 시스템을 확장할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [프로젝트 형식](../../extensibility/internals/project-types.md):

 *프로젝트 형식* 에는 프로그래밍 언어와 같은 새로운 종류의 프로젝트에 대 한 지원이 추가 되었습니다. 예를 들어 Visual Studio에서 지 원하는 각 언어에는 고유한 프로젝트 형식이 있고 IronPython 통합 샘플에는 IronPython 언어의 프로젝트 형식이 포함 되어 있습니다. 항목을 빌드, 디버그, 배포 및 **솔루션 탐색기**에 표시 하는 방법을 사용자 지정 하려면 c # 또는 Visual Basic 이외의 언어에 대 한 프로젝트 형식을 만들어야 합니다. 자세한 내용은 [프로젝트 형식](../../extensibility/internals/project-types.md)을 참조 하세요.

- [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)

 *프로젝트 하위* 유형은 프로젝트 유형을 기반으로 하며, 프로젝트를 빌드, 디버깅 및 배포 하는 방법을 사용자 지정 하는 데 사용할 수 있습니다. Visual Studio는 스마트 장치 프로젝트에 프로젝트 하위 유형을 사용 합니다. 개발 컴퓨터에서 대상 장치로 새로 빌드된 프로그램을 복사 하 여 배포를 사용자 지정 합니다. C # 및 Visual Basic 프로젝트 형식을 프로젝트 하위 형식에 대 한 기준으로 사용할 수 있습니다. C + + 프로젝트 형식은 사용할 수 없습니다. 프로젝트 형식에 대 한 기본으로 사용할 수도 있습니다. 자세한 내용은 [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)을 참조 하세요.

- [웹 프로젝트](../../extensibility/internals/web-projects.md)

 웹 응용 프로그램을 만드는 웹 프로젝트에 대해 설명 합니다.

- [새 프로젝트 생성:](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) 내부, 1 부 및 [새 프로젝트 생성: 내부에서 2 부](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)

 새 프로젝트를 만들 때 실제로 발생 하는 상황을 설명 합니다.

- 가 나 [진한 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples) 프로젝트 및 솔루션을 처리 하는 고의 샘플을 포함 합니다.

## <a name="related-sections"></a>관련 섹션
- [Visual Studio SDK 기본 사항](../../extensibility/internals/inside-the-visual-studio-sdk.md)

 Visual Studio 확장성의 다양 한 측면을 설명 합니다.
