---
title: 속성 표시 그리드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5fd5e17d764336cda450c726023b209f89f194a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180389"
---
# <a name="properties-display-grid"></a>속성 표시 그리드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**속성** 창에는 그리드 내의 필드가 표시 됩니다. 왼쪽 열에는 속성 이름이 포함 됩니다. 오른쪽 열에는 속성 값이 포함 됩니다.  
  
## <a name="working-with-the-grid"></a>표 작업  
 두 열 목록은 디자인 타임에 변경 될 수 있는 구성 독립적 속성과 현재 설정을 보여 줍니다. 모든 속성은 표시 되지 않을 수 있습니다. 예를 들어 메서드를 구현 하 여 속성을 숨김으로 설정할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> . 특히 자식 속성이 있는 속성을 숨기려면 [자식 속성이 있는 속성](../../misc/hiding-properties-that-have-child-properties.md)을 숨깁니다.  
  
 **속성** 창에 정보를 푸시하는 IDE는를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 는 **속성** 창에 표시 되는 관련 속성이 포함 된 선택 가능한 개체를 포함 하는 각 창에 대해 vspackage에 의해 호출 됩니다. **Solution Explorer** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> `GetProperty` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 계층 구조에서 browseable 개체를 얻기 위해 프로젝트 계층 구조에서를 사용 하 여를 호출 하는 솔루션 탐색기의 구현입니다.  
  
 VSPackage에서을 지원 하지 않는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> IDE는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 계층 항목이 제공 하는 값을 사용 하 여를 사용 하려고 시도 합니다.  
  
 프로젝트 VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 을 구현 하는 IDE 제공 창 패키지 (예: **솔루션 탐색기**)가 대신 생성 하기 때문에 프로젝트를 만들 필요가 없습니다 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 는 IDE에 의해 호출 되는 세 가지 메서드로 구성 됩니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>**속성** 창에 표시 되도록 선택 된 개체의 수를 포함 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>`IDispatch` **속성** 창에 표시 되도록 선택 된 개체를 반환 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> 에서 반환 하는 개체를 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 사용자가 선택할 수 있도록 합니다. 이렇게 하면 VSPackage가 UI에서 사용자에 게 표시 되는 선택 항목을 시각적으로 업데이트할 수 있습니다.  
  
  **속성** 창은 개체에서 정보를 추출 `IDispatch` 하 여 검색할 속성을 검색 합니다. 속성 브라우저는를 사용 하 여 `IDispatch` 에서 가져온 쿼리를 통해 지원 되는 속성을 개체에 요청 합니다 `ITypeInfo` `IDispatch::GetTypeInfo` . 그런 다음 브라우저는 이러한 값을 사용 하 여 **속성** 창을 채우고 표에 표시 된 개별 속성의 값을 변경 합니다. 속성 정보는 개체 자체 내에서 유지 관리 됩니다.  
  
  반환 된 개체가를 지원 하기 때문에 `IDispatch` 호출자는 또는를 호출 하 고 `IDispatch::Invoke` `ITypeInfo::Invoke` 원하는 정보를 나타내는 미리 정의 된 디스패치 식별자 (DISPID)를 사용 하 여 개체 이름과 같은 정보를 얻을 수 있습니다. 선언 된 Dispid는 사용자 정의 식별자와 충돌 하지 않도록 음수입니다.  
  
  **속성** 창에는 선택한 개체의 특정 속성 특성에 따라 다른 유형의 필드가 표시 됩니다. 이러한 필드에는 편집 상자, 드롭다운 목록 및 사용자 지정 편집기 대화 상자에 대 한 링크가 포함 됩니다.  
  
- 열거 된 목록에 포함 된 값은에 대 한 쿼리에 의해 검색 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> `IDispatch` . 열거 된 목록에서 가져온 값은 속성 표에서 필드 이름을 두 번 클릭 하거나 값을 클릭 하 고 드롭다운 목록에서 새 값을 선택 하 여 변경할 수 있습니다. 열거 된 목록에서 설정을 미리 정의한 속성의 경우 속성 목록에서 속성 이름을 두 번 클릭 하면 사용 가능한 선택 항목이 순환 됩니다. True/false와 같이 선택 항목을 두 개만 포함 하는 미리 정의 된 속성의 경우 속성 이름을 두 번 클릭 하 여 선택 항목 사이를 전환 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A>값이 변경 되었음을 나타내는가 이면 `false` 값이 굵은 텍스트로 표시 됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> 값을 원래 값으로 다시 설정할 수 있는지 여부를 확인 하는 데 사용 됩니다. 이 경우 값을 마우스 오른쪽 단추로 클릭 하 고 표시 된 메뉴에서 **다시 설정** 을 선택 하 여 기본값으로 다시 변경할 수 있습니다. 그렇지 않으면 값을 다시 기본값으로 다시 변경 해야 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 를 사용 하면 디자인 타임에 표시 되는 속성 이름을 지역화 하 고 숨길 수도 있지만 런타임에 표시 되는 속성 이름에는 영향을 주지 않습니다.  
  
- 줄임표 (...) 단추를 클릭 하면 사용자가 선택할 수 있는 속성 값의 목록 (예: 색 선택 또는 글꼴 목록)이 표시 됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> 는 이러한 값을 제공 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [속성 확장](../../extensibility/internals/extending-properties.md)
