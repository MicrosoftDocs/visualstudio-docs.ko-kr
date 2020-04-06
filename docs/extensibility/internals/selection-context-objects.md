---
title: 선택 컨텍스트 개체 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e4f33dd0168a667b8f266ea606cecf0c26d62f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705507"
---
# <a name="selection-context-objects"></a>선택 컨텍스트 개체
통합 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 개발 환경(IDE)은 전역 선택 컨텍스트 개체를 사용하여 IDE에 표시할 항목을 결정합니다. IDE의 각 창에는 자체 선택 컨텍스트 개체가 전역 선택 컨텍스트로 푸시될 수 있습니다. IDE는 해당 창에 포커스가 있는 경우 창의 값으로 전역 선택 컨텍스트를 업데이트합니다. 자세한 내용은 [사용자에 대한 피드백을](../../extensibility/internals/feedback-to-the-user.md)참조하십시오.

 IDE의 각 창 프레임 또는 사이트에는 .라는 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>서비스가 있습니다. 창 프레임에 있는 VSPackage에서 만든 개체는 `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 메서드를 호출하여 인터페이스에 대한 포인터를 얻어야 합니다.

 프레임 창은 선택 컨텍스트 정보의 일부가 시작될 때 전역 선택 컨텍스트로 전파되지 않도록 할 수 있습니다. 이 기능은 빈 선택으로 시작해야 할 수 있는 도구 창에 유용합니다.

 전역 선택 컨텍스트를 수정하면 VSPackage가 모니터링할 수 있는 이벤트가 트리거됩니다. VSPackage는 구현 및 `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> 인터페이스를 통해 다음 작업을 수행할 수 있습니다.

- 계층 구조에서 현재 활성 파일을 업데이트합니다.

- 특정 유형의 요소에 대한 변경 내용을 모니터링합니다. 예를 들어 VSPackage에서 특수 **속성** 창을 사용하는 경우 활성 **속성** 창의 변경 내용을 모니터링하고 필요할 때 다시 시작할 수 있습니다.

  다음 순서는 선택 추적의 일반적인 과정을 보여 주며,

1. IDE는 새로 열린 창에서 선택 컨텍스트를 검색하고 전역 선택 컨텍스트에 넣습니다. 선택 컨텍스트에서 HIERARCHY_DONTPROPAGATE 또는 SELCONTAINER_DONTPROPAGATE 사용하는 경우 해당 정보는 전역 컨텍스트에 전파되지 않습니다. 자세한 내용은 [사용자에 대한 피드백을](../../extensibility/internals/feedback-to-the-user.md)참조하십시오.

2. 알림 이벤트는 요청한 모든 VSPackage에 브로드캐스트됩니다.

3. VSPackage는 계층 구조 업데이트, 도구 재활성화 또는 기타 유사한 작업과 같은 작업을 수행하여 수신되는 이벤트에 대해 작동합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Visual Studio의 계층 구조](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [IDE의 선택 및 통화](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [프로젝트 유형](../../extensibility/internals/project-types.md)
