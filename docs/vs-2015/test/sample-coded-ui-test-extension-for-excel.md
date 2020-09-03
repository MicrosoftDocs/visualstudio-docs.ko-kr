---
title: Excel용 샘플 코딩된 UI 테스트 확장 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c6075f9f95f7dc1d21db91936cf35c76f9b2e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672236"
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Excel용 샘플 코딩된 UI 테스트 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

샘플의 확장 구성 요소는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 코딩된 UI 테스트 프로세스에서 실행되며, 기본 수준에 `ExtensionPackage` 클래스가 있는 다소 계층적인 구조입니다. 다음 수준에는 `TechnologyManager`, `ActionFilter` 및 `PropertyProvider` 클래스가 있고 최상위 수준에는 컨트롤 요소가 있습니다.

 ![Excel 테스트 확장 아키텍처](../test/media/excel-extarch.png "Excel_ExtArch") Excel 확장 아키텍처

## <a name="extension-points"></a>확장점
 이러한 클래스는 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]에 대해 코딩된 UI 테스트를 사용할 수 있도록 샘플에서 구현되는 확장점을 나타냅니다.

### <a name="extensionpackage"></a>ExtensionPackage
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> 클래스에서 상속되는 이 클래스는 코딩된 UI 테스트 확장의 진입점입니다. 이 추상 클래스를 구현하면 코딩된 UI 테스트 프레임워크가 새 UI 테스트를 위한 UI 테스트 작업 필터, UI 테스트 속성 공급자 및 사용자 지정 UI 테스트 기술 관리자에 내부에서 액세스할 수 있습니다. 자세한 내용은 [ExtensionPackage 클래스](../test/sample-excel-extension-extensionpackage-class.md)를 참조하세요.

### <a name="technologymanager"></a>TechnologyManager
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> 클래스에서 상속되는 이 클래스는 테스트 기록 및 재상을 위한 기술 관리자를 제공합니다. 자세한 내용은 [TechnologyManager 클래스](../test/sample-excel-extension-technologymanager-class.md)를 참조하세요.

### <a name="actionfilter"></a>ActionFilter
 [Uitestactionfilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) 클래스에서 상속 되는이 클래스는 유사한 테스트 작업 결과를 단일 테스트 결과로 집계 하기 위한 기본 클래스를 제공 합니다. 자세한 내용은 [ActionFilter 클래스](../test/sample-excel-extension-actionfilter-class.md)를 참조하세요.

### <a name="technology-elements"></a>기술 요소
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 클래스에서 상속되는 기본 클래스는 기록 및 재생 가능한 UI 테스트의 기술 요소에 대한 토대를 제공합니다. 자세한 내용은 [Element 클래스](../test/sample-excel-extension-element-classes.md)를 참조하세요.

### <a name="propertyprovider"></a>PropertyProvider
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> 클래스에서 상속되는 이 클래스는 테스트 기록 및 재생을 위한 UI 요소의 속성을 지원하는 기본 클래스를 제공합니다. 자세한 내용은 [PropertyProvider 클래스](../test/sample-excel-extension-propertyprovider-class.md)를 참조하세요.

## <a name="see-also"></a>추가 정보

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [ExtensionPackage 클래스](../test/sample-excel-extension-extensionpackage-class.md)
- [TechnologyManager 클래스](../test/sample-excel-extension-technologymanager-class.md)
- [ActionFilter 클래스](../test/sample-excel-extension-actionfilter-class.md)
- [Element 클래스](../test/sample-excel-extension-element-classes.md)
- [PropertyProvider 클래스](../test/sample-excel-extension-propertyprovider-class.md)
