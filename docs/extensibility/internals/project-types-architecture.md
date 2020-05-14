---
title: 프로젝트 유형 아키텍처 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e53929b1ec2ed9c73191bf16f1cedc84a53b58f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706315"
---
# <a name="project-types-architecture"></a>프로젝트 형식 아키텍처
이 섹션에는 의 프로젝트 유형 아키텍처에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]대한 자세한 정보가 포함되어 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md)

 프로젝트 유형이 사용할 수 있는 서비스와 구현해야 하는 인터페이스를 나열합니다.

- [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)

 프로젝트 형식이 구현해야 하는 인터페이스와 추가 기능을 제공하기 위해 선택적으로 구현할 수 있는 인터페이스에 대해 설명합니다.

- [프로젝트 형식을 만들어야 하는 경우](../../extensibility/internals/when-to-create-project-types.md)

 프로젝트 유형을 만들어야 하는 시기와 VSPackage 및 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 편집기와 같은 다른 확장성 기능을 사용하여 동일한 목표를 달성할 수 있는 시기를 결정하는 데 도움이 됩니다.

- [계층 구조 및 선택](../../extensibility/internals/hierarchies-and-selection.md)

 계층 구조 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 및 선택 컨텍스트를 사용하여 일관되고 간소화된 사용자 환경을 제공하는 방법을 설명합니다.

## <a name="related-sections"></a>관련 단원
- [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)

 프로젝트 하위 유형을 통해 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 및 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]의 프로젝트 시스템의 동작을 사용자 지정할 수 있는 방법을 설명합니다.

- [프로젝트 유형](../../extensibility/internals/project-types.md)

 통합 개발 환경(IDE)의 기본 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 구성 요소로서 프로젝트의 개요를 제공합니다. 프로젝트가 빌드 및 컴파일 코드를 제어하는 방법을 설명하는 추가 항목에 대한 링크가 제공됩니다.
