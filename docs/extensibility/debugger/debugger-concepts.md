---
title: 디버거 개념 | Microsoft Docs
description: 해당 패키지를 빌드하는 데 도움이 되는 Visual Studio 디버그 패키지를 디자인 하는 데 사용 되는 아키텍처 개념에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5202ebdb621121e63adbdf5118cb0848689adde6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952410"
---
# <a name="debugger-concepts"></a>디버거 개념
Visual Studio 디버그 패키지를 빌드하려면 패키지를 디자인 하는 데 사용 되는 아키텍처 개념에 대해 잘 알고 있어야 합니다.

## <a name="in-this-section"></a>단원 내용
 [디버그 세션](../../extensibility/debugger/debug-session.md) 디버깅 아키텍처에서 세션의 역할을 설명 합니다.

 [서버](../../extensibility/debugger/servers-visual-studio-sdk.md) 디버깅 아키텍처 측면에서 서버를 추상 및 물리적 용어로 정의 합니다.

 [포트 공급자](../../extensibility/debugger/port-suppliers.md) 디버깅 아키텍처 측면에서 포트 공급자를 정의 합니다.

 [포트](../../extensibility/debugger/ports.md) 디버깅 아키텍처 측면에서 포트의 정의를 정의 합니다.

 [프로세스](../../extensibility/debugger/processes.md) 디버깅 아키텍처 측면에서 프로세스를 정의 합니다.

 [프로그램 노드](../../extensibility/debugger/program-nodes.md) 디버깅 아키텍처와 관련 하 여 프로그램 노드를 정의 합니다 .이 노드는 자체를 식별 하는 방법 및 실행 중인 프로세스를 포함 합니다.

 [프로그램](../../extensibility/debugger/programs.md) 디버깅 아키텍처 측면에서 프로그램을 정의 합니다.

 [스레드](../../extensibility/debugger/threads.md) 디버깅 아키텍처 측면에서 스레드의 특성을 정의 합니다.

 [스택 프레임](../../extensibility/debugger/stack-frames.md) 디버깅 아키텍처 측면에서 스택 프레임을 정의 합니다. 스택 프레임은 스레드의 실행 컨텍스트를 제공 하는 스택을 추상화 한 것입니다.

 [모듈](../../extensibility/debugger/modules.md) 디버깅 아키텍처와 관련 하 여 실행 파일이 나 DLL과 같은 물리적 코드 컨테이너로 모듈을 정의 합니다.

 [중단점](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) 디버깅 아키텍처 측면에서 세 가지 유형의 중단점 (보류 중, 바인딩 및 오류)을 정의 합니다.

## <a name="related-sections"></a>관련 단원
 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md) 디버그 엔진 (DE)이 코드, 설명서 및 식 계산 컨텍스트 내에서 동시에 작동 하는 방법을 설명 합니다. 세 가지 컨텍스트, 위치 또는 관련 계산에 관해 설명합니다.

 [디버거 구성 요소](../../extensibility/debugger/debugger-components.md) 디버그 엔진 (DE), 식 계산기 (EE) 및 기호 처리기 (SH)를 포함 하는 Visual Studio 디버깅 구성 요소에 대 한 개요를 제공 합니다.

 [디버그 작업](../../extensibility/debugger/debugging-tasks.md) 프로그램 시작 및 식 계산과 같은 다양 한 디버깅 태스크에 대 한 링크를 포함 합니다.
