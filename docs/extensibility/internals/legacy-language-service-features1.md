---
title: 레거시 언어 서비스 Features1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f2a4010529d3d9727ceb76d6a34f2cbc41b959
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238493"
---
# <a name="legacy-language-service-features-1"></a>레거시 언어 서비스 기능 1
MPF (관리 되는 패키지 프레임 워크) 언어 서비스는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 구문 강조 표시, IntelliSense 및 중단점 유효성 검사와 같은 하나 이상의 기능을 지원할 수 있습니다. 각 기능은 다른 항목에 독립적으로 구현 될 수 있지만, 스캐너만 필요한 구문 강조를 제외 하 고는 파서 및 스캐너가 필요 합니다.

## <a name="in-this-section"></a>섹션 내용
- [레거시 언어 서비스의 중괄호 일치](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 문자 일치를 지 원하는 데 필요한 사항에 대해 설명 합니다 (중괄호 일치 라고도 함).

- [레거시 언어 서비스의 코드 주석 처리](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 선택한 코드의 주석 처리 및 주석 처리을 지 원하는 데 필요한 사항을 설명 합니다.

- [레거시 언어 서비스의 사용자 지정 문서 속성](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 소스 파일에 포함 된 문서 속성을 지 원하는 데 필요한 사항을 설명 합니다.

- [레거시 언어 서비스의 개요 표시](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 숨겨진 영역 구현에 대 한 개요를 지 원하는 데 필요한 사항을 설명 합니다.

- [레거시 언어 서비스의 코드 서식 다시 지정](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 코드 다시 포맷을 지 원하는 데 필요한 사항을 설명 합니다.

- [레거시 언어 서비스의 코드 조각 지원](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 코드 조각을 삽입 하 고 편집할 수 있는 코드 세그먼트를 지 원하는 데 필요한 사항에 대해 설명 합니다.

- [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 메서드가 형식화 될 때 메서드 시그니처를 표시 하기 위해 IntelliSense 매개 변수 정보 작업을 지 원하는 데 필요한 사항을 설명 합니다.

- [레거시 언어 서비스의 빠른 정보](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 식별자에 대 한 정보를 표시 하기 위해 IntelliSense 요약 정보 작업을 지 원하는 데 필요한 사항을 설명 합니다.

- [레거시 언어 서비스의 멤버 완성](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 목록에서 네임 스페이스의 멤버를 선택 하기 위해 IntelliSense 멤버 완료 작업을 지 원하는 데 필요한 사항을 설명 합니다.

- [레거시 언어 서비스의 단어 완성](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 부분적으로 형식화 된 단어를 완성 하기 위해 IntelliSense 자동 완성 작업을 지 원하는 데 필요한 사항을 설명 합니다.

- [레거시 언어 서비스의 자동 창 지원](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 디버깅 하는 동안 **자동** 창을 지원 하기 위해 언어 서비스에서 수행할 수 있는 작업을 설명 합니다.

- [레거시 언어 서비스의 탐색 모음 지원](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 편집기 보기의 위쪽에 있는 **탐색 모음** 을 사용 하 여 해당 보기에 표시 된 파일의 형식 또는 멤버에 대 한 빠른 탐색을 제공 하는 방법을 설명 합니다.

- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 소스 코드의 구문 강조 표시를 지 원하는 데 필요한 사항을 설명 합니다.

- [레거시 언어 서비스의 중단점 유효성 검사](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 디버거 외부에서 중단점 유효성 검사를 지원 하기 위해 언어 서비스에서 수행할 수 있는 작업을 설명 합니다.

## <a name="related-sections"></a>관련 섹션
- [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 관리 되는 패키지 프레임 워크를 사용 하는 언어 서비스의 모든 기능을 구현 하는 데 필요한 파서와 스캐너에 대해 설명 합니다.

- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 MPF를 사용 하 여 언어 서비스를 구현 하는 데 필요한 사항을 설명 합니다.

- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)

 에 MPF 기반 언어 서비스를 등록 하는 데 필요한 단계에 대해 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [IntelliSense 사용](../../ide/using-intellisense.md)

 IntelliSense를 사용 하 여 언어 참조를 쉽게 액세스 하는 방법을 설명 합니다.

- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 MPF (관리 되는 패키지 프레임 워크)를 사용 하 여 관리 코드에서 완전 한 기능을 갖춘 언어 서비스를 구현 하는 방법에 대 한 정보를 제공 합니다.
