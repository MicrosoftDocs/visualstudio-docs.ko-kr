---
title: 로슬린 분석기 시작하기 | 마이크로 소프트 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444984"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Roslyn 분석기 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 라이브 프로젝트 기반 코드 분석기를 사용하면 API 작성자는 NuGet 패키지의 일부로 도메인별 코드 분석을 제공할 수 있습니다.  이러한 분석기는 .NET 컴파일러 플랫폼(코드명 "Roslyn")에 의해 구동되므로 줄을 완료하기 전에 입력할 때 코드에 경고를 생성할 수 있습니다(문제를 발견하기 위해 코드를 빌드할 때까지 더 이상 기다리지 않아도 됨).  분석기는 Visual Studio 전구 프롬프트를 통해 자동 코드 수정을 표시하여 코드를 즉시 정리할 수 있습니다.

## <a name="getting-started"></a>시작하기
[Roslyn 라이브 코드 분석기 소개 및 연습](https://msdn.microsoft.com/magazine/dn879356.aspx)

[코드 수정 연습 추가: 분석기 문제에 대한 사용자 수정 사항 제공](https://msdn.microsoft.com/magazine/dn904670.aspx)

[실제 분석기 토크 소개 및 연습](https://channel9.msdn.com/events/Build/2015/3-725)

당신이 또한 [이야기로](https://channel9.msdn.com/events/Build/2015/3-725) 볼 수있는 [실제 세계 로슬린 분석기](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)

[GitHub의 몇 가지 예는 세 가지 종류의 분석기로 그룹화되었습니다.](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[몇 가지 분석기 토크 소개 및 투어](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>관련 자료
[GitHub OSS 사이트에 대한 더 많은 문서](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[GitHub에 로슬린 분석기와 구현 FxCop 규칙](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
