---
title: 명령 가용성 | 마이크로 소프트 문서
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca47d9ed9968c101e3b6b859b51c1cd8d7404db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709693"
---
# <a name="command-availability"></a>명령 가용성

Visual Studio 컨텍스트는 사용할 수 있는 명령을 결정합니다. 컨텍스트는 현재 프로젝트, 현재 편집기, 로드된 VSPackage 및 통합 개발 환경(IDE)의 다른 측면에 따라 달라질 수 있습니다.

## <a name="command-contexts"></a>명령 컨텍스트

다음 명령 컨텍스트가 가장 일반적입니다.

- IDE: IDE에서 제공하는 명령은 항상 사용할 수 있습니다.

- VSPackage: VSPackage는 명령을 표시하거나 숨길 시기를 정의할 수 있습니다.

- 프로젝트: 프로젝트 명령은 현재 선택한 프로젝트에 대해서만 표시됩니다.

- 편집자: 한 번에 하나의 편집기만 활성화할 수 있습니다. 활성 편집기의 명령을 사용할 수 있습니다. 편집자는 언어 서비스와 긴밀하게 작동합니다. 언어 서비스는 연결된 편집기의 컨텍스트에서 명령을 처리해야 합니다.

- 파일 형식: 편집기는 두 개 이상의 파일 형식을 로드할 수 있습니다. 사용 가능한 명령은 파일 형식에 따라 변경될 수 있습니다.

- 활성 창: 마지막 활성 문서 창은 키 바인딩에 대한 사용자 인터페이스(UI) 컨텍스트를 설정합니다. 그러나 내부 웹 브라우저와 유사한 키 바인딩 테이블이 있는 도구 창은 UI 컨텍스트를 설정할 수도 있습니다. HTML 편집기와 같은 다중 탭된 문서 창의 경우 모든 탭에는 다른 명령 컨텍스트 GUID가 있습니다. 도구 창을 등록한 후에는 **항상 보기** 메뉴에서 사용할 수 있습니다.

- UI 컨텍스트: UI 컨텍스트는 솔루션이 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> 빌드되는 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> 경우 또는 디버거가 활성 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> 상태일 때와 같은 클래스의 값으로 식별됩니다. 여러 UI 컨텍스트를 동시에 활성화할 수 있습니다.

## <a name="define-custom-context-guids"></a>사용자 지정 컨텍스트 GUID 정의

적절한 명령 컨텍스트 GUID가 아직 정의되지 않은 경우 VSPackage에서 GUID를 정의한 다음 명령의 가시성을 제어하는 데 필요한 대로 활성 또는 비활성으로 프로그래밍할 수 있습니다.

1. 메서드를 호출하여 컨텍스트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> GUID를 등록합니다.

2. 메서드를 호출하여 컨텍스트 GUID의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 상태를 가져옵니다.

3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 메서드를 호출하여 컨텍스트 GUID를 켜고 끕니다.

> [!CAUTION]
> 다른 VSPackage가 종속될 수 있으므로 VSPackage가 기존 컨텍스트 GUID에 영향을 주지 않는지 확인합니다.

## <a name="see-also"></a>참조

- [선택 컨텍스트 개체](../../extensibility/internals/selection-context-objects.md)
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
