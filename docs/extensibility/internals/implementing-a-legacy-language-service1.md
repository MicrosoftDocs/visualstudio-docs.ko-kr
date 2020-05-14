---
title: 레거시 언어 서비스 구현1 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3805e49ffa83f7dea2ee58ef36e1bc8e48b1eaa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707693"
---
# <a name="implementing-a-legacy-language-service"></a>레거시 언어 서비스 구현
MPF(관리되는 패키지 프레임워크)의 클래스를 사용하여 구문 강조 표시, 중괄호 일치 및 IntelliSense 완료와 같은 다양한 기능을 지원하는 레거시 언어 서비스를 구현할 수 있습니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 언어 서비스를 구현하는 새로운 방법에 대한 자세한 내용은 [편집기 및 언어 서비스 확장을](../../extensibility/editor-and-language-service-extensions.md)참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [레거시 언어 서비스 개요](../../extensibility/internals/legacy-language-service-overview.md)

 MPF에서 지원되는 언어 서비스 기능에 대한 개요입니다.

- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 MPF를 사용하여 언어 서비스를 구현하는 데 필요한 사항을 설명합니다.

- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]MPF 기반 언어 서비스를 에 등록하는 데 필요한 단계를 설명합니다.

- [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 MPF를 사용하여 언어 서비스의 모든 기능을 구현하는 데 필요한 두 구문 분석자에 대해 설명합니다.

- [연습: 레거시 언어 서비스 만들기](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 VSPackage에서 MPF 언어 서비스를 구현하는 데 필요한 기본 단계를 제공합니다.

- [연습: 설치된 코드 조각 목록 가져오기(레거시 구현)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 설치된 코드 조각 목록을 검색하는 기술을 보여 줍니다.

- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)

 MPF를 사용하여 언어 서비스의 모든 기능을 구현하기 위해 수행해야 하는 작업을 자세히 설명하는 항목에 대한 링크를 제공합니다.
