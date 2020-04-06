---
title: 레거시 언어 서비스 확장성 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707402"
---
# <a name="legacy-language-service-extensibility"></a>레거시 언어 서비스 확장성
언어 서비스는 IDE에서 소스 코드를 편집하기 위한 언어별 지원을 제공합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 언어 서비스를 구현하는 새로운 방법에 대한 자세한 내용은 [편집기 및 언어 서비스 확장을](../../extensibility/editor-and-language-service-extensions.md)참조하십시오.

 이 섹션에서는 레거시 언어 서비스의 구조 및 구현에 대해 설명합니다.

## <a name="in-this-section"></a>섹션 내용
- [레거시 언어 서비스 마이그레이션](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Visual Studio 2008에서 최신 버전으로 언어 서비스를 업데이트하는 방법을 설명합니다.

- [레거시 언어 서비스 필수 항목](../../extensibility/internals/legacy-language-service-essentials.md)

 프로그래밍 언어를 Visual Studio에 통합하기 위한 언어 서비스를 개발하는 방법에 대한 중요한 정보를 제공합니다.

- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)

 언어 서비스를 만드는 데 도움이 되는 항목에 대한 링크를 제공합니다.

- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 언어 서비스에서 강조 표시하는 구문 지원에 대한 정보를 제공합니다.

- [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 관리되는 패키지 프레임워크(MPF)를 사용하여 관리 코드에서 완전한 기능을 갖춘 언어 서비스를 구현하는 방법에 대한 정보를 제공합니다.

- [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 IDE에서 기호의 트리 보기를 탐색할 수 있는 라이브러리 및 도구에 대해 설명합니다.

## <a name="related-sections"></a>관련 단원
- [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)

 Visual Studio 편집기의 개요를 제공합니다.

- [디버깅에 대한 언어 서비스 지원](../../extensibility/internals/language-service-support-for-debugging.md)

 프로그램을 디버깅하는 데 사용되는 디버거 구성 요소를 만들고 사용자 지정하는 데 필요한 정보가 포함된 Visual Studio 디버깅 SDK에 대한 정보와 링크를 제공합니다.
