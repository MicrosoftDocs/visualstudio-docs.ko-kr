---
title: Roslyn 분석기 시작 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444984"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Roslyn 분석기 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 라이브 프로젝트 기반 코드 분석기를 사용 하면 API 작성자는 도메인 특정 코드 분석을 NuGet 패키지의 일부로 제공할 수 있습니다.  이러한 분석기는 .NET Compiler Platform (코드 이름 "Roslyn")을 기반으로 하기 때문에 줄을 완료 하기 전에 입력 하는 코드에서 경고를 생성할 수 있습니다 (문제를 검색 하기 위해 코드를 작성 하기 위해 대기 하지 않음).  분석기는 코드를 즉시 정리할 수 있도록 Visual Studio 전구 프롬프트를 통해 자동 코드 수정 사항을 표시할 수도 있습니다.

## <a name="getting-started"></a>시작하기
[Roslyn 라이브 코드 분석기 소개 및 연습](https://msdn.microsoft.com/magazine/dn879356.aspx)

[코드 수정 추가 연습: 분석기 문제에 대 한 사용자 수정 제공](https://msdn.microsoft.com/magazine/dn904670.aspx)

[실제 분석기의 소개 및 연습](https://channel9.msdn.com/events/Build/2015/3-725)

Roslyn으로 시청할 수 있는 [실제 세계](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) [의](https://channel9.msdn.com/events/Build/2015/3-725) 분석기

[GitHub에 대 한 몇 가지 예제는 세 가지 분석기로 그룹화 되어 있습니다.](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[몇 가지 분석기의 소개 및 둘러보기](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>기타 리소스
[GitHub OSS 사이트의 추가 문서](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[GitHub에서 Roslyn 분석기를 사용 하 여 구현 된 FxCop 규칙](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
