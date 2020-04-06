---
title: .NET 컴파일러&quot;플랫폼&quot;(로슬린) 확장성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712069"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET 컴파일러&quot;플랫폼&quot;(로슬린) 확장성
.NET 컴파일러 플랫폼("Roslyn")의 핵심 임무는 C# 및 Visual Basic 컴파일러를 열고 도구와 개발자가 프로그램에 대한 풍부한 정보 컴파일러에서 공유할 수 있도록 하는 것입니다. 코드 분석 도구는 코드 품질을 향상시키고 코드 생성기는 응용 프로그램 생성에 도움이 됩니다. 도구가 더욱 스마트해짐에 따라 컴파일러만 보유한 심층적인 코드 지식에 점점 더 많이 액세스해야 합니다. Roslyn 컴파일러에서는 불투명 한 번역기(소스 코드 및 개체 코드 아웃)가 아니라 도구 및 응용 프로그램에서 코드 관련 작업에 사용할 수 있는 API를 제공합니다.

 가장 좋은 점은 Roslyn 컴파일러, API, 샘플 및 연습 및 이러한 API 위에 구축된 실제 도구가 모두 [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)완전히 오픈 소스라는 것입니다. OSS 사이트로 이동하여 자세한 내용을 알아보고 Roslyn을 시작하십시오. 최종 사용자로 사용할 수 있는 최신 C# 및 Visual Basic 기능을 얻을 수 있는 링크와 Roslyn API를 활용하는 도구 빌더로 시작하는 링크를 찾을 수 있습니다.

## <a name="see-also"></a>참조
- [로슬린 분석기 시작](../extensibility/getting-started-with-roslyn-analyzers.md)
