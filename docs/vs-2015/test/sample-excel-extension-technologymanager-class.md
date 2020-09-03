---
title: '샘플 Excel 확장: TechnologyManager 클래스 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac9a4517fcf13dbb0e1d7a6f994092168723e660
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672159"
---
# <a name="sample-excel-extension-technologymanager-class"></a>샘플 Excel 확장: TechnologyManager 클래스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 클래스는 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> 클래스를 확장하고 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] 확장용 핵심 서비스를 제공합니다. 기본 클래스에는 여러 가지 메서드가 있지만, 이 샘플에서는 이러한 메서드 중 일부만 사용합니다.

 일부 메서드는 속성 값만 반환합니다. 개발자는 대부분의 메서드를 통해 코딩된 UI 테스트 엔진에서 기본적으로 제공되는 기본 알고리즘을 재정의할 수 있습니다. 이러한 메서드는 <xref:System.NotSupportedException>를 throw하거나 `null`을 반환하여 기본 알고리즘을 사용하도록 프레임워크에 알립니다.

 기본 기술의 복잡도에 따라서는 기술 관리자 코드를 개발하는 데 몇 주에서 몇 달까지 걸릴 수 있습니다. Excel에서는 매우 포괄적으로 활용 가능한 기술 관리자를 만들 수 있습니다. 이 예제에서는 의도적으로 Excel 워크시트 및 셀만 사용하며 제한된 서식을 사용합니다.

 기술 관리자 코드는 가능한 경우 `Communicator` 클래스를 통해 열리는 .NET Remoting 채널을 사용하여 Excel 프로세스에서 실행되는 추가 기능에서 정보를 추출합니다.

## <a name="com-visibility"></a>COM 표시 여부
 이 클래스와 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 클래스를 확장하는 각 요소 클래스에는 모두 값이 `true`인 <xref:System.Runtime.InteropServices.ComVisibleAttribute>가 포함되어 있습니다. 이 속성을 통해 이러한 클래스가 COM에 표시됩니다.

## <a name="technologyname-property"></a>TechnologyName 속성
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> 속성의 이 재정의는 확장의 기타 모든 구성 요소에 대한 기본 기술을 식별하는 고유하고 의미 있는 이름을 제공해야 합니다. 이 확장의 경우 값은 "Excel"입니다.

## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel 메서드
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> 메서드의 이 재정의는 제공된 핸들로 표시되는 컨트롤에 대해 기술 관리자가 제공할 수 있는 기술 수준을 나타내는 숫자를 반환합니다. 반환된 값이 클수록 기술 관리자의 컨트롤 지원 가능 수준도 높아집니다. 이 문서의 예제에서는 메서드가 컨트롤이 포함된 창을 확인하여 컨트롤이 Excel 워크시트이면 최고 값을 반환하고, 그렇지 않으면 지원이 제공되지 않음을 나타내는 0을 반환합니다.

## <a name="methods-to-get-an-element"></a>요소를 가져오는 메서드
 코딩된 UI 테스트 프레임워크는 몇 가지 중요한 메서드를 사용하여 핸들, 화면의 점 또는 다른 기술의 요소를 제공해 기술과 관련된 요소를 가져옵니다. 이러한 메서드에 해당하는 코드에는 설명이 포함되어 있습니다. 기본 메서드는 다음과 같습니다.

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>

## <a name="parsequeryid-method"></a>ParseQueryId 메서드
 코딩된 UI 테스트를 만들 때 사용자는 테스트의 일부 또는 모든 컨트롤에 대해 속성 값을 지정할 수 있습니다. 이러한 속성 값은 테스트 프레임워크가 테스트 중에 특정 UI 컨트롤을 찾는 데 사용하는 검색 속성이라는 이름/값 쌍을 만드는 데 사용됩니다. 모든 검색 속성은 기술 내 모든 요소의 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> 속성 값을 나타냅니다. 여기에는 모든 컨트롤도 포함됩니다. 테스트 중에는 컨트롤을 여러 번 확인해야 할 수 있으므로, 기술 관리자는 이 메서드를 사용하여 지정된 컨트롤의 검색 속성 구문 분석을 최적화할 수 있습니다. 또한 이 메서드는 프레임워크가 해당 컨트롤의 후속 검색에 사용할 수 있는 쿠키도 반환합니다. 메서드의 이 구현은 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> 메서드를 사용하여 검색 속성을 구문 분석합니다.

## <a name="matchelement-method"></a>MatchElement 메서드
 기술 관리자를 사용한 컨트롤 검색을 수행하려는 경우 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> 메서드를 구현하여 가능한 일치 항목 배열을 반환하거나, 프레임워크가 자체 검색 알고리즘을 사용하도록 지시하는 <xref:System.NotSupportedException>을 throw할 수 있습니다. 어떤 방법을 사용하든 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> 메서드를 구현해야 합니다. 이 메서드에서도 이 구현은 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> 메서드를 사용합니다.

## <a name="navigation-methods"></a>탐색 메서드
 이러한 메서드는 UI 계층에서 제공되는 요소의 부모, 자식 또는 형제를 가져옵니다. 코드는 간단하며 명확하게 주석 처리되어 있습니다.

## <a name="getexcelelement-internal-method"></a>GetExcelElement 내부 메서드
 이 내부 메서드는 Excel 요소에 대한 정보와 창 핸들을 가져오며 요청된 Excel 요소를 반환합니다.

## <a name="see-also"></a>관련 항목
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> <xref:System.NotSupportedException>
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>
 [Microsoft Excel을 지원하도록 코딩된 UI 테스트 및 작업 기록 확장](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
