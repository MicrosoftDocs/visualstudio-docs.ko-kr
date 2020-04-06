---
title: 레거시 언어 서비스 기능1 | 마이크로 소프트 문서
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
ms.openlocfilehash: f0be7cb4401792b30eac595faf64162dc375dbb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707394"
---
# <a name="legacy-language-service-features"></a>레거시 언어 서비스 기능
MPF(관리되는 패키지 프레임워크) 언어 서비스는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 구문 강조 표시, IntelliSense 및 중단점 유효성 검사와 같은 하나 이상의 기능을 지원할 수 있습니다. 각 기능은 다른 기능과 독립적으로 구현할 수 있지만 스캐너만 필요한 구문 강조 표시를 제외한 모든 기능은 파서와 스캐너가 필요합니다.

## <a name="in-this-section"></a>섹션 내용
- [레거시 언어 서비스의 중괄호 일치](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 중괄호 일치라고도 하는 언어 쌍 일치를 지원하는 데 필요한 내용을 설명합니다.

- [레거시 언어 서비스의 코드 주석 처리](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 선택한 코드의 주석 달기 및 주석 해제를 지원하는 데 필요한 사항에 대해 설명합니다.

- [레거시 언어 서비스의 사용자 지정 문서 속성](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 원본 파일에 포함된 문서 속성을 지원하는 데 필요한 내용을 설명합니다.

- [레거시 언어 서비스의 개요 표시](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 숨겨진 영역의 구현을 통해 개요를 지원하는 데 필요한 내용을 설명합니다.

- [레거시 언어 서비스의 코드 서식 다시 지정](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 다시 포이팅 코드를 지원하는 데 필요한 내용을 설명합니다.

- [레거시 언어 서비스의 코드 조각 지원](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 삽입되고 편집할 수 있는 코드 세그먼트인 코드 조각을 지원하는 데 필요한 내용을 설명합니다.

- [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 메서드를 입력할 때 메서드 서명을 표시하기 위해 IntelliSense 매개 변수 정보 작업을 지원하는 데 필요한 작업에 대해 설명합니다.

- [레거시 언어 서비스의 빠른 정보](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 식별자에 대한 정보를 표시하기 위해 IntelliSense 빠른 정보 작업을 지원하는 데 필요한 작업에 대해 설명합니다.

- [레거시 언어 서비스의 멤버 완성](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 목록에서 네임스페이스의 멤버를 선택하는 데 IntelliSense 멤버 완료 작업을 지원하는 데 필요한 작업에 대해 설명합니다.

- [레거시 언어 서비스의 단어 완성](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 부분적으로 입력된 단어를 완료하기 위해 IntelliSense 전체 단어 작업을 지원하는 데 필요한 내용을 설명합니다.

- [레거시 언어 서비스의 자동 창 지원](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 디버깅하는 동안 언어 서비스가 **Autos** 창을 지원하기 위해 수행할 수 있는 작업을 설명합니다.

- [레거시 언어 서비스의 탐색 모음 지원](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 편집기 보기 의 상단에 있는 **탐색 모음을** 사용하여 해당 보기에 표시된 파일의 모든 형식 또는 멤버에 대한 빠른 탐색을 제공하는 방법에 대해 설명합니다.

- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 소스 코드의 구문 강조 표시를 지원하는 데 필요한 내용을 설명합니다.

- [레거시 언어 서비스의 중단점 유효성 검사](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 언어 서비스가 디버거 외부의 중단점 유효성 검사를 지원하기 위해 수행할 수 있는 작업을 설명합니다.

## <a name="related-sections"></a>관련 단원
- [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 관리되는 패키지 프레임워크를 사용하는 언어 서비스의 모든 기능을 구현하는 데 필요한 파서 및 스캐너에 대해 설명합니다.

- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 MPF를 사용하여 언어 서비스를 구현하는 데 필요한 사항을 설명합니다.

- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]MPF 기반 언어 서비스를 에 등록하는 데 필요한 단계를 설명합니다.

- [IntelliSense 사용](../../ide/using-intellisense.md)

 IntelliSense가 언어 참조에 쉽게 액세스할 수 있도록 하는 방법을 설명합니다.

- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 관리되는 패키지 프레임워크(MPF)를 사용하여 관리 코드에서 완전한 기능을 갖춘 언어 서비스를 구현하는 방법에 대한 정보를 제공합니다.
