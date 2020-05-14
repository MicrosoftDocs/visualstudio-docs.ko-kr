---
title: 옵션 대화 상자, 프로젝트, VB 기본값
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f33dd9b19297811597be406337d70392904e6e44
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596387"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>옵션 대화 상자, 프로젝트, VB 기본값
Visual Basic 프로젝트 옵션에 대한 기본 설정을 지정합니다. 새 프로젝트를 만든 경우 지정된 옵션 문이 코드 편집기의 프로젝트 헤더에 추가됩니다. 이 옵션은 모든 Visual Basic 프로젝트에 적용됩니다.

이 대화 상자에 액세스하려면 **도구** 메뉴에서 **옵션**을 클릭하고 **프로젝트 및 솔루션**을 확장한 후 **VB 기본값**을 클릭합니다.

 **Option Explicit**

변수의 명시적 선언이 필요하도록 컴파일러 기본값을 설정합니다. 기본적으로 **Option Explicit**은 **On**으로 설정됩니다. 자세한 내용은 [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit)을 참조하세요.

 **Option Strict**

명시적 축소 변환이 필요하고 런타임에 바인딩이 허용되지 않도록 컴파일러 기본값을 설정합니다. 기본적으로 **Option Strict**은 **해제**로 설정됩니다. 자세한 내용은 [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict)을 참조하세요.

 **Option Compare**

문자열 비교를 위한 컴파일러 기본값을 이진(대/소문자 구분) 또는 텍스트(대/소문자 구분 안 함)로 설정합니다. 기본적으로 **Option Compare**는 **Binary**로 설정됩니다. 자세한 내용은 [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare)를 참조하세요.

 **Option Infer**

지역 형식 유추를 위한 컴파일러 기본값을 설정합니다. 기본적으로 새로 만든 프로젝트에 대해서는 **Option Infer**가 **설정**으로 설정되고 이전 버전의 Visual Basic에서 만든 마이그레이션된 프로젝트에 대해서는 **Off**로 설정됩니다. 자세한 내용은 [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer)를 참조하세요.

## <a name="see-also"></a>참조

- [솔루션 및 프로젝트](../../ide/solutions-and-projects-in-visual-studio.md)
