---
title: VSCodeWindowManager 개체 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindowManager
helpviewer_keywords:
- VsCodeWindowManager object
- views [Visual Studio SDK], VSCodeWindowManager object
ms.assetid: e313add5-afdb-4d8d-abd1-764e1fc10c44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e88885d339e55b7c3df1312b4a72c59d2959bbcc
ms.sourcegitcommit: ba966327498a0f67d2df2291c60b62312f40d1d3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93414347"
---
# <a name="vscodewindowmanager-object"></a>VSCodeWindowManager 개체

언어 서비스는 코드 창 관리자를 구현 하며 장식 (예: 드롭다운 모음) 관리를 담당 합니다. 자세한 내용은 [레거시 API를 사용 하 여 코드 창 사용자 지정](/previous-versions/visualstudio/visual-studio-2015/extensibility/customizing-code-windows-by-using-the-legacy-api?preserve-view=true&view=vs-2015)을 참조 하세요.

다음 표에서는 개체의 인터페이스를 보여 줍니다 `VSCodeWindowManager` .

|인터페이스|Description|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|코드 창에서 장식 (예: 드롭다운 모음)을 추가 하거나 제거할 수 있습니다.|