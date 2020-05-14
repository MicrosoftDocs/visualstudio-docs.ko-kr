---
title: 레거시 언어 서비스 개요 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed653ec200063e72434fc758c7920e6caabafe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707350"
---
# <a name="legacy-language-service-overview"></a>레거시 언어 서비스 개요
언어 서비스는 특정 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 기능을 구현할 수 있는 편집기 지원을 제공합니다. MPF(관리되는 패키지 프레임워크) 언어 서비스 클래스는 자주 사용하는 기능과 다른 기능에 대한 부분 지원을 제공합니다.

## <a name="fully-supported-features-in-the-mpf"></a>MPF에서 완벽하게 지원되는 기능
 MPF 언어 서비스 클래스는 다음 기능을 지원합니다.

- 구문 강조 표시

- 개요

- 코드 블록 주석 달기

- 중괄호 일치

- 코드 조각

- 사용자 지정 문서 속성

- 인텔리센스 파라미터 정보

- 인텔리센스 퀵 정보

- 인텔리센스 회원 완료

- 인텔리센스 단어 완성

## <a name="partially-supported-features-in-the-mpf"></a>MPF에서 부분적으로 지원되는 기능
 MPF는 다음 기능에 대한 부분 지원만 제공합니다. 즉, MPF에서 호출하는 메서드를 구현해야 합니다.

- 코드 다시 포식. 다시 포식을 구현하는 코드를 제공합니다.

- 유효한 코드 범위를 식별하여 중단점의 유효성을 검사합니다. 코드 범위를 식별하는 코드를 제공합니다.

- 변수를 표시하기 위한 디버거 **자동** 창 지원. 창에 표시할 내용을 결정하는 코드를 제공합니다.

- 형식과 멤버 간의 빠른 탐색을 위해 **탐색 모음을** 지원합니다. **탐색 모음** 콤보 상자에 목록을 채우는 도우미 클래스를 구현 하 고 반환 합니다.

## <a name="implementation"></a>구현
 언어 서비스 자체와 해당 언어에 대해 지원하려는 언어 서비스 기능을 구현하기 위해 몇 단계를 완료해야 합니다. 다음 단계에서는 다음 항목에 대해 설명합니다.

- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [레거시 언어 서비스의 중괄호 일치](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [레거시 언어 서비스의 개요 표시](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [레거시 언어 서비스의 코드 주석 처리](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [레거시 언어 서비스의 코드 서식 다시 지정](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [레거시 언어 서비스의 사용자 지정 문서 속성](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [레거시 언어 서비스의 코드 조각 지원](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [레거시 언어 서비스의 탐색 모음 지원](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [레거시 언어 서비스의 단어 완성](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [레거시 언어 서비스의 멤버 완성](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [레거시 언어 서비스의 빠른 정보](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [레거시 언어 서비스의 자동 창 지원](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [레거시 언어 서비스의 중단점 유효성 검사](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>참조
- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [레거시 언어 서비스 확장성](../../extensibility/internals/legacy-language-service-extensibility.md)
