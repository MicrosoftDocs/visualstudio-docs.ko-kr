---
title: 디버거 컨텍스트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56825fe299147e60c5ed9dfcefa491a427ab59e4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738967"
---
# <a name="debugger-contexts"></a>디버거 컨텍스트
디버깅에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DE(디버그 엔진)는 다음과 같이 여러 가지 고유한 컨텍스트 내에서 동시에 작동합니다.

- 프로그램의 실행 스트림에서 현재 위치를 설명하는 코드 컨텍스트입니다.

- 원본 문서 내의 현재 위치를 설명하는 문서 컨텍스트 또는 위치입니다.

- 식 평가가 수행되는 컨텍스트를 설명하는 식 평가 컨텍스트입니다.

## <a name="in-this-section"></a>섹션 내용
 [코드 컨텍스트](../../extensibility/debugger/code-context.md) 코드 컨텍스트는 오늘날의 런타임 아키텍처와 코드가 지침으로 표현되지 않을 수 있는 비전통적인 언어의 프로그램 명령 스트림에서 주소로 설명합니다.

 [문서 위치](../../extensibility/debugger/document-position.md) Visual Studio 디버깅에서 IDE에 알려진 소스 파일의 위치를 추상화하여 문서 위치를 정의합니다.

 [문서 컨텍스트](../../extensibility/debugger/document-context.md) 소스 파일과 관련하여 Visual Studio 디버깅에서 나타내는 문서 컨텍스트에 대해 설명합니다. 또한 기호 처리기가 코드 컨텍스트를 문서 컨텍스트에 매핑하는 방법에 대해서도 설명합니다.

 [식 평가 컨텍스트](../../extensibility/debugger/expression-evaluation-context.md) Visual Studio에서 식 평가 컨텍스트에 대한 정보를 제공합니다. 예를 들어 스택 프레임과 연결된 식 평가 컨텍스트는 지역 변수, 메서드 매개 변수 및 클래스 멤버를 평가하기 위한 컨텍스트를 제공합니다.

## <a name="related-sections"></a>관련 단원
 [디버그 개념](../../extensibility/debugger/debugger-concepts.md) 주요 디버깅 아키텍처 개념에 대해 설명합니다.

 [구성 요소 디버그](../../extensibility/debugger/debugger-components.md) 디버그 엔진(DE), 식 계산기(EE) 및 기호 처리기(SH)를 포함하는 Visual Studio 디버깅 구성 요소에 대한 개요를 제공합니다.

 [디버그 작업](../../extensibility/debugger/debugging-tasks.md) 프로그램 실행 및 식 평가와 같은 다양한 디버깅 작업에 대한 링크가 포함되어 있습니다.
