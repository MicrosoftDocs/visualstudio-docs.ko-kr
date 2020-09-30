---
title: 도구 창 등록 | Microsoft Docs
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
ms.openlocfilehash: d7b82353247776eb2dac8135a0a412b396d571a1
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584718"
---
# <a name="register-a-tool-window"></a>도구 창 등록
및를 사용 하 여 도구 창을 등록할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> .

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

 위의 코드에서는 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> `PersistedWindowPane` Visual Studio를 사용 하 여 및 `DynamicWindowPane` 도구 창을 등록 합니다. 지속형 도구 창은 고정 되어 있고 **솔루션 탐색기**탭 하 고 동적 창에는 기본 시작 위치와 크기가 지정 됩니다. 동적 창이 일시적으로 수행 되어 시작할 때 생성 되지 않았음을 나타냅니다. 그러면 `DontForceCreate` 시스템 레지스트리의 키에 값이 기록 `ToolWindows` 됩니다. 자세한 내용은 [도구 창 표시 구성](../vs-2015/extensibility/tool-window-display-configuration.md?view=vs-2015&preserve-view=true)을 참조 하세요.