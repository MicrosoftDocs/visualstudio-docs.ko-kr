---
title: 레거시 언어 서비스 인터페이스 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707377"
---
# <a name="legacy-language-service-interfaces"></a>레거시 언어 서비스 인터페이스
특정 프로그래밍 언어의 경우 한 번에 하나의 언어 서비스 인스턴스만 있을 수 있습니다. 그러나 단일 언어 서비스에서는 두 개 이상의 편집기를 사용할 수 있습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 언어 서비스를 특정 편집기와 연결 하지 않습니다. 따라서 언어 서비스 작업을 요청 하는 경우 매개 변수로 적절 한 편집기를 식별 해야 합니다.

## <a name="common-interfaces-associated-with-language-services"></a>언어 서비스와 연결 된 공통 인터페이스
 편집기는 해당 VSPackage에서를 호출 하 여 언어 서비스를 가져옵니다 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> . 이 호출에 전달 된 서비스 ID (SID)는 요청 되는 언어 서비스를 식별 합니다.

 여러 개별 클래스에서 핵심 언어 서비스 인터페이스를 구현할 수 있습니다. 그러나 일반적인 방법은 단일 클래스에서 다음 인터페이스를 구현 하는 것입니다.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock>(선택 사항)

  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>모든 언어 서비스에서 인터페이스를 구현 해야 합니다. 언어 서비스에 대 한 정보 (예: 언어의 지역화 된 이름, 언어 서비스와 연결 된 파일 이름 확장명 및 svc를 검색 하는 방법)를 제공 합니다.

## <a name="additional-language-service-interfaces"></a>추가 언어 서비스 인터페이스
 다른 인터페이스는 언어 서비스와 함께 제공 될 수 있습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 텍스트 버퍼의 각 인스턴스에 대해 이러한 인터페이스의 개별 인스턴스를 요청 합니다. 따라서 이러한 각 인터페이스를 자체 개체에 구현 해야 합니다. 다음 표에서는 텍스트 버퍼 인스턴스당 하나의 인스턴스가 필요한 인터페이스를 보여 줍니다.

|인터페이스|설명|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|드롭다운 표시줄과 같은 코드 창 장식을 관리 합니다. 메서드를 사용 하 여이 인터페이스를 가져올 수 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>코드 창 마다 하나씩 있습니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|언어 키워드와 구분 기호를 색으로 합니다. 메서드를 사용 하 여이 인터페이스를 가져올 수 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 는 그리기 타임에 호출 됩니다. 내에서 계산 집약적인 작업을 수행 하지 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 않거나 성능이 저하 될 수 있습니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|IntelliSense 매개 변수 도구 설명을 제공 합니다. 언어 서비스에서 열기 괄호와 같이 메서드 데이터를 표시 해야 함을 나타내는 문자를 인식 하는 경우 메서드를 호출 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 언어 서비스가 매개 변수 정보 도구 설명을 표시할 준비가 되었음을 텍스트 뷰에 알립니다. 그런 다음 텍스트 뷰는 인터페이스의 메서드를 사용 하 여 언어 서비스를 다시 호출 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 도구 설명을 표시 하는 데 필요한 정보를 가져옵니다.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|IntelliSense 문 완성 기능을 제공 합니다. 언어 서비스가 완성 목록을 표시할 준비가 되 면 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 텍스트 보기에서 메서드를 호출 합니다. 그런 다음 텍스트 뷰는 개체의 메서드를 사용 하 여 언어 서비스로 다시 호출 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> .|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|명령 처리기를 사용 하 여 텍스트 뷰를 수정할 수 있습니다. 인터페이스를 구현 하는 클래스 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 도 인터페이스를 구현 해야 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . 텍스트 뷰는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> 메서드에 전달 되는 개체를 쿼리하여 개체를 검색 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> . <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>각 뷰에 대해 하나의 개체가 있어야 합니다.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|사용자가 코드 창에 입력 하는 명령을 차단 합니다. 구현에서 출력 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 을 모니터링 하 여 사용자 지정 완료 정보 및 보기 수정 제공<br /><br /> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>개체를 텍스트 뷰에 전달 하려면를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 합니다.|

## <a name="see-also"></a>추가 정보
- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
- [검사 목록: 레거시 언어 서비스 만들기](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
