---
title: 디버깅을 위한 언어 서비스 지원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c80e8e1f584b1728f342cb596b689f6a22c9297
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707432"
---
# <a name="language-service-support-for-debugging"></a>디버깅에 대한 언어 서비스 지원
언어 서비스는 인터페이스를 통해 디버거를 지원하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> 기능을 제공할 수 있습니다. 이러한 기능에는 중단점의 유효성을 검사하고 자동 창에 표현식 목록을 제공하는 것이 **포함됩니다.**

 그러나 언어를 디버깅하려면 식 계산자가 있어야 합니다. 식 계산기는 디버깅하는 동안 값을 생성하는 식을 평가합니다. CLR 식 평가기 구현에 대한 자세한 내용은 다음을 참조하십시오.

- [CLR 표현식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [관리식 평가기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>컴파일러 출력
 컴파일러 유형에 따라 언어에 대한 디버깅을 구현하기 위해 수행해야 하는 작업을 결정합니다. 컴파일러가 Windows 운영 체제를 대상으로 하고 .pdb 파일을 작성하는 경우 Visual Studio에 통합된 기본 코드 디버깅 엔진으로 프로그램을 디버깅할 수 있습니다. 컴파일러가 MsIL(Microsoft 중간 언어)을 생성하는 경우 Visual Studio에 통합된 관리되는 코드 디버깅 엔진을 통해 프로그램을 디버깅할 수 있습니다. 컴파일러가 독점 운영 체제 또는 다른 런타임 환경을 대상으로 하는 경우 고유한 디버깅 엔진을 작성해야 합니다.

 언어에 대한 디버깅 구현에 대한 자세한 내용은 Visual Studio 디버깅 SDK에서 [시작하기](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) 를 참조하십시오.
