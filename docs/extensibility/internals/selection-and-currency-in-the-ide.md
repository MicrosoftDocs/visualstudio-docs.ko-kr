---
title: IDE의 선택 및 통화 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f580b7c8e1651dcbcd053476ae756399a0ac3482
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705575"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE의 선택 및 통화
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE (통합 개발 환경)는 선택 *컨텍스트*를 사용 하 여 사용자의 현재 선택 된 개체에 대 한 정보를 유지 관리 합니다. 선택 컨텍스트를 사용 하 여 Vspackage는 다음과 같은 두 가지 방법으로 통화 추적에 참여 합니다.

- Vspackage에 대 한 통화 정보를 IDE에 전파 합니다.

- IDE 내에서 사용자의 현재 활성 선택 항목을 모니터링 합니다.

## <a name="selection-context"></a>선택 컨텍스트
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Ide는 전역 선택 컨텍스트 개체에서 ide 통화를 전역적으로 추적 합니다. 다음 표에서는 선택 컨텍스트를 구성 하는 요소를 보여 줍니다.

|요소|설명|
|-------------|-----------------|
|현재 계층 구조|일반적으로 현재 프로젝트입니다. NULL 현재 계층은 전체 솔루션이 최신 상태임을 나타냅니다.|
|현재 ItemID|현재 계층 구조 내에서 선택한 항목입니다. 프로젝트 창에서 여러 항목을 선택 하는 경우 여러 개의 현재 항목이 있을 수 있습니다.|
|현재 `SelectionContainer`|속성 창에서 속성을 표시 해야 하는 하나 이상의 개체를 포함 합니다.|

 또한 환경은 다음과 같은 두 가지 전역 목록을 유지 관리 합니다.

- 활성 UI 명령 식별자 목록

- 현재 활성 요소 형식의 목록입니다.

### <a name="window-types-and-selection"></a>창 유형 및 선택
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE는 다음과 같은 두 가지 일반적인 형식으로 창을 구성 합니다.

- 계층 구조 형식 창

- 도구 및 문서 창과 같은 프레임 창

  IDE는 이러한 각 창 유형에 대해 통화를 다르게 추적 합니다.

  가장 일반적인 프로젝트 형식 창은 IDE에서 제어 하는 솔루션 탐색기입니다. 프로젝트 형식 창은 전역 선택 컨텍스트의 전역 계층 및 ItemID를 추적 하 고 창은 사용자의 선택에 따라 현재 계층을 결정 합니다. 프로젝트 형식 창의 경우 환경은 전역 서비스를 제공 하며 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> ,이를 통해 vspackage는 열려 있는 요소의 현재 값을 모니터링할 수 있습니다. 환경에서의 속성 검색은이 글로벌 서비스에 의해 결정 됩니다.

  반면 프레임 창에는 프레임 창 내에서 DocObject를 사용 하 여 SelectionContext 값 (hierarchy/ItemID/Selectioncontext 3 개 숫자)을 푸시합니다. . 이 용도로는 프레임 창에서 서비스를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 합니다. DocObject는 MDI 자식 문서와 마찬가지로 계층 및 ItemID의 로컬 값이 변경 되지 않은 상태로 유지 되는 선택 컨테이너에 대 한 값만 푸시할 수 있습니다.

### <a name="events-and-currency"></a>이벤트 및 통화
 환경의 통화 개념에 영향을 주는 두 가지 유형의 이벤트가 발생할 수 있습니다.

- 전역 수준으로 전파 되 고 창 프레임 선택 컨텍스트를 변경 하는 이벤트입니다. 이러한 종류의 이벤트에는 열려 있는 MDI 자식 창, 열린 전역 도구 창 또는 프로젝트 형식 도구 창이 포함 됩니다.

- 창 프레임 선택 컨텍스트 내에서 추적 되는 요소를 변경 하는 이벤트입니다. 예를 들어 DocObject 내에서 선택 내용을 변경 하거나 프로젝트 형식 창에서 선택을 변경 합니다.

## <a name="see-also"></a>참조
- [선택 컨텍스트 개체](../../extensibility/internals/selection-context-objects.md)
- [사용자에 대한 피드백](../../extensibility/internals/feedback-to-the-user.md)
