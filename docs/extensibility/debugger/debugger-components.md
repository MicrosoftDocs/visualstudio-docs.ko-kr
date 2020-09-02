---
title: 디버거 구성 요소 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739014"
---
# <a name="debugger-components"></a>디버거 구성 요소
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버거는 VSPackage으로 구현 되 고 전체 디버그 세션을 관리 합니다. 디버그 세션은 다음 요소로 구성 됩니다.

- **디버그 패키지:** [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 디버거는 디버깅 대상에 관계 없이 동일한 사용자 인터페이스를 제공 합니다.

- **세션 디버그 관리자 (SDM):** 는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다양 한 디버그 엔진을 관리 하기 위해 디버거에 일관 된 프로그래밍 인터페이스를 제공 합니다. 이는에 의해 구현 됩니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **프로세스 디버그 관리자 (PDM):** 실행 중인 모든 인스턴스에 대해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 또는 디버그할 수 있는 모든 프로그램의 목록을 관리 합니다. 이는에 의해 구현 됩니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- **디버그 엔진 (DE):** 는 디버깅 중인 프로그램을 모니터링 하 고, 실행 중인 프로그램의 상태를 SDM 및 PDM으로 통신 하 고, 식 계산기 및 기호 공급자와 상호 작용 하 여 프로그램의 메모리 및 변수의 상태를 실시간으로 분석할 수 있도록 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](지원 되는 언어의 경우) 및 자체 실행 시간을 지원 하려는 타사 공급 업체에 의해 구현 됩니다.

- **식 계산기 (EE):** 프로그램이 특정 지점에서 중지 될 때 사용자가 제공 하는 변수 및 식을 동적으로 평가 하는 기능을 지원 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](지원 되는 언어의 경우) 및 자체 언어를 지원 하려는 타사 공급 업체에 의해 구현 됩니다.

- **기호 공급자 (SP):** 기호 처리기 라고도 하는 프로그램의 디버깅 기호를 프로그램의 실행 중인 인스턴스에 매핑하여 소스 코드 수준 디버깅 및 식 평가와 같은 의미 있는 정보를 제공할 수 있도록 합니다. 이 클래스는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (CLR (공용 언어 런타임) 기호 및 프로그램 데이터베이스 [PDB] 기호 파일 형식) 및 디버깅 정보를 저장 하는 고유한 소유 방법이 있는 타사 공급 업체에 의해 구현 됩니다.

  다음 다이어그램은 Visual Studio 디버거의 이러한 요소 간의 관계를 보여 줍니다.

  ![디버그 구성 요소 개요](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")

## <a name="in-this-section"></a>섹션 내용
 [패키지 디버그](../../extensibility/debugger/debug-package.md) 셸에서 실행 되 고 모든 UI를 처리 하는 디버그 패키지에 대해 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 [프로세스 디버그 관리자](../../extensibility/debugger/process-debug-manager.md) 디버깅할 수 있는 프로세스의 관리자 인 PDM의 기능에 대 한 개요를 제공 합니다.

 [세션 디버그 관리자](../../extensibility/debugger/session-debug-manager.md) IDE에 대 한 디버그 세션의 통합 보기를 제공 하는 SDM을 정의 합니다. SDM은 DE를 관리 합니다.

 [디버그 엔진](../../extensibility/debugger/debug-engine.md) DE에서 제공 하는 디버깅 서비스를 문서화 합니다.

 [운영 모드](../../extensibility/debugger/operational-modes.md) IDE가 작동 하는 세 가지 모드 (디자인 모드, 실행 모드 및 중단 모드)에 대 한 개요를 제공 합니다. 전환 메커니즘에 대해서도 설명 합니다.

 [식 계산기](../../extensibility/debugger/expression-evaluator.md) 런타임에 EE의 용도에 대해 설명 합니다.

 [기호 공급자](../../extensibility/debugger/symbol-provider.md) 구현 시 기호 공급자가 변수와 식을 평가 하는 방법에 대해 설명 합니다.

 [형식 시각화 도우미 및 사용자 지정 뷰어](../../extensibility/debugger/type-visualizer-and-custom-viewer.md) 형식 시각화 도우미 및 사용자 지정 뷰어가 무엇 인지와 식 계산기가 둘 다 지원 하기 위해 수행 하는 역할에 대해 설명 합니다.

## <a name="related-sections"></a>관련 단원
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md) 주요 디버깅 아키텍처 개념을 설명 합니다.

 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md) 코드, 설명서 및 식 계산 컨텍스트 내에서 DE가 동시에 작동 하는 방식을 설명 합니다. 각각의 세 가지 컨텍스트, 위치, 위치 또는 관련 평가에 대해 설명 합니다.

 [디버그 작업](../../extensibility/debugger/debugging-tasks.md) 프로그램 시작 및 식 계산과 같은 다양 한 디버깅 태스크에 대 한 링크를 포함 합니다.

## <a name="see-also"></a>참조
- [시작](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
