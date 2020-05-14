---
title: 소스 제어 통합 필수 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e56658d644720f1563d71d3d08bf35268119112f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705242"
---
# <a name="source-control-integration-essentials"></a>소스 제어 통합 필수 항목
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]소스 제어 통합의 두 가지 유형을 지원합니다: 기본 기능을 제공하고 소스 제어 플러그인 API(이전의 MSSCCI API)를 사용하여 빌드되는 소스 제어 플러그인과 보다 강력한 기능을 제공하는 VSPackage 기반 소스 제어 통합 솔루션을 지원합니다.

## <a name="source-control-plug-in"></a>소스 제어 플러그인
 소스 제어 플러그인은 소스 제어 플러그인 API를 구현하는 DLL로 작성됩니다. 등록 및 소스 제어 통합 기능은 API를 통해 제공됩니다. 이 방법은 소스 제어 VSPackage보다 구현하기가 더 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 쉬우며 대부분의 소스 제어 작업에 는 사용자 인터페이스(UI)를 사용합니다.

 소스 제어 플러그인 API를 사용하여 소스 제어 플러그인을 구현하려면 다음 단계를 따르십시오.

1. [소스 제어 플러그인에](../../extensibility/source-control-plug-ins.md)지정된 함수를 구현하는 DLL을 만듭니다.

2. 소스 제어 플러그인 설치 방법: 에 설명된 대로 적절한 레지스트리 항목을 만들어 [DLL을 등록합니다.](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)

3. 도우미 UI를 만들고 소스 제어 어댑터 패키지(소스 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제어 플러그인을 통해 소스 제어 기능을 처리하는 구성 요소)에 의해 메시지가 표시될 때 도우미 UI를 표시합니다.

   자세한 내용은 [소스 제어 플러그인 만들기를](../../extensibility/internals/creating-a-source-control-plug-in.md)참조하십시오.

## <a name="source-control-vspackage"></a>소스 제어 VS패키지
 소스 제어 VSPackage 구현을 사용하면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 제어 UI에 대한 사용자 지정 대체 를 개발할 수 있습니다. 이 방법은 소스 제어 통합을 완벽하게 제어하지만 UI 요소를 제공하고 플러그인 접근 방식에서 제공하는 소스 제어 인터페이스를 구현해야 합니다.

 소스 제어 VSPackage를 구현하려면 다음을 수행해야 합니다.

1. 등록 및 [선택에서](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)설명한 대로 고유한 소스 제어 VSPackage를 만들고 등록합니다.

2. 기본 소스 제어 UI를 사용자 지정 UI로 바꿉습니다. [사용자 지정 사용자 인터페이스](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)를 참조하십시오.

3. 사용할 글리프를 지정하고 솔루션 **탐색기** 글리프 이벤트를 처리합니다. [글리프 컨트롤](../../extensibility/internals/glyph-control-source-control-vspackage.md)을 참조하십시오.

4. 쿼리 편집 및 쿼리 저장 이벤트에 표시된 것처럼 [쿼리](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)편집 및 쿼리 저장 이벤트를 처리합니다.

   자세한 내용은 [소스 제어 VSPackage 만들기를](../../extensibility/internals/creating-a-source-control-vspackage.md)참조하십시오.

## <a name="see-also"></a>참조
- [개요](../../extensibility/internals/source-control-integration-overview.md)
- [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [소스 제어 VSPackage 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md)
