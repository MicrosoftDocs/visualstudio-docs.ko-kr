---
title: 사용자에 대한 피드백 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46b9190b16b9aa444384847bf209ccca50c7f768
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708409"
---
# <a name="feedback-to-the-user"></a>사용자에 대한 피드백
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합 개발 환경(IDE)에서는 사용 가능한 기능에 대한 시각적 피드백은 사용자의 현재 선택 및 전역 선택 컨텍스트를 기반으로 합니다. 다음 표에는 다양한 선택 컨텍스트에서 사용할 수 있는 기능이 나열되어 있습니다.

|선택 컨텍스트|사용 가능한 기능|
|-----------------------|-----------------------------|
|IDE|Global|
|현재 제품 세트|제품별|
|활성 계층 구조|계층 유형별|
|활성 계층 구조 항목|계층 구조 항목 유형별|
|활성 문서|문서 유형별|
|최상위 다중 문서 인터페이스(MDI) 창|창 유형별|
|현재 선택 컨텍스트|선택 컨텍스트별|

 사용자에게 필요한 기능만 표시하고 일관된 선택 및 환경 컨텍스트 피드백을 지속적으로 제공하는 경우 IDE의 복잡성이 줄어듭니다. 다음 규칙은 IDE에서 창을 열 때마다 적용됩니다.

- 창이 선택 컨텍스트를 변경하면 선택 피드백이 창에 명확하게 표시되고 **동적 도움말** 창이 표시되는 경우 현재 컨텍스트를 반영하도록 업데이트됩니다.

- 창이 전역 선택 컨텍스트를 변경하면 모든 컨텍스트별 메뉴, 활성 계층 구조 창 및 응용 프로그램 제목 표시줄이 현재 컨텍스트를 반영하도록 업데이트됩니다.

- 창은 **속성** 창에서 현재 선택 영역에 대한 속성을 표시해야 하며, 선택적으로 속성 페이지 대화 상자가 표시되는 경우 선택적으로 표시되어야 **합니다.**

- 창이 속성을 표시하지 않거나 전역 선택 컨텍스트를 변경하지 않는 경우 IDE의 활성 창이 더 이상 없을 때 선택 피드백이 창에 남아 있지 않아야 합니다.

- 모든 문서별 도구 창은 활성 문서를 지속적으로 반영해야 합니다.

- 메뉴, 도구 모음 및 응용 프로그램 제목 표시줄은 최상위 MDI(다중 문서 인터페이스) 클라이언트 창을 반영해야 합니다.

  예를 들어 Visual Basic 웹 응용 프로그램 프로젝트 내의 **웹 양식의** HTML `<td>` 보기가 열리고 사용자가 태그를 선택하면 다음과 같은 방식으로 피드백이 제공됩니다.

- 선택 영역은 활성 창에 표시되고 **속성** 창에 반영됩니다.

- 활성 문서를 반영하도록 문서별 **도구 상자가** 업데이트됩니다.

- **편집기** 도구 모음 및 **테이블** 메뉴가 표시되고 제목 표시줄이 웹 양식 창을 반영하도록 업데이트됩니다.

- 일반적으로 **솔루션 탐색기인**활성 계층 구조 창과 현재 컨텍스트 및 상황에 맞는 **프로젝트** 메뉴 명령을 반영하기 위한 제목 표시줄 업데이트가 활성 웹 응용 프로그램 프로젝트에 적용됩니다.

## <a name="see-also"></a>참조
- [IDE의 선택 및 통화](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [선택 컨텍스트 개체](../../extensibility/internals/selection-context-objects.md)
- [계층 구조 및 선택](../../extensibility/internals/hierarchies-and-selection.md)
