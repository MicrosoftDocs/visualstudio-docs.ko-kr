---
title: 속성 창 단추 | Microsoft Docs
description: 속성 창 도구 모음에 기본적으로 표시되는 단추와 단추 구현에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a9c45d6cf0f271683c3c708bd71ef46377a5c5ca
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903452"
---
# <a name="properties-window-buttons"></a>속성 창 단추
개발 언어 및 제품 유형에 따라 속성 **창의** 도구 모음에 특정 단추가 기본적으로 표시됩니다. 모든 경우에 **범주화**, **사전순**, **속성** 및 **속성 페이지** 단추가 표시됩니다. Visual C# 및 Visual Basic **이벤트** 단추도 표시됩니다. 특정 Visual C++ **프로젝트에서는 VC++ 메시지** 및 **VC 재정의** 단추가 표시됩니다. 다른 프로젝트 형식에 대한 추가 단추가 표시될 수 있습니다. 속성 창의 단추에 대한 자세한 내용은 **속성** 창 을 [참조하세요.](../../ide/reference/properties-window.md)

## <a name="implementation-of-properties-window-buttons"></a>속성 창 단추 구현
 **범주화된** 단추를 클릭하면 Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 포커스가 있는 개체에서 인터페이스를 호출하여 해당 속성을 범주별로 정렬합니다. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>`IDispatch` **는 속성** 창에 표시되는 개체에서 구현됩니다.

 음수 값을 갖는 11가지 미리 정의된 속성 범주가 있습니다. 사용자 지정 범주를 정의할 수 있지만 미리 정의된 범주와 구분하기 위해 양수 값을 할당하는 것이 좋습니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A>메서드는 지정된 속성에 대한 적절한 속성 범주 값을 반환합니다. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>메서드는 범주 이름을 포함하는 문자열을 반환합니다. Visual Studio 표준 속성 범주 값을 알고 있으므로 사용자 지정 범주 값만 지원하면 됩니다.

 **사전순** 단추를 클릭하면 속성이 이름별로 사전순으로 표시됩니다. 이름은 `IDispatch` 지역화된 정렬 알고리즘에 따라 에 의해 검색됩니다.

 **속성** 창이 열리면 **속성** 단추가 선택된 대로 자동으로 표시됩니다. 환경의 다른 부분에서는 동일한 단추가 표시되며, 이 단추를 클릭하여 **속성** 창을 표시할 수 있습니다.

 선택한 개체에 대해 가 구현되지 않은 경우 **속성 페이지** 단추를 사용할 수 `ISpecifyPropertyPages` 없습니다. 속성 페이지에는 일반적으로 솔루션 및 프로젝트와 연결된 구성 종속 속성이 표시되지만 프로젝트 항목(예: Visual C++)과도 연결될 수 있습니다.

> [!NOTE]
> 관리되지 않는 코드를 사용하여 **속성** 창에 도구 모음 단추를 추가할 수 없습니다. 도구 모음 단추를 추가하려면 에서 파생되는 관리되는 개체를 만들어야 <xref:System.Windows.Forms.Design.PropertyTab> 합니다.

## <a name="see-also"></a>참조
- [속성 확장](../../extensibility/internals/extending-properties.md)
