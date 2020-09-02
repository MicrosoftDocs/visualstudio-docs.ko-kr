---
title: .NET Compiler Platform ( &quot; Roslyn &quot; ) 확장성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fba277731444a294f276f43cc67b098039f4a64f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204725"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET 컴파일러 플랫폼(&quot;Roslyn&quot;) 확장성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET Compiler Platform ("Roslyn")의 핵심 임무는 c # 및 Visual Basic 컴파일러를 열고 도구와 개발자가 프로그램에 대 한 풍부한 정보를 공유 하도록 합니다. 코드 분석 도구는 코드 품질을 향상 시키고 코드 생성기는 응용 프로그램 생성을 지원 합니다. 도구는 더 효율적으로 사용할 수 있으므로 컴파일러에만 있는 심층 코드 기술 자료에 대 한 액세스 권한이 필요 합니다. Roslyn 컴파일러는 불투명 한 변환기 (의 소스 코드 및 개체 코드 출력) 대신 도구 및 응용 프로그램에서 코드 관련 작업에 사용할 수 있는 Api를 제공 합니다.  
  
 가장 좋은 부분은 Roslyn 컴파일러, 해당 Api, 샘플 및 연습, 그리고 이러한 Api를 기반으로 구축 된 실제 도구는 모두 [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)에 완전히 오픈 소스입니다. 자세한 내용을 알아보고 Roslyn을 시작 하려면 OSS 사이트로 이동 하세요. 최종 사용자로 사용할 수 있는 최신 c # 및 VB 기능 뿐만 아니라 Roslyn Api를 활용 하는 도구 작성기로 시작 하는 링크를 찾을 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Roslyn 분석기 시작](../extensibility/getting-started-with-roslyn-analyzers.md)
