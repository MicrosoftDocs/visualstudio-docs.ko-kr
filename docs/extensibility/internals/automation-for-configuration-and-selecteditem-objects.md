---
title: Configuration 및 SelectedItem 개체 | 자동화 Microsoft Docs
description: Shell Interop에서 Configuration 및 SelectedItem 개체를 사용하여 Visual Studio 빌드 및 선택한 항목 프로세스를 자동화하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a95fc06c5d84a936cdb1ada3369f584381dfe7f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901632"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Configuration 및 SelectedItem 개체에 대한 자동화

Visual Studio 빌드 및 선택한 항목 프로세스를 자동화할 수 있습니다.

## <a name="automation-for-builds"></a>빌드 자동화

빌드 또는 구성에는 를 구현할 때 제공되는 자동화 모델이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> 있습니다. 자세한 내용은 [빌드 구성 이해](../../ide/understanding-build-configurations.md)를 참조하세요.

VSPackage를 만들고 구성 옵션을 제어하려면 자동화 모델을 사용해야 합니다.

## <a name="automation-for-selecteditem"></a>SelectedItem에 대한 Automation

Visual Studio 표준 구현을 포함하기 때문에 개체에 대한 구현을 제공할 필요가 `SelectedItem` 없습니다. 그러나 원하는 경우 개체를 구현할 수 `SelectedItem` 있습니다. 인터페이스를 포함하는 개체를 구현하고 가 `SelectedItem` __VSHPROPID 로 설정된 메서드 호출에 대한 응답을 반환해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> `VSITEMID` [합니다. 를 VSHPROPID_ExtSelectedItem.](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>)

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [자동화 모델에 기여](../../extensibility/internals/contributing-to-the-automation-model.md)
- [빌드 구성 이해](../../ide/understanding-build-configurations.md)
