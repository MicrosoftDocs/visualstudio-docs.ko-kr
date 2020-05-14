---
title: 구성 및 선택 항목 개체에 대한 자동화 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0341cdf56b32b8b1ac77104b3f3e813ae0610767
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709967"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>구성 및 선택항목 개체에 대한 자동화

Visual Studio에서 빌드 및 선택한 항목 프로세스를 자동화할 수 있습니다.

## <a name="automation-for-builds"></a>빌드를 위한 자동화

빌드 또는 구성에는 을 구현할 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>때 제공되는 자동화 모델이 있습니다. 자세한 내용은 [빌드 구성 이해](../../ide/understanding-build-configurations.md)를 참조하세요.

VSPackage를 만들고 구성 옵션을 제어하려면 자동화 모델을 사용해야 합니다.

## <a name="automation-for-selecteditem"></a>선택된 항목에 대한 자동화항목

Visual Studio에는 표준 구현이 `SelectedItem` 포함되어 있으므로 개체에 대한 구현을 제공할 필요가 없습니다. 그러나 원하는 경우 `SelectedItem` 개체를 구현할 수 있습니다. `SelectedItem` 인터페이스를 포함하는 개체를 구현하고 __VSHPROPID `VSITEMID` 설정된 메서드에 대한 호출에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 대한 응답을 반환해야 [합니다. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [자동화 모델에 기여](../../extensibility/internals/contributing-to-the-automation-model.md)
- [빌드 구성 이해](../../ide/understanding-build-configurations.md)
