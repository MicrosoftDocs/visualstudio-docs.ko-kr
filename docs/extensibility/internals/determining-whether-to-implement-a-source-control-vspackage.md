---
title: 소스 제어 VS패키지 구현 여부 결정 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8707f3c1ced1cc2df9d3ae77280fc8779874a837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708716"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>소스 제어 VSPackage를 구현할지 여부 결정
이 섹션에서는 소스 제어 솔루션을 확장하기 위한 소스 제어 플러그인 및 소스 제어 VSPackage의 선택에 대해 자세히 설명하며 적합한 통합 경로 선택에 대한 광범위한 지침을 제공합니다.

## <a name="small-source-control-solution-with-limited-resources"></a>제한된 리소스를 갖춘 소규모 소스 제어 솔루션
 리소스가 제한되어 있고 소스 제어 패키지를 작성하는 오버헤드에 부담을 주지 않는 경우 소스 제어 플러그인 API 기반 플러그인을 만들 수 있습니다. 자세한 내용은 [등록 및 선택을](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)참조하십시오.

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>풍부한 기능 세트를 갖춘 대형 소스 제어 솔루션
 소스 제어 플러그인 API를 사용하여 적절히 캡처되지 않은 풍부한 소스 제어 모델을 제공하는 소스 제어 솔루션을 구현하려는 경우 소스 제어 패키지를 통합 경로로 간주할 수 있습니다. 이는 소스 제어 어댑터 패키지(소스 제어 플러그인과 통신하고 기본 소스 제어 UI를 제공함)를 사용자 지정 방식으로 소스 제어 이벤트를 처리할 수 있도록 사용자 고유의 로 대체하는 경우에 특히 적용됩니다. 이미 만족스러운 소스 제어 UI가 있고 해당 환경을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]유지하려는 경우 소스 제어 패키지 옵션을 사용하면 이 작업을 수행할 수 있습니다. 소스 제어 패키지는 일반 패키지가 아니며 IDE와 함께 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용하도록만 설계되었습니다.

 소스 제어 논리 및 UI에 대한 유연성과 보다 풍부한 제어를 제공하는 소스 제어 솔루션을 구현하려는 경우 소스 제어 패키지 통합 경로를 선호할 수 있습니다. 다음을 수행할 수 있습니다.

1. 자신의 소스 제어 VSPackage를 등록하십시오(등록 [및 선택](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)참조).

2. 기본 소스 제어 UI를 사용자 지정 UI로 바꿉니다(사용자 [지정 사용자 인터페이스](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)참조).

3. 사용할 글리프를 지정하고 솔루션 탐색기 글리프 이벤트를 [처리합니다(글리프 컨트롤](../../extensibility/internals/glyph-control-source-control-vspackage.md)참조).

4. 쿼리 편집 및 쿼리 저장 이벤트를 처리합니다(쿼리 [편집 쿼리 저장](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)참조).

## <a name="see-also"></a>참조
- [소스 제어 플러그인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)
