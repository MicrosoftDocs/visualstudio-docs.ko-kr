---
title: IDE의 선택 및 통화 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705575"
---
# <a name="selection-and-currency-in-the-ide"></a>IDE의 선택 및 통화
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합 개발 환경(IDE)은 선택 *컨텍스트를*사용하여 사용자의 현재 선택된 개체에 대한 정보를 유지 관리합니다. 선택 컨텍스트를 사용하면 VSPackage는 다음 두 가지 방법으로 통화 추적에 참여할 수 있습니다.

- VSPackage에 대한 통화 정보를 IDE에 전파합니다.

- IDE 내에서 사용자의 현재 활성 선택을 모니터링합니다.

## <a name="selection-context"></a>선택 컨텍스트
 IDE는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 자체 전역 선택 컨텍스트 개체에서 IDE 통화를 추적합니다. 다음 표에서는 선택 컨텍스트를 구성하는 요소를 보여 주어집니다.

|요소|Description|
|-------------|-----------------|
|현재 계층 구조|일반적으로 현재 프로젝트; NULL 현재 계층 구조는 솔루션 전체가 현재임을 나타냅니다.|
|현재 항목ID|현재 계층 구조 내에서 선택한 항목; 프로젝트 창에 여러 선택 항목이 있는 경우 여러 현재 항목이 있을 수 있습니다.|
|현재`SelectionContainer`|속성 창에 속성을 표시해야 하는 하나 이상의 객체를 보유합니다.|

 또한 환경은 두 개의 전역 목록을 유지 관리합니다.

- 활성 UI 명령 식별자 목록

- 현재 활성 요소 유형의 목록입니다.

### <a name="window-types-and-selection"></a>창 유형 및 선택
 IDE는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 창을 두 가지 일반 유형으로 구성합니다.

- 계층 유형 창

- 도구 및 문서 창과 같은 프레임 창

  IDE는 이러한 각 창 유형에 대해 통화를 다르게 추적합니다.

  가장 일반적인 프로젝트 유형 창은 IDE가 제어하는 솔루션 탐색기입니다. 프로젝트 유형 창은 전역 선택 컨텍스트의 전역 계층 및 ItemID를 추적하고 창은 사용자의 선택에 의존하여 현재 계층구조를 결정합니다. 프로젝트 형식 창의 경우 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>VSPackage가 열려 있는 요소에 대한 현재 값을 모니터링할 수 있는 전역 서비스를 제공합니다. 환경에서 속성 검색은 이 전역 서비스에 의해 구동됩니다.

  반면 프레임 창은 프레임 창 내의 DocObject를 사용하여 SelectionContext 값(계층/ItemID/SelectionContainer 트리오)을 푸시합니다. . 프레임 창은 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> 이 목적을 위해 서비스를 사용합니다. DocObject는 선택 컨테이너에 대한 값만 푸시할 수 있으며, MDI 자식 문서의 경우처럼 계층 구조 및 ItemID에 대한 로컬 값은 변경되지 않습니다.

### <a name="events-and-currency"></a>이벤트 및 통화
 환경의 통화 개념에 영향을 주는 두 가지 유형의 이벤트가 발생할 수 있습니다.

- 전역 수준으로 전파되고 창 프레임 선택 컨텍스트를 변경하는 이벤트입니다. 이러한 종류의 이벤트의 예로는 열려 있는 MDI 자식 창, 열려 있는 전역 도구 창 또는 열려 있는 프로젝트 형식 도구 창 등이 있습니다.

- 창 프레임 선택 컨텍스트 내에서 추적된 요소를 변경하는 이벤트입니다. 예를 들어 DocObject 내에서 선택 을 변경하거나 프로젝트 유형 창에서 선택 을 변경합니다.

## <a name="see-also"></a>참조
- [선택 컨텍스트 개체](../../extensibility/internals/selection-context-objects.md)
- [사용자에 대한 피드백](../../extensibility/internals/feedback-to-the-user.md)
