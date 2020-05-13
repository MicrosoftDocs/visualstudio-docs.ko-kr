---
title: 레거시 언어 서비스 인터페이스 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89d80d6961f5eaf91721567ccb0efa73bbe31406
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707377"
---
# <a name="legacy-language-service-interfaces"></a>레거시 언어 서비스 인터페이스
특정 프로그래밍 언어의 경우 한 번에 언어 서비스의 인스턴스가 하나만 있을 수 있습니다. 그러나 단일 언어 서비스는 두 개 이상의 편집기에서 서비스를 제공할 수 있습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]언어 서비스를 특정 편집기와 연결하지 않습니다. 따라서 언어 서비스 작업을 요청할 때 적절 한 편집기 매개 변수로 식별 해야 합니다.

## <a name="common-interfaces-associated-with-language-services"></a>언어 서비스와 관련된 공통 인터페이스
 편집기는 적절한 VSPackage를 호출하여 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 언어 서비스를 가져옵니다. 이 호출에서 전달된 서비스 ID(SID)는 요청되는 언어 서비스를 식별합니다.

 여러 개의 개별 클래스에서 핵심 언어 서비스 인터페이스를 구현할 수 있습니다. 그러나 일반적인 방법은 단일 클래스에서 다음 인터페이스를 구현하는 것입니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock>(선택 사항)

  인터페이스는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 모든 언어 서비스에서 구현되어야 합니다. 언어의 지역화된 이름, 언어 서비스와 연결된 파일 이름 확장명 및 색칠하기를 검색하는 방법과 같은 언어 서비스에 대한 정보를 제공합니다.

## <a name="additional-language-service-interfaces"></a>추가 언어 서비스 인터페이스
 다른 인터페이스는 언어 서비스와 함께 제공 될 수 있습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]은 텍스트 버퍼의 각 인스턴스에 대해 이러한 인터페이스의 별도의 인스턴스를 요청합니다. 따라서 이러한 각 인터페이스를 자체 개체에 구현 해야 합니다. 다음 표에서는 텍스트 버퍼 인스턴스당 하나의 인스턴스가 필요한 인터페이스를 보여 줍니다.

|인터페이스|설명|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|드롭다운 막대와 같은 코드 창 장식을 관리합니다. 메서드를 사용 하 여이 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> 얻을 수 있습니다. 코드 창당 1개씩 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> 있습니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|언어 키워드와 구분기호를 색칠합니다. 메서드를 사용 하 여이 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 얻을 수 있습니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>페인트 시간에 호출됩니다. 내부의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 계산 집약적인 작업이나 성능저하를 방지합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|IntelliSense 매개 변수 도구 설명서를 제공합니다. 언어 서비스가 열린 괄호와 같이 메서드 데이터가 표시되어야 한다는 문자를 인식하면 언어 서비스가 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 매개 변수 정보 ToolTip을 표시할 준비가 되었음을 텍스트 보기에 알리는 메서드를 호출합니다. 그런 다음 텍스트 뷰는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 인터페이스의 메서드를 사용하여 도구 설명에 필요한 정보를 얻도록 하여 언어 서비스로 다시 호출합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|IntelliSense 문 완료를 제공합니다. 언어 서비스가 완료 목록을 표시할 준비가 되면 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 텍스트 보기에서 메서드를 호출합니다. 그런 다음 텍스트 뷰는 개체의 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 사용하여 언어 서비스로 다시 호출합니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|명령 처리기를 사용하여 텍스트 보기를 수정할 수 있습니다. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 인터페이스를 구현하는 클래스도 인터페이스를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 구현해야 합니다. 텍스트 뷰는 메서드에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 전달되는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 개체를 쿼리하여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 개체를 검색합니다. 각 뷰에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 대해 하나의 개체가 있어야 합니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|사용자가 코드 창에 입력하는 명령을 차단합니다. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 구현에서 출력을 모니터링하여 사용자 지정 완료 정보를 제공하고 수정 사항을 확인합니다.<br /><br /> 개체를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 텍스트 보기로 전달하려면 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>을 호출합니다.|

## <a name="see-also"></a>참조
- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
- [검사 목록: 레거시 언어 서비스 만들기](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
