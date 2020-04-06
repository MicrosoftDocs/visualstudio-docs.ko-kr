---
title: 디버거 구성 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03c400fd03c5ee0f2629e9f436b65f53f8f2ac8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739014"
---
# <a name="debugger-components"></a>디버거 구성 요소
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버거는 VSPackage로 구현되며 전체 디버그 세션을 관리합니다. 디버그 세션은 다음과 같은 요소로 구성됩니다.

- **디버그 패키지:** 디버거는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버깅되는 내용에 관계없이 동일한 사용자 인터페이스를 제공합니다.

- **세션 디버그 관리자(SDM):** 다양한 디버그 엔진을 관리하기 위해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버거에 일관된 프로그래밍 인터페이스를 제공합니다. 에 의해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]구현됩니다.

- **프로세스 디버그 관리자(PDM):** 실행 중인 모든 인스턴스에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]대해 디버깅할 수 있거나 디버깅중인 모든 프로그램 목록을 관리합니다. 에 의해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]구현됩니다.

- **디버그 엔진 (DE):** 디버깅되는 프로그램을 모니터링하고, 실행 중인 프로그램의 상태를 SDM 및 PDM에 전달하고, 식 평가기 및 기호 공급자와 상호 작용하여 프로그램의 메모리 및 변수 상태를 실시간으로 분석합니다. 자신의 실행 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 시간을 지원하려는 타사 공급업체와 지원 언어에 대해 구현됩니다.

- **식 계산기(EE):** 프로그램이 특정 지점에서 중지되었을 때 사용자가 제공한 변수 및 식을 동적으로 평가할 수 있는 지원을 제공합니다. 해당 언어는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 지원되는 언어와 해당 언어를 지원하려는 타사 공급업체에 의해 구현됩니다.

- **심볼 공급자(SP):** 심볼 처리기라고도 하는 프로그램의 디버깅 기호를 프로그램의 실행 중인 인스턴스에 매핑하여 의미 있는 정보를 제공할 수 있습니다(예: 소스 코드 수준 디버깅 및 식 평가). 공용 언어 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 런타임 [CLR] 기호 및 프로그램 DataBase [PDB] 기호 파일 형식)과 디버깅 정보를 저장하는 독자적인 방법을 가진 타사 공급업체에 의해 구현됩니다.

  다음 다이어그램은 Visual Studio 디버거의 이러한 요소 간의 관계를 보여 주며 있습니다.

  ![구성 요소 개요 디버깅](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>섹션 내용
 [디버그 패키지](../../extensibility/debugger/debug-package.md) 셸에서 실행되고 모든 UI를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 처리하는 디버그 패키지에 대해 설명합니다.

 [프로세스 디버그 관리자](../../extensibility/debugger/process-debug-manager.md) 디버깅할 수 있는 프로세스의 관리자인 PDM의 기능에 대한 개요를 제공합니다.

 [세션 디버그 관리자](../../extensibility/debugger/session-debug-manager.md) IDE에 디버그 세션의 통합보기를 제공하는 SDM을 정의합니다. SDM은 DE를 관리합니다.

 [디버그 엔진](../../extensibility/debugger/debug-engine.md) DE가 제공하는 디버깅 서비스를 문서화합니다.

 [작동 모드](../../extensibility/debugger/operational-modes.md) IDE가 작동할 수 있는 세 가지 모드(디자인 모드, 실행 모드 및 중단 모드)에 대한 개요를 제공합니다. 전환 메커니즘도 설명합니다.

 [식 계산기](../../extensibility/debugger/expression-evaluator.md) 런타임에 EE의 목적을 설명합니다.

 [기호 공급자](../../extensibility/debugger/symbol-provider.md) 구현 시 기호 공급자가 변수 및 식을 평가하는 방법에 대해 설명합니다.

 [시각화 도우미 및 사용자 지정 뷰어 유형](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) 형식 시각화 도우미 및 사용자 지정 뷰어가 무엇이며 식 계산기가 둘 다 지원에서 수행하는 역할에 대해 설명합니다.

## <a name="related-sections"></a>관련 단원
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md) 주요 디버깅 아키텍처 개념에 대해 설명합니다.

 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md) DE가 코드, 설명서 및 식 평가 컨텍스트 내에서 동시에 작동하는 방법을 설명합니다. 세 가지 컨텍스트 각각에 대해 해당 컨텍스트와 관련된 위치, 위치 또는 평가에 대해 설명합니다.

 [디버그 작업](../../extensibility/debugger/debugging-tasks.md) 프로그램 실행 및 식 평가와 같은 다양한 디버깅 작업에 대한 링크가 포함되어 있습니다.

## <a name="see-also"></a>참조
- [시작](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
