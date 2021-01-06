---
title: 프로젝트 형식 아키텍처 | Microsoft Docs
description: 이 문서는 Visual Studio에서 프로젝트 형식의 아키텍처에 대 한 자세한 정보를 포함 하는 문서에 연결 됩니다.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ecde348ce52bdd354df61855d9907acf85900be2
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877782"
---
# <a name="project-types-architecture"></a>프로젝트 형식 아키텍처
이 섹션에는의 프로젝트 형식 아키텍처에 대 한 자세한 정보가 포함 되어 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>섹션 내용
- [프로젝트 모델의 요소](../../extensibility/internals/elements-of-a-project-model.md)

 프로젝트 형식에서 사용할 수 있는 서비스와이 서비스에서 구현 해야 하는 인터페이스를 나열 합니다.

- [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)

 구현 해야 하는 프로젝트 형식에 대해 설명 하 고 선택적으로을 구현 하 여 추가 기능을 제공 합니다.

- [프로젝트 형식을 만들어야 하는 경우](../../extensibility/internals/when-to-create-project-types.md)

 프로젝트 형식을 만들어야 하는 경우와 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vspackage 및 편집기와 같은 다른 확장성 기능을 사용 하 여 동일한 목표를 달성할 수 있는 경우를 결정할 수 있습니다.

- [계층 구조 및 선택](../../extensibility/internals/hierarchies-and-selection.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에서 계층 및 선택 컨텍스트를 사용 하 여 일관적이 고 간소화 된 사용자 환경을 제공 하는 방법을 설명 합니다.

## <a name="related-sections"></a>관련 단원
- [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)

 프로젝트 하위 유형을 사용 하 여 및의 프로젝트 시스템 동작을 사용자 지정 하는 방법을 설명 합니다 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

- [프로젝트 형식](../../extensibility/internals/project-types.md):

 IDE (통합 개발 환경)의 기본 구성 요소로 프로젝트 개요를 제공 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다. 프로젝트에서 코드 빌드 및 컴파일을 제어 하는 방법을 설명 하는 추가 항목에 대 한 링크가 제공 됩니다.
