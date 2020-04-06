---
title: 옵션 페이지에 대한 자동화 지원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe45238948d5b4cdebbf9f002f6b242515e7622e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709925"
---
# <a name="automation-support-for-options-pages"></a>옵션 페이지에 대한 자동화 지원
VSPackages는 **도구** 메뉴(도구**옵션** 페이지)에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자 지정 **옵션** 대화 상자를 제공하고 자동화 모델에서 사용할 수 있도록 할 수 있습니다.

## <a name="tools-options-pages"></a>도구 옵션 페이지
 **도구 옵션** 페이지를 만들려면 VSPackage 메서드의 구현을 통해 환경에 반환 되는 사용자 컨트롤 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 구현을 제공 해야 합니다. (또는 관리 코드의 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 메서드입니다.

 자동화 모델을 통해 이 새 페이지에 액세스할 수 있도록 허용하는 것은 선택 사항이지만 강력하게 권장됩니다. 다음 단계를 수행하면 됩니다.

1. IDispatch <xref:EnvDTE._DTE.Properties%2A> 파생 개체의 구현을 통해 개체를 확장합니다.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 메서드(또는 메서드관리 코드)의 <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> 구현을 IDispatch 파생 개체에 반환합니다.

3. 자동화 소비자가 사용자 <xref:EnvDTE._DTE.Properties%2A> 지정 **Option** 속성 페이지에서 메서드를 호출하는 경우 환경은 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 사용하여 사용자 지정 도구 **옵션** 페이지의 자동화 구현을 가져옵니다.

4. 그런 다음 VSPackage의 자동화 개체를 <xref:EnvDTE.Property> 사용하여 <xref:EnvDTE._DTE.Properties%2A>에서 반환된 각 개체를 제공합니다.

   사용자 지정 도구 **옵션** 페이지를 구현하는 샘플은 [VSSDK 샘플을](https://github.com/Microsoft/VSSDK-Extensibility-Samples)참조하십시오.

## <a name="see-also"></a>참조
- [프로젝트 객체 노출](../../extensibility/internals/exposing-project-objects.md)
