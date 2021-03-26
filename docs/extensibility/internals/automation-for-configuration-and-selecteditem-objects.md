---
title: 구성 및 SelectedItem 개체에 대 한 자동화 | Microsoft Docs
description: 셸 Interop에서 구성 및 SelectedItem 개체를 사용 하 여 Visual Studio 빌드 및 선택한 항목 프로세스를 자동화 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9f6e7f153e7d5b32e54cc51e3b7af06f14545cea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086263"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>구성 및 SelectedItem 개체에 대 한 자동화

Visual Studio에서 빌드 및 선택한 항목 프로세스를 자동화할 수 있습니다.

## <a name="automation-for-builds"></a>빌드에 대 한 자동화

빌드 또는 구성에는를 구현할 때 제공 되는 자동화 모델이 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . 자세한 내용은 [빌드 구성 이해](../../ide/understanding-build-configurations.md)를 참조하세요.

VSPackage을 만들고 구성 옵션을 제어 하려면 자동화 모델을 사용 해야 합니다.

## <a name="automation-for-selecteditem"></a>SelectedItem에 대 한 자동화

`SelectedItem`Visual Studio에는 표준 구현이 포함 되어 있으므로 개체에 대 한 구현을 제공할 필요가 없습니다. 그러나 원하는 경우 개체를 구현할 수 있습니다 `SelectedItem` . 인터페이스를 포함 하는 개체를 구현 하 `SelectedItem` 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> `VSITEMID` __VSHPROPID로 설정 된를 사용 하 여 메서드에 대 한 호출에 대 한 응답을 반환 해야 합니다 [. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [자동화 모델에 기여](../../extensibility/internals/contributing-to-the-automation-model.md)
- [빌드 구성 이해](../../ide/understanding-build-configurations.md)
