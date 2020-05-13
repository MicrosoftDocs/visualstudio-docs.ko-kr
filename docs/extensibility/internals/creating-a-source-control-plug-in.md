---
title: 소스 제어 플러그인 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e0d9dc54a61cabe7bdd5c21c10abf0def34ff6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709177"
---
# <a name="create-a-source-control-plug-in"></a>소스 제어 플러그인 만들기
Visual Studio SDK는 통합 개발 환경(IDE)에 소스 제어 기능을 추가할 수 있는 리소스를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제공합니다. 이 문서에서 설명하는 소스 제어 플러그인 API를 준수하는 모든 플러그인 DLL을 사용할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [시작](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)

 소스 제어 플러그인을 설치하는 방법을 설명하고 현재 사용 가능한 소스 제어 플러그인 API 버전을 강조 합니다.

- [Architecture](../../extensibility/internals/source-control-plug-in-architecture.md)

 아키텍처 다이어그램을 사용하여 소스 제어 플러그인과 IDE의 통합을 설명합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

- [테스트 가이드](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

 소스 제어 플러그인의 설치 및 작동을 테스트하는 방법에 대한 지침을 제공합니다.

## <a name="related-sections"></a>관련 단원
- [소스 제어 VS패키지 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md)

 소스 제어 기능을 제공 하지만 소스 제어 UI를 대체 하는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 제어 VSPackage를 만드는 방법에 대해 설명 합니다.

- [소스 제어 플러그인](../../extensibility/source-control-plug-ins.md)

 소스 제어 플러그인 API의 모든 요소에 대한 전체 목록을 제공합니다.

- [소스 제어](../../extensibility/internals/source-control.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]의 통합 기능으로 소스 제어를 구현하기 위한 옵션에 대해 설명합니다.
