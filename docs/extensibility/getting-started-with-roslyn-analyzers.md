---
title: 로슬린 분석기 시작하기 | 마이크로 소프트 문서
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711268"
---
# <a name="get-started-with-roslyn-analyzers"></a>로슬린 분석기 시작

Visual Studio의 라이브 프로젝트 기반 코드 분석기를 사용하면 API 작성자는 NuGet 패키지의 일부로 도메인별 코드 분석을 제공할 수 있습니다. 이러한 분석기는 .NET 컴파일러 플랫폼(코드명 "Roslyn")에 의해 구동되므로 줄을 완료하기 전에 입력할 때 코드에 경고를 생성할 수 있습니다(문제를 발견하기 위해 코드를 빌드할 때까지 더 이상 기다리지 않아도 됨). 분석기는 Visual Studio 전구 프롬프트를 통해 자동 코드 수정을 표시하여 코드를 즉시 정리할 수도 있습니다.

## <a name="get-started"></a>시작하기

[로슬린 분석기 개요](../code-quality/roslyn-analyzers-overview.md)

[자습서: 첫 번째 분석기 및 코드 수정 사항 작성](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[코드 수정 연습 추가: 분석기 문제에 대한 사용자 수정 사항 제공](https://msdn.microsoft.com/magazine/dn904670.aspx)

당신이 또한 [이야기로](https://channel9.msdn.com/events/Build/2015/3-725) 볼 수있는 [실제 세계 Roslyn 분석기](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)

[GitHub의 몇 가지 예는 세 가지 종류의 분석기로 그룹화되었습니다.](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>참조

- [.NET 컴파일러 플랫폼 패키지 버전 참조](roslyn-version-support.md)
- [GitHub OSS 사이트에 대한 더 많은 문서](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Roslyn 분석기로 구현된 FxCop 규칙](../code-quality/fxcop-rule-port-status.md)
