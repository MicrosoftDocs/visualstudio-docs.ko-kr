---
title: 속성 표시 그리드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d094c32ba8a64fc636f3fb6dfb2944dc3955628a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706182"
---
# <a name="properties-display-grid"></a>속성 표시 표

**속성** 창은 그리드 내의 필드를 표시합니다. 왼쪽 열에는 속성 이름이 포함되어 있습니다. 오른쪽 열에는 속성 값이 포함됩니다.

## <a name="work-with-the-grid"></a>그리드로 작업

두 열 목록에는 디자인 타임과 현재 설정에서 변경할 수 있는 구성 독립적 속성이 표시됩니다. 모든 속성이 표시되지 않을 수 있습니다. 예를 들어 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> 메서드를 구현하여 속성을 숨김으로 설정할 수 있습니다. 특히 자식 속성이 있는 속성을 숨기려면 다음을 수행합니다.

1. 매개 `pfDisplay` 변수를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> `FALSE`에 설정합니다.

2. 매개 `pfHide` 변수를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> `TRUE`에 설정합니다.

**속성** 창에 정보를 푸시하기 위해 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>IDE는 을 사용합니다. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>**속성** 창에 표시할 관련 속성이 있는 선택 가능한 개체를 포함하는 각 창에 대해 VSPackage에서 호출됩니다. **솔루션 탐색기의** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> __VSHPROPID `GetProperty` 사용하여 호출을 [구현합니다. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)프로젝트 계층에서 VSHPROPID_BrowseObject 계층에서 찾아볼 수 있는 개체를 획득합니다.

VSPackage가 __VSHPROPID 지원하지 않는 [경우. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)IDE는 __VSHPROPID <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 값을 사용하여 사용하려고 시도합니다. [ 계층](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) 구조 항목 또는 항목이 제공하는 VSHPROPID_SelContainer.

프로젝트 VSPackage를 구현 하는 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> IDE 제공 된 창 패키지 (예: **솔루션 탐색기)** 대신 구성 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 하기 때문에 만들 필요가 없습니다.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>IDE에서 호출하는 세 가지 메서드로 구성됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>속성 **창에** 표시할 선택한 개체 수가 포함됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>은 `IDispatch` **속성** 창에 표시할 선택된 객체를 반환합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>을 사용하면 반환된 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 모든 개체가 사용자가 선택할 수 있습니다. 이렇게 하면 VSPackageUI에서 사용자에 게 표시 된 선택 을 시각적으로 업데이트할 수 있습니다.

**속성** 창은 `IDispatch` 개체에서 정보를 추출하여 찾아볼 속성을 검색합니다. 속성 브라우저는 `IDispatch` 에서 가져온 쿼리를 `ITypeInfo`통해 개체에 지원하는 속성을 `IDispatch::GetTypeInfo`묻는 데 사용합니다. 그런 다음 브라우저는 이러한 값을 사용하여 **속성** 창을 채우고 그리드에 표시되는 개별 속성의 값을 변경합니다. 속성 정보는 개체 자체 내에서 유지됩니다.

반환된 개체가 `IDispatch`지원되므로 호출자는 원하는 정보를 나타내는 미리 정의된 `IDispatch::Invoke` `ITypeInfo::Invoke` 디스패치 식별자(DISPID)를 호출하거나 개체 이름과 같은 정보를 가져올 수 있습니다. 선언된 DISPID는 사용자 정의 식별자와 충돌하지 않도록 음수입니다.

**속성** 창은 선택한 개체의 특정 속성 특성에 따라 다양한 유형의 필드를 표시합니다. 이러한 필드에는 편집 상자, 드롭다운 목록 및 사용자 지정 편집기 대화 상자에 대한 링크가 포함됩니다.

- 나열된 목록에 포함된 값은 에 대한 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 쿼리에서 `IDispatch`검색됩니다. 열거된 목록에서 얻은 값은 필드 이름을 두 번 클릭하거나 값을 클릭하고 드롭다운 목록에서 새 값을 선택하여 속성 표에서 변경할 수 있습니다. 열거된 목록에서 미리 정의된 설정이 있는 속성의 경우 속성 목록에서 속성 이름을 두 번 클릭하여 사용 가능한 선택 사항을 순환합니다. true/false와 같이 두 가지 선택 사항만 있는 미리 정의된 속성의 경우 속성 이름을 두 번 클릭하여 선택 항목 간에 전환합니다.

- 값이 변경되었음을 나타내는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> 값이 굵은 텍스트로 표시됩니다. `false` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>은 값을 원래 값으로 재설정할 수 있는지 여부를 결정하는 데 사용됩니다. 이 경우 값을 마우스 오른쪽 단추로 클릭하고 표시된 메뉴에서 **재설정을** 선택하여 기본값으로 다시 변경할 수 있습니다. 그렇지 않으면 값을 수동으로 기본값으로 다시 변경해야 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>또한 디자인 시간 동안 표시되는 속성 의 이름을 지역화하고 숨길 수 있지만 런타임 중에 표시되는 속성 이름에는 영향을 주지 않습니다.

- 타원(...) 버튼을 클릭하면 사용자가 선택할 수 있는 속성 값 목록(예: 색상 선택기 또는 글꼴 목록)이 표시됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>은 이러한 값을 제공합니다.

## <a name="see-also"></a>참조

- [속성 확장](../../extensibility/internals/extending-properties.md)
