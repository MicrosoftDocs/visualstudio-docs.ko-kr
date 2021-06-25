---
title: 디버거 구성 요소 | Microsoft Docs
description: vsPackage로 구현된 Visual Studio 디버거에서 관리되는 디버그 세션을 구성하는 요소에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c246bc00ee4f6fcead8404b3174da39f7b5ca2d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903985"
---
# <a name="debugger-components"></a>디버거 구성 요소
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버거는 VSPackage로 구현되고 전체 디버그 세션을 관리합니다. 디버그 세션은 다음 요소로 구성됩니다.

- **디버그 패키지:** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버거는 디버깅되는 내용에 관계없이 동일한 사용자 인터페이스를 제공합니다.

- **SDM(세션 디버그 관리자):** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다양한 디버그 엔진을 관리하기 위해 디버거에 일관된 프로그래밍 인터페이스를 제공합니다. 에 의해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 구현됩니다.

- **PDM(프로세스 디버그 관리자):** 의 실행 중인 모든 인스턴스에 대해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버그할 수 있거나 디버깅 중인 모든 프로그램의 목록을 관리합니다. 에 의해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 구현됩니다.

- **디버그 엔진(DE):** 디버깅 중인 프로그램을 모니터링하고, 실행 중인 프로그램의 상태를 SDM 및 PDM에 전달하고, 식 계산기 및 기호 공급자와 상호 작용하여 프로그램의 메모리 및 변수 상태에 대한 실시간 분석을 제공합니다. 자체 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 런타임을 지원하려는 (지원하는 언어) 및 타사 공급업체에 의해 구현됩니다.

- **EE(식 계산기):** 프로그램이 특정 지점에서 중지되었을 때 사용자가 제공하는 변수 및 식을 동적으로 평가할 수 있는 지원을 제공합니다. (지원하는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 언어의 경우) 및 자체 언어를 지원하려는 타사 공급업체에 의해 구현됩니다.

- **SP(기호 공급자):** 기호 처리기라고도 하며, 의미 있는 정보(예: 소스 코드 수준 디버깅 및 식 계산)를 제공할 수 있도록 프로그램의 디버깅 기호를 프로그램의 실행 중인 인스턴스에 매핑합니다. 이는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (CLR(공용 언어 런타임) 기호 및 Program DataBase [PDB] 기호 파일 형식의 경우) 및 디버깅 정보를 저장하는 고유한 소유 방법이 있는 타사 공급업체에 의해 구현됩니다.

  다음 다이어그램은 Visual Studio 디버거의 이러한 요소 간의 관계를 보여 주는 다이어그램입니다.

  ![디버깅 구성 요소 개요](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>단원 내용
 [패키지 디버그](../../extensibility/debugger/debug-package.md) 셸에서 실행되고 모든 UI를 처리하는 디버그 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 패키지에 대해 설명합니다.

 [프로세스 디버그 관리자](../../extensibility/debugger/process-debug-manager.md) 디버그할 수 있는 프로세스의 관리자인 PDM의 기능에 대한 개요를 제공합니다.

 [세션 디버그 관리자](../../extensibility/debugger/session-debug-manager.md) IDE에 대한 디버그 세션의 통합 보기를 제공하는 SDM을 정의합니다. SDM은 DE를 관리합니다.

 [디버그 엔진](../../extensibility/debugger/debug-engine.md) DE에서 제공하는 디버깅 서비스를 문서화합니다.

 [작동 모드](../../extensibility/debugger/operational-modes.md) IDE가 작동할 수 있는 세 가지 모드인 디자인 모드, 실행 모드 및 중단 모드에 대한 개요를 제공합니다. 전환 메커니즘도 설명합니다.

 [식 계산기](../../extensibility/debugger/expression-evaluator.md) 런타임에 EE의 용도를 설명합니다.

 [기호 공급자](../../extensibility/debugger/symbol-provider.md) 구현에서 기호 공급자가 변수와 식을 평가하는 방법을 설명합니다.

 [형식 시각화 도우미 및 사용자 지정 뷰어](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) 형식 시각화 도우미와 사용자 지정 뷰어의 정의 및 식 계산기가 둘 다 지원하는 데 수행하는 역할에 대해 설명합니다.

## <a name="related-sections"></a>관련 단원
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md) 기본 디버깅 아키텍처 개념을 설명합니다.

 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md) 코드, 문서 및 식 계산 컨텍스트 내에서 DE가 동시에 작동하는 방식을 설명합니다. 세 가지 컨텍스트, 위치 또는 관련 계산에 관해 설명합니다.

 [디버그 작업](../../extensibility/debugger/debugging-tasks.md) 프로그램 시작 및 식 계산과 같은 다양한 디버깅 작업에 대한 링크를 포함합니다.

## <a name="see-also"></a>추가 정보
- [시작](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
