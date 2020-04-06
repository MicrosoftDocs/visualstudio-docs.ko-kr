---
title: 도구 창 등록 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e7971de5ae5301d99147bbfc374dda6b039662a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701591"
---
# <a name="register-a-tool-window"></a>도구 창 등록
<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>을 사용하여 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 도구 창을 등록할 수 있습니다.

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

 위의 코드에서 Visual <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> Studio를 `PersistedWindowPane` `DynamicWindowPane` 사용하여 도구 창을 등록합니다. 지속된 도구 창은 도킹되고 **Solution 탐색기로**탭되고 동적 창에는 기본 시작 위치와 크기가 지정됩니다. 동적 창은 시작 시 만들어지지 않음을 나타내는 일시적인 창이 만들어집니다. 이렇게 하면 `DontForceCreate` 시스템 `ToolWindows` 레지스트리의 키에 값이 기록됩니다. 자세한 내용은 [도구 창 디스플레이 구성을](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015)참조하십시오.
