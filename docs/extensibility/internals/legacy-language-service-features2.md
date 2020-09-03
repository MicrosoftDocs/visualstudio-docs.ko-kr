---
title: 레거시 언어 서비스 Features2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], code development aides
ms.assetid: 97c38622-ae0b-4ae0-90ed-604072c298d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04e7df7fc5c7532d2db45bc2b643a249d1e566c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88237908"
---
# <a name="legacy-language-service-features-2"></a>레거시 언어 서비스 기능 2
다음 항목에서는 사용자가 제공할 수 있는 레거시 언어 서비스 기능 중 일부를 나열 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 언어 서비스를 구현 하는 새로운 방법에 대해 자세히 알아보려면 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)을 참조 하세요.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 구문 색 지정을 구현 하는 방법을 설명 합니다.

- [레거시 언어 서비스의 자동 서식](../../extensibility/internals/automatic-formatting-in-a-legacy-language-service.md)

 자동 서식 지정을 구현 하는 방법을 설명 합니다.

- [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 IntelliSense 매개 변수 정보 도구 설명을 구현 하는 방법을 설명 합니다.

- [레거시 언어 서비스의 명령문 완성](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 IntelliSense 문 목록 및 멤버 완성 목록을 구현 하는 방법에 대해 설명 합니다.

- [레거시 언어 서비스의 개요 표시 및 숨겨진 텍스트](../../extensibility/internals/outlining-and-hidden-text-in-a-legacy-language-service.md)

 개요 또는 숨겨진 텍스트를 구현 하는 방법을 설명 합니다.

- [방법: 레거시 언어 서비스에서 확장 개요 표시 지원 제공](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 디버거 지원 구현의 일부 단계에 대해 설명 합니다.

## <a name="related-sections"></a>관련 섹션
