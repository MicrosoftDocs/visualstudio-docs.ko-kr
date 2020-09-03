---
title: 사용자 의견 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708409"
---
# <a name="feedback-to-the-user"></a>사용자 의견
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE (통합 개발 환경)에서 사용 가능한 기능에 대 한 시각적 피드백은 사용자의 현재 선택 영역 및 전역 선택 컨텍스트를 기반으로 합니다. 다음 표에서는 다양 한 선택 컨텍스트에서 사용할 수 있는 기능을 보여 줍니다.

|선택 컨텍스트|사용 가능한 기능|
|-----------------------|-----------------------------|
|IDE|전역|
|현재 제품 집합|제품별|
|활성 계층|계층 유형별 특정|
|활성 계층 항목|계층 항목 형식별|
|활성 문서|문서 유형별|
|최상위 MDI (다중 문서 인터페이스) 창|창 유형별|
|현재 선택 컨텍스트|선택 컨텍스트별 컨텍스트별|

 사용자가 필요로 하는 기능을 노출 하 고 일관 된 선택 및 환경 컨텍스트 피드백을 지속적으로 제공 하는 경우 IDE의 복잡성을 줄일 수 있습니다. IDE에서 창이 열릴 때마다 다음 규칙이 적용 됩니다.

- 창이 선택 컨텍스트를 변경 하면 창에 선택 피드백이 명확 하 게 표시 되 고, 표시 되는 경우 **동적 도움말** 창이 현재 컨텍스트를 반영 하도록 업데이트 됩니다.

- 창에서 전역 선택 컨텍스트를 변경 하면 모든 컨텍스트별 메뉴, 활성 계층 창 및 응용 프로그램 제목 표시줄이 현재 컨텍스트를 반영 하도록 업데이트 됩니다.

- 창에는 **속성 창에서** 현재 선택 영역에 대 한 속성 및 속성 **페이지** 대화 상자 (표시 되는 경우)가 표시 됩니다.

- 창에서 속성을 노출 하지 않거나 전역 선택 컨텍스트를 변경 하는 경우 IDE의 활성 창이 더 이상 없으면 선택 피드백이 창에 남아 있지 않아야 합니다.

- 모든 문서 관련 도구 창은 활성 문서를 지속적으로 반영 해야 합니다.

- 메뉴, 도구 모음 및 응용 프로그램 제목 표시줄에는 최상위 MDI (다중 문서 인터페이스) 클라이언트 창이 반영 되어야 합니다.

  예를 들어 Visual Basic 웹 응용 프로그램 프로젝트 내의 **웹 폼** 에 대 한 HTML 보기가 열리고 사용자가 태그를 선택 하면 `<td>` 다음과 같은 방식으로 피드백이 제공 됩니다.

- 선택은 활성 창에 표시 되 고 **속성** 창에 반영 됩니다.

- 문서 관련 **도구 상자** 는 활성 문서를 반영 하도록 업데이트 됩니다.

- **편집기** 도구 모음과 **테이블** 메뉴가 표시 되 고 웹 폼 창을 반영 하는 제목 표시줄이 업데이트 됩니다.

- 현재 컨텍스트를 반영 하 고 상황에 맞는 **프로젝트** 메뉴 명령이 현재 컨텍스트를 반영 하 고 현재 컨텍스트를 반영 하는 활성 웹 응용 프로그램 프로젝트에 적용 되는 활성 계층 구조 창 (일반적으로 **솔루션 탐색기**)입니다.

## <a name="see-also"></a>참고 항목
- [IDE의 선택 및 통화](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [선택 컨텍스트 개체](../../extensibility/internals/selection-context-objects.md)
- [계층 및 선택](../../extensibility/internals/hierarchies-and-selection.md)
