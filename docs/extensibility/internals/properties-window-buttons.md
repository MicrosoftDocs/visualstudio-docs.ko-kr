---
title: 속성 창 버튼 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aaa4db159ccb0ecf3d0e9c9243e23fcd0dacc455
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706167"
---
# <a name="properties-window-buttons"></a>속성 창 단추
개발 언어 및 제품 유형에 따라 **속성** 창의 도구 모음에 기본적으로 특정 단추가 표시됩니다. 모든 경우에 **분류된**, **알파벳화된**속성 및 **속성** **페이지** 단추가 표시됩니다. 시각적 C# 및 시각적 기본에서 **이벤트** 단추도 표시 됩니다. 특정 Visual C++ **프로젝트에서는 VC++ 메시지와** **VC 재정의** 단추가 표시됩니다. 다른 프로젝트 유형에 대한 추가 단추가 표시될 수 있습니다. **속성** 창의 단추에 대한 자세한 내용은 [속성 창](../../ide/reference/properties-window.md)을 참조하십시오.

## <a name="implementation-of-properties-window-buttons"></a>속성 창 단추 구현
 **범주화된** 단추를 클릭하면 Visual Studio는 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 포커스가 있는 개체의 인터페이스를 호출하여 해당 속성을 범주별로 정렬합니다. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>속성 창에 `IDispatch` 표시되는 개체에 **Properties** 구현됩니다.

 음수 값을 가진 11개의 미리 정의된 속성 범주가 있습니다. 사용자 지정 범주를 정의할 수 있지만 미리 정의된 범주와 구분하기 위해 양수 값을 할당하는 것이 좋습니다.

 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> 지정된 속성에 대 한 적절 한 속성 범주 값을 반환 합니다. 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> 범주 이름을 포함 하는 문자열을 반환 합니다. Visual Studio에서 표준 속성 범주 값을 알고 있으므로 사용자 지정 범주 값에 대한 지원만 제공하면 됩니다.

 **알파벳 화된** 단추를 클릭하면 속성이 이름별로 알파벳 순서로 표시됩니다. 이름은 지역화된 정렬 `IDispatch` 알고리즘에 따라 검색됩니다.

 **속성** 창이 열리면 **속성** 단추가 자동으로 선택됨으로 표시됩니다. 환경의 다른 부분에서는 동일한 단추가 표시되고 이를 클릭하여 **속성** 창을 표시할 수 있습니다.

 선택한 개체에 대해 구현되지 않으면 **속성 페이지** 단추를 사용할 수 없습니다. `ISpecifyPropertyPages` 속성 페이지에는 일반적으로 솔루션 및 프로젝트와 연관된 구성 종속 속성을 표시하지만 프로젝트 항목(예: Visual C++)과도 연결할 수 있습니다.

> [!NOTE]
> 관리되지 않는 코드를 사용하여 **속성** 창에 도구 모음 단추를 추가할 수 없습니다. 도구 모음 단추를 추가하려면 <xref:System.Windows.Forms.Design.PropertyTab>에서 파생되는 관리되는 개체를 만들어야 합니다.

## <a name="see-also"></a>참조
- [속성 확장](../../extensibility/internals/extending-properties.md)
