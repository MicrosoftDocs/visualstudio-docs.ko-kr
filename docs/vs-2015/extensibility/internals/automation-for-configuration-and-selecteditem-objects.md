---
title: 구성 및 SelectedItem 개체에 대 한 자동화 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42faf8127c1ab70d3470aa497a0cdab6058060f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157252"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>구성 SelectedItem 개체 자동화
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

에서 빌드 및 선택한 항목 프로세스를 자동화할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="automation-for-builds"></a>빌드에 대 한 자동화  
 빌드 또는 구성에는를 구현할 때 제공 되는 자동화 모델이 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . 자세한 내용은 [빌드 구성 이해](../../ide/understanding-build-configurations.md)를 참조하세요.  
  
 VSPackage을 만들고 구성 옵션을 제어 하려면 자동화 모델을 사용 해야 합니다.  
  
## <a name="automation-for-selecteditem"></a>SelectedItem에 대 한 자동화  
 `SelectedItem`Visual Studio에는 표준 구현이 포함 되어 있으므로 개체에 대 한 구현을 제공할 필요가 없습니다. 그러나 원하는 경우 개체를 구현할 수 있습니다 `SelectedItem` . 인터페이스를 포함 하는 개체를 구현 하 `SelectedItem` 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> VSITEMID가로 설정 된 상태에서 메서드에 대 한 호출에 대 한 응답을 반환 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [자동화 모델에 기여](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [빌드 구성 이해](../../ide/understanding-build-configurations.md)
