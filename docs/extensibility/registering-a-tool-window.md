---
title: 도구 창 | 등록 Microsoft Docs
description: ProvideToolWindowAttribute 및 ProvideToolWindowVisibilityAttribute를 사용하여 도구 창을 Visual Studio 등록하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f4fb6330f913989a69c5d8d28374a40ea14d266d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899097"
---
# <a name="register-a-tool-window"></a>도구 창 등록
및 를 사용하여 도구 창을 등록할 수 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> 있습니다.

## <a name="example"></a>예제

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 위의 코드에서 는 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 및 도구 창을 Visual Studio 등록합니다. `PersistedWindowPane` `DynamicWindowPane` 지속형 도구 창은 **도킹되고 솔루션 탐색기** 탭으로 표시되며 동적 창에는 기본 시작 위치와 크기가 지정됩니다. 동적 창은 시작 시 생성되지 않음을 나타내는 일시적 창으로 만들어집니다. 그러면 시스템 `DontForceCreate` `ToolWindows` 레지스트리의 키에 값이 기록됩니다. 자세한 내용은 [도구 창 표시 구성을 참조하세요.](/previous-versions/visualstudio/visual-studio-2015/extensibility/tool-window-display-configuration?preserve-view=true&view=vs-2015)