---
title: 레거시 언어 서비스 개발 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c7f930d5087b6a822156fd44024def0d5b42b49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708666"
---
# <a name="develop-a-legacy-language-service"></a>레거시 언어 서비스 개발
이 섹션에서는 레거시 언어 서비스를 만드는 데 도움이 되는 항목에 연결됩니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현되지만 언어 서비스 기능을 구현하는 최신 방법은 MEF 확장을 사용하는 것입니다. 언어 서비스를 구현하는 새로운 방법에 대한 자세한 내용은 [편집기 및 언어 서비스 확장을](../../extensibility/editor-and-language-service-extensions.md)참조하십시오.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상되고 새로운 편집기 기능을 활용할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [레거시 언어 서비스 모델](../../extensibility/internals/model-of-a-legacy-language-service.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 핵심 편집기용 최소 언어 서비스 모델을 제공합니다. 이 모델을 사용자 고유의 언어 서비스를 만들기 위한 지침으로 사용할 수 있습니다.

- [레거시 언어 서비스 인터페이스](../../extensibility/internals/legacy-language-service-interfaces.md)

 언어 서비스를 구현하는 데 필요한 개체에 대해 설명하고 구문 강조 표시, 메서드 데이터 및 기타 기능을 제공하는 데 사용할 수 있는 추가 개체 목록을 제공합니다.

- [레거시 언어 서비스 명령 가로채기](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 언어 서비스에 명령 필터를 삽입하여 텍스트 뷰가 처리할 명령을 가로채는 방법을 설명합니다.

- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service2.md)

 을 사용하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]언어 서비스를 등록하는 방법에 대한 정보를 제공합니다.

- [디버깅을 위한 언어 서비스 지원](../../extensibility/internals/language-service-support-for-debugging.md)

 언어 서비스가 디버거를 지원하는 기능을 제공하는 방법에 대해 설명합니다.

- [체크리스트: 레거시 언어 서비스 만들기](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 핵심 편집기의 언어 서비스를 만들고 통합하기 위한 단계별 지침을 제공합니다.

## <a name="related-sections"></a>관련 단원
- [레거시 언어 서비스의 구문 색칠](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 언어 서비스에서 구문 강조 표시를 구현하는 방법에 대해 설명합니다.

- [레거시 언어 서비스에서 명령문 완료](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 언어 서비스가 사용자가 입력을 시작한 언어 키워드 또는 요소를 완료하는 데 도움이 되는 프로세스인 문 완성에 대해 설명합니다.

- [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 오버로드된 함수 및 메서드에 대한 메서드 팁을 제공하는 방법에 대해 설명합니다.

- [방법: 레거시 언어 서비스에 숨겨진 텍스트 지원 제공](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 숨겨진 텍스트 영역의 용도를 설명하고 숨겨진 텍스트 영역을 구현하는 방법에 대한 지침을 제공합니다.

- [방법: 레거시 언어 서비스에서 확장된 개요 지원 제공](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 정의 축소 명령을 지원하는 것 이상으로 언어에 대한 개요 지원을 확장하는 두 가지 옵션에 대해 *설명합니다.*
