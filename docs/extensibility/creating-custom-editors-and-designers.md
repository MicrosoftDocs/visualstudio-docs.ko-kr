---
title: 사용자 지정 편집자 및 디자이너 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9f56b82225e1e40782b6753bea03d3c1780f596
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739479"
---
# <a name="create-custom-editors-and-designers"></a>사용자 지정 편집기 및 디자이너 만들기

Visual Studio 통합 개발 환경(IDE)은 다음과 같은 다양한 유형의 편집기와 호스트할 수 있습니다.

- 비주얼 스튜디오 코어 편집기

- 사용자 지정 편집기

- 외부 편집자

- 디자이너

다음 정보는 필요한 편집기 유형을 선택하는 데 도움이 됩니다.

## <a name="types-of-editor"></a>편집기 유형

Visual Studio 코어 편집기에 대한 자세한 내용은 [편집기 및 언어 서비스 확장을](../extensibility/extending-the-editor-and-language-services.md)참조하십시오.

### <a name="custom-editors"></a>사용자 지정 편집기
 사용자 지정 편집기는 특수한 환경에서 작동하도록 설계된 편집기입니다. 예를 들어 Microsoft Exchange 서버와 같은 특정 리포지토리에 데이터를 읽고 쓰는 기능을 하는 편집기를 만들 수 있습니다. 프로젝트 유형에서만 작동하는 편집기를 원하거나 몇 가지 특정 명령만 있는 편집기를 원하는 경우 사용자 지정 편집기를 선택합니다. 그러나 사용자는 사용자 지정 편집기를 사용하여 표준 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로젝트를 편집할 수 없습니다.

 사용자 지정 편집기는 편집기 팩터리를 사용하고 편집기에 대한 정보를 레지스트리에 추가할 수 있습니다. 그러나 사용자 지정 편집기와 연결된 프로젝트 유형은 다른 방법으로 사용자 지정 편집기를 인스턴스화할 수 있습니다.

 사용자 지정 편집기는 내부 활성화 또는 단순화된 임베디드를 사용하여 뷰를 구현할 수 있습니다.

### <a name="external-editors"></a>외부 편집기
 외부 편집기는 마이크로소프트 워드, 메모장 또는 마이크로소프트 프론트 페이지와 같은 Visual Studio에 통합되지 않은 편집자입니다. 예를 들어 VSPackage에서 텍스트를 전달하는 경우 이러한 편집기를 호출할 수 있습니다. 외부 편집기는 자신을 등록하고 Visual Studio 외부에서 사용할 수 있습니다. 외부 편집기라고 부르고 호스트 창에 포함할 수 있으면 IDE의 창에 나타납니다. 그렇지 않은 경우 IDE는 별도의 창을 만듭니다.

 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 열거형사용을 사용하여 문서 우선 순위를 설정합니다. `DP_External` 값을 지정하면 외부 편집기에서 파일을 열 수 있습니다.

## <a name="editor-design-decisions"></a>편집기 디자인 결정
 다음 디자인 질문은 응용 프로그램에 가장 적합한 편집기 유형을 선택하는 데 도움이 됩니다.

- 응용 프로그램이 데이터를 파일에 저장합니까? 데이터를 파일에 저장하면 사용자 지정 또는 표준 형식입니까?

   표준 파일 형식을 사용하는 경우 프로젝트 외에 다른 프로젝트 형식이 데이터를 열고 읽고 쓸 수 있습니다. 그러나 사용자 지정 파일 형식을 사용하는 경우 프로젝트 형식만 데이터를 열고 읽고 쓸 수 있습니다.

   프로젝트에서 파일을 사용하는 경우 표준 편집기의 사용자 지정을 수행해야 합니다. 프로젝트에서 파일을 사용하지 않고 데이터베이스 또는 다른 리포지토리의 항목을 사용하는 경우 사용자 지정 편집기(custom editor)를 만들어야 합니다.

- 편집기에서 ActiveX 컨트롤을 호스팅해야 합니까?

   편집자가 ActiveX 컨트롤을 호스팅하는 경우 내부 활성화 에 설명된 대로 [내부 활성화](/visualstudio/misc/in-place-activation?view=vs-2015)편집기 구현합니다. ActiveX 컨트롤을 호스팅하지 않는 경우 단순화된 임베딩 편집기또는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 기본 편집기 사용자 지정을 사용합니다.

- 편집자가 여러 보기를 지원합니까? 편집기의 뷰를 기본 편집기와 동시에 표시하려면 여러 보기를 지원해야 합니다.

   편집기에서 여러 뷰를 지원해야 하는 경우 편집기의 문서 데이터 및 문서 보기 개체는 별도의 개체여야 합니다. 자세한 내용은 [여러 문서 보기 지원](../extensibility/supporting-multiple-document-views.md)을 참조하십시오.

   편집기에서 여러 뷰를 지원하는 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 문서 데이터 개체에 코어<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 편집기의 텍스트 버퍼 구현(개체)을 사용할 계획입니까? 즉, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 핵심 편집기와 나란히 편집기 보기를 지원하시겠습니까? 이 작업을 수행하는 기능은 양식 디자이너의 기본입니다.

- 외부 편집기를 호스팅해야 하는 경우 편집기를 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]내부에 포함할 수 있습니다.

   포함할 수 있는 경우 외부 편집기의 호스트 창을 만든 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 다음 메서드를 호출하고 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 열거 형 값을 `DP_External`로 설정해야 합니다. 편집기포함할 수 없는 경우 IDE는 편집에 대한 별도의 창을 자동으로 만듭니다.

## <a name="in-this-section"></a>섹션 내용

[연습: 사용자 지정 편집기 만들기](../extensibility/walkthrough-creating-a-custom-editor.md)\
사용자 지정 편집기를 만드는 방법을 설명합니다.

[연습: 사용자 지정 편집기에 피처 추가](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
사용자 지정 편집기에 기능을 추가하는 방법을 설명합니다.

[디자이너 초기화 및 메타데이터 구성](../extensibility/designer-initialization-and-metadata-configuration.md)\
디자이너를 초기화하는 방법을 설명합니다.

[디자이너에게 수행 취소 지원 제공](../extensibility/supplying-undo-support-to-designers.md)\
디자이너에 대한 취소 지원을 제공하는 방법을 설명합니다.

[사용자 지정 편집기의 구문 색칠](../extensibility/syntax-coloring-in-custom-editors.md)\
코어 편집기와 사용자 지정 편집기에서 구문 색지정의 차이점을 설명합니다.

[사용자 지정 편집기의 문서 데이터 및 문서 보기](../extensibility/document-data-and-document-view-in-custom-editors.md)\
사용자 지정 편집기에서 문서 데이터 및 문서 뷰를 구현하는 방법을 설명합니다.

## <a name="related-sections"></a>관련 단원

[편집기의 레거시 인터페이스](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
레거시 API를 통해 코어 편집기에 액세스하는 방법을 설명합니다.

[레거시 언어 서비스 개발](../extensibility/internals/developing-a-legacy-language-service.md)\
언어 서비스를 구현하는 방법을 설명합니다.

[비주얼 스튜디오의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)\
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]의 나머지 부분과 일치하는 UI 요소를 만드는 방법에 대해 설명합니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
