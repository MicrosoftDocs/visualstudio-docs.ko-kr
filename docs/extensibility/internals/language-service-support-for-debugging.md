---
title: 디버깅을 위한 언어 서비스 지원 | Microsoft Docs
description: Visual Studio에서 디버깅에 대 한 지원을 제공 하는 IVsLanguageDebugInfo 인터페이스의 언어 서비스 기능에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b53eb738b695726cf86859ce83a8ee93440564a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839705"
---
# <a name="language-service-support-for-debugging"></a>디버깅에 대한 언어 서비스 지원
언어 서비스는 인터페이스를 통해 디버거를 지 원하는 기능을 제공할 수 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> . 이러한 기능에는 중단점 유효성 검사 및 **자동** 창에 식 목록 제공이 포함 됩니다.

 그러나 언어를 디버그 하려면 식 계산기가 있어야 합니다. 식 계산기는 디버깅 하는 동안 값을 생성 하는 식을 계산 합니다. CLR 식 계산기를 구현 하는 방법에 대 한 자세한 내용은 다음을 참조 하세요.

- [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>컴파일러 출력
 컴파일러의 형식에 따라 언어에 대 한 디버깅을 구현 하기 위해 수행 해야 하는 작업이 결정 됩니다. 컴파일러가 Windows 운영 체제를 대상으로 하 고 .pdb 파일을 작성 하는 경우 Visual Studio에 통합 된 네이티브 코드 디버깅 엔진을 사용 하 여 프로그램을 디버그할 수 있습니다. 컴파일러가 MSIL (Microsoft 중간 언어)을 생성 하는 경우 Visual Studio에 통합 된 관리 되는 코드 디버깅 엔진을 사용 하 여 프로그램을 디버그할 수 있습니다. 컴파일러가 독점 운영 체제 또는 다른 런타임 환경을 대상으로 하는 경우에는 사용자 고유의 디버깅 엔진을 작성 해야 합니다.

 해당 언어에 대 한 디버깅을 구현 하는 방법에 대 한 자세한 내용은 Visual Studio 디버깅 SDK에서 [시작](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) 을 참조 하세요.
