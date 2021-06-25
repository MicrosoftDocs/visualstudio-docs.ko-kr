---
title: VSCodeWindowManager 개체 | Microsoft Docs
description: '장식 관리(예: 드롭다운 막대)를 담당하는 VSCodeWindowManager 개체에 대해 알아봅니다.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 76ab3d2a72c957b20a79850dc312f5c16de98afc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905295"
---
# <a name="vscodewindowmanager-object"></a>VSCodeWindowManager 개체

언어 서비스는 코드 창 관리자를 구현하고 장식(예: 드롭다운 막대)을 관리합니다. 자세한 내용은 [레거시 API를 사용하여 코드 창 사용자 지정을 참조하세요.](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015)

다음 표에서는 개체의 인터페이스를 `VSCodeWindowManager` 보여줍니다.

|인터페이스|설명|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|코드 창에서 장식(예: 드롭다운 막대)을 추가하거나 제거할 수 있습니다.|