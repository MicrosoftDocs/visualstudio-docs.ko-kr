---
title: 레거시 언어 서비스 확장성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81b5ec3de8d7b0b9466e162c3ee193c130634cd4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707402"
---
# <a name="legacy-language-service-extensibility"></a>레거시 언어 서비스 확장성
언어 서비스는 IDE에서 소스 코드를 편집 하는 언어 관련 지원을 제공 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 언어 서비스를 구현 하는 새로운 방법에 대해 자세히 알아보려면 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)을 참조 하세요.

 이 섹션에서는 레거시 언어 서비스의 구조 및 구현에 대해 설명 합니다.

## <a name="in-this-section"></a>섹션 내용
- [레거시 언어 서비스 마이그레이션](../../extensibility/internals/migrating-a-legacy-language-service.md)

 언어 서비스를 Visual Studio 2008에서 최신 버전으로 업데이트 하는 방법을 설명 합니다.

- [레거시 언어 서비스 필수 항목](../../extensibility/internals/legacy-language-service-essentials.md)

 프로그래밍 언어를 Visual Studio에 통합 하는 언어 서비스를 개발 하는 방법에 대 한 중요 한 정보를 제공 합니다.

- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)

 언어 서비스를 만드는 데 도움이 될 수 있는 항목에 대 한 링크를 제공 합니다.

- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 언어 서비스에서 구문 강조 표시를 지 원하는 방법에 대 한 정보를 제공 합니다.

- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 MPF (관리 되는 패키지 프레임 워크)를 사용 하 여 관리 코드에서 완전 한 기능을 갖춘 언어 서비스를 구현 하는 방법에 대 한 정보를 제공 합니다.

- [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 IDE에서 기호 트리 뷰를 찾아볼 수 있는 라이브러리 및 도구에 대해 설명 합니다.

## <a name="related-sections"></a>관련 섹션
- [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)

 Visual Studio 편집기에 대 한 개요를 제공 합니다.

- [디버깅에 대한 언어 서비스 지원](../../extensibility/internals/language-service-support-for-debugging.md)

 프로그램 디버깅에 사용 되는 디버거 구성 요소를 만들고 사용자 지정 하는 데 필요한 정보를 포함 하는 Visual Studio 디버깅 SDK에 대 한 정보 및 링크를 제공 합니다.
