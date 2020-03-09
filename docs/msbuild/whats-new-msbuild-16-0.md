---
title: MSBuild 16.0의 새로운 기능 | Microsoft Docs
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 69c576f34b73ec99edd231d39e8bfa8ea661f2ff
ms.sourcegitcommit: a80489d216c4316fde2579a0a2d7fdb54478abdf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652809"
---
# <a name="whats-new-in-msbuild-160"></a>MSBuild 16.0의 새로운 기능

이 문서에서는 MSBuild16.0의 업데이트된 기능 및 속성에 대해 설명합니다. 자세한 릴리스 정보는 [ MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831)을 참조하세요.

## <a name="changed-path"></a>변경된 경로

 MSBuild는 각 Visual Studio 버전 아래 *\Current* 폴더에 설치되며, 실행 파일은 *\Bin* 하위 폴더에 있습니다. 예를 들어 Visual Studio 2019 Community와 함께 설치된 *MSBuild.exe* 경로는 *C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe*입니다. PowerShell 모듈 [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell)을 사용하여 MSBuild를 찾을 수도 있습니다.

## <a name="changed-properties"></a>변경된 속성

 다음 MSBuild 속성은 새 버전 번호의 결과로 업데이트되었습니다.

- 이 도구 버전의 `MSBuildToolsVersion`은 “현재”입니다. 어셈블리 버전은 15.1.0.0인 Visual Studio 2017과 동일합니다.

- 이 도구 버전의 `VisualStudioVersion`은 “16.0”입니다.

## <a name="updates"></a>Updates

MSBuild(및 Visual Studio)는 이제 .NET Framework 4.7.2를 대상으로 합니다. 새로운 MSBuild API 기능을 사용하려면 어셈블리도 업그레이드해야 하지만 기존 코드는 계속 작동합니다.

## <a name="see-also"></a>참조

- [MSBuild](../msbuild/msbuild.md)
