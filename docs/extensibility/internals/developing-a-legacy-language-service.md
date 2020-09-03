---
title: 레거시 언어 서비스 개발 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708666"
---
# <a name="develop-a-legacy-language-service"></a>레거시 언어 서비스 개발
이 섹션에서는 레거시 언어 서비스를 만드는 데 도움이 되는 항목에 대 한 링크를 제공 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 언어 서비스를 구현 하는 새로운 방법에 대해 자세히 알아보려면 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)을 참조 하세요.

> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [레거시 언어 서비스의 모델](../../extensibility/internals/model-of-a-legacy-language-service.md)

 핵심 편집기에 대 한 최소 언어 서비스의 모델을 제공 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 사용자 고유의 언어 서비스를 만들기 위한 지침으로이 모델을 사용할 수 있습니다.

- [레거시 언어 서비스 인터페이스](../../extensibility/internals/legacy-language-service-interfaces.md)

 언어 서비스를 구현 하는 데 필요한 개체에 대해 설명 하 고 구문 강조 표시, 메서드 데이터 및 기타 기능을 제공 하는 데 사용할 수 있는 추가 개체의 목록을 제공 합니다.

- [레거시 언어 서비스 명령을 가로챕니다.](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 명령 필터를 언어 서비스에 삽입 하 여 텍스트 뷰에서 다른 방법으로 처리할 명령을 가로채는 방법에 대해 설명 합니다.

- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service2.md)

 를 사용 하 여 언어 서비스를 등록 하는 방법에 대 한 정보를 제공 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다.

- [디버깅을 위한 언어 서비스 지원](../../extensibility/internals/language-service-support-for-debugging.md)

 언어 서비스에서 디버거를 지 원하는 기능을 제공 하는 방법을 설명 합니다.

- [검사 목록: 레거시 언어 서비스 만들기](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 핵심 편집기에 대 한 언어 서비스를 만들고 통합 하는 방법에 대 한 단계별 지침을 제공 합니다.

## <a name="related-sections"></a>관련 단원
- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 언어 서비스에서 구문 강조 표시를 구현 하는 방법에 대해 설명 합니다.

- [레거시 언어 서비스의 문 완성](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 언어 서비스에서 사용자가 입력을 시작한 언어 키워드나 요소를 완료 하는 데 도움이 되는 프로세스를 설명 합니다.

- [레거시 언어 서비스의 매개 변수 정보](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 오버 로드 된 함수 및 메서드에 대 한 메서드 팁을 제공 하는 방법을 설명 합니다.

- [방법: 레거시 언어 서비스에서 숨겨진 텍스트 지원 제공](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 숨겨진 텍스트 영역의 용도를 설명 하 고 숨겨진 텍스트 영역을 구현 하는 방법에 대 한 지침을 제공 합니다.

- [방법: 레거시 언어 서비스에서 확장 된 개요 지원 제공](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 *정의로 축소* 명령을 지 원하는 것 이상으로 언어에 대 한 개요 지원을 확장 하는 두 가지 옵션에 대해 설명 합니다.
