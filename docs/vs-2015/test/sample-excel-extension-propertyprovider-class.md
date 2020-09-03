---
title: '샘플 Excel 확장: PropertyProvider 클래스 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ae254f85b00c47ba00250641f7afe0a638ceabc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660431"
---
# <a name="sample-excel-extension-propertyprovider-class"></a>샘플 Excel 확장: PropertyProvider 클래스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 내부 클래스는 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> 클래스를 확장하며 UI(사용자 인터페이스) 테스트를 기록하고 확장하기 위한 속성 서비스를 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 요소에 제공합니다.

## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel 메서드
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A> 메서드는 속성 공급자가 제공된 컨트롤에 대해 제공할 수 있는 지원 수준을 나타내는 숫자를 반환합니다. 반환된 값이 클수록 속성 공급자의 컨트롤 지원 가능 수준도 높아집니다. 이 경우 메서드는 제공된 컨트롤의 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A> 속성 값을 확인합니다. 값이 “Excel”이고 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A>가 `CellElement`임을 나타내는 경우 메서드는 최고 값을 반환하고, 그렇지 않으면 지원이 제공되지 않음을 나타내는 0을 반환합니다.

## <a name="getpropertynames-method"></a>GetPropertyNames 메서드
 Excel 셀 컨트롤의 지원되는 속성에 대한 속성 이름 및 속성 설명자 사전을 반환합니다.

## <a name="getpropertydescriptor-method"></a>GetPropertyDescriptor 메서드
 이 속성은 된 속성 이름에 대해 미리 정의된 속성 설명자를 가져오기 위해 테스트 프레임워크에서 호출됩니다.

## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>GetPropertyValue 및 SetPropertyValue 메서드
 `GetPropertyValue` 메서드는 이 확장의 `Communicator` 클래스를 사용하여 Excel에서 속성 값을 반환합니다. `SetPropertyValue` 메서드는 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> 클래스 및 `Communicator` 구성 요소를 사용하여 속성 값을 설정합니다. 이러한 메서드는 테스트 프레임워크에서 호출됩니다.

## <a name="code-generation-customization-methods"></a>코드 생성 사용자 지정 메서드
 이러한 메서드는 이 확장에 대해 구현되지 않습니다. 따라서 `null`을 반환하거나 <xref:System.NotImplementedException>를 throw합니다.

## <a name="see-also"></a>관련 항목
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
 [Microsoft Excel을 지원하도록 코딩된 UI 테스트 및 작업 기록 확장](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
