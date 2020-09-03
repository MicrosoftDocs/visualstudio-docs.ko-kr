---
title: 명령 가용성 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709693"
---
# <a name="command-availability"></a>명령 가용성

Visual Studio 컨텍스트는 사용할 수 있는 명령을 결정 합니다. 컨텍스트는 현재 프로젝트, 현재 편집기, 로드 된 Vspackage 및 IDE (통합 개발 환경)의 기타 측면에 따라 달라질 수 있습니다.

## <a name="command-contexts"></a>명령 컨텍스트

가장 일반적인 명령 컨텍스트는 다음과 같습니다.

- IDE: IDE에서 제공 되는 명령은 항상 사용할 수 있습니다.

- VSPackage: Vspackage는 명령을 표시 하거나 숨기는 시기를 정의할 수 있습니다.

- 프로젝트: 프로젝트 명령은 현재 선택한 프로젝트에 대해서만 표시 됩니다.

- 편집기: 한 번에 하나의 편집기만 활성화 될 수 있습니다. 활성 편집기의 명령을 사용할 수 있습니다. 편집기는 언어 서비스와 긴밀 하 게 작동 합니다. 언어 서비스는 연결 된 편집기의 컨텍스트에서 해당 명령을 처리 해야 합니다.

- 파일 형식: 편집기에서 두 개 이상의 파일 형식을 로드할 수 있습니다. 사용할 수 있는 명령은 파일 형식에 따라 달라질 수 있습니다.

- 활성 창: 마지막 활성 문서 창에서는 키 바인딩에 대 한 UI (사용자 인터페이스) 컨텍스트를 설정 합니다. 그러나 내부 웹 브라우저와 유사한 키 바인딩 테이블이 있는 도구 창은 UI 컨텍스트를 설정할 수도 있습니다. HTML 편집기와 같은 다중 탭 문서 창의 경우 모든 탭에는 다른 명령 컨텍스트 GUID가 있습니다. 도구 창을 등록 한 후에는 항상 **보기** 메뉴에서 사용할 수 있습니다.

- UI 컨텍스트: UI 컨텍스트는 클래스의 값 (예: <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> 솔루션이 빌드되는 경우 또는 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> 디버거가 활성화 된 경우)으로 식별 됩니다. 여러 UI 컨텍스트는 동시에 활성화 될 수 있습니다.

## <a name="define-custom-context-guids"></a>사용자 지정 컨텍스트 Guid 정의

적절 한 명령 컨텍스트 GUID를 아직 정의 하지 않은 경우 VSPackage에서 정의 하 고 명령 표시 여부를 제어 하는 필요에 따라 활성 또는 비활성으로 프로그래밍할 수 있습니다.

1. 메서드를 호출 하 여 컨텍스트 Guid를 등록 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> 합니다.

2. 메서드를 호출 하 여 컨텍스트 GUID의 상태를 가져옵니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> .

3. 메서드를 호출 하 여 컨텍스트 Guid를 설정 및 해제 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> 합니다.

> [!CAUTION]
> 다른 Vspackage가이에 종속 될 수 있으므로 VSPackage가 기존 컨텍스트 Guid에 영향을 주지 않는지 확인 합니다.

## <a name="see-also"></a>추가 정보

- [선택 컨텍스트 개체](../../extensibility/internals/selection-context-objects.md)
- [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
