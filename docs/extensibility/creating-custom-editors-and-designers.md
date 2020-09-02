---
title: 사용자 지정 편집기 및 디자이너 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0ddfe2b61c8ef08d77fbb7c841b3bb69c167af2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903732"
---
# <a name="create-custom-editors-and-designers"></a>사용자 지정 편집기 및 디자이너 만들기

Visual Studio IDE (통합 개발 환경)는 다음과 같은 다양 한 유형의 편집기를 호스트할 수 있습니다.

- Visual Studio 핵심 편집기

- 사용자 지정 편집기

- 외부 편집기

- 디자이너

다음 정보는 필요한 편집기 유형을 선택 하는 데 도움이 됩니다.

## <a name="types-of-editor"></a>편집기 유형

Visual Studio 핵심 편집기에 대 한 자세한 내용은 [편집기 및 언어 서비스 확장](../extensibility/extending-the-editor-and-language-services.md)을 참조 하세요.

### <a name="custom-editors"></a>사용자 지정 편집기
 사용자 지정 편집기는 특수 한 상황에서 작동 하도록 설계 된 편집기입니다. 예를 들어 Microsoft Exchange server와 같은 특정 리포지토리의 데이터를 읽고 쓰기 위한 함수를 갖는 편집기를 만들 수 있습니다. 프로젝트 형식 에서만 작동 하는 편집기를 사용 하거나 몇 가지 특정 명령만 있는 편집기를 사용 하려는 경우 사용자 지정 편집기를 선택 합니다. 그러나 사용자는 사용자 지정 편집기를 사용 하 여 표준 프로젝트를 편집할 수 없습니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 사용자 지정 편집기는 편집기 팩터리를 사용 하 고 편집기에 대 한 정보를 레지스트리에 추가할 수 있습니다. 그러나 사용자 지정 편집기와 연결 된 프로젝트 형식은 사용자 지정 편집기를 다른 방식으로 인스턴스화할 수 있습니다.

 사용자 지정 편집기는 내부 활성화 또는 단순화 된 포함을 사용 하 여 뷰를 구현할 수 있습니다.

### <a name="external-editors"></a>외부 편집기
 외부 편집기는 Microsoft Word, 메모장 또는 Microsoft FrontPage와 같이 Visual Studio에 통합 되지 않은 편집기입니다. 예를 들어 VSPackage에서 텍스트를 전달 하는 경우 이러한 편집기를 호출할 수 있습니다. 외부 편집기는 자신을 등록 하며 Visual Studio 외부에서 사용할 수 있습니다. 외부 편집기를 호출 하 고 호스트 창에 포함할 수 있는 경우 IDE의 창에 표시 됩니다. 그렇지 않으면 IDE에서 별도의 창을 만듭니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>메서드는 열거형을 사용 하 여 문서 우선 순위를 설정 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> . `DP_External`값이 지정 된 경우 외부 편집기에서 파일을 열 수 있습니다.

## <a name="editor-design-decisions"></a>편집기 디자인 결정
 다음 디자인 질문은 응용 프로그램에 가장 적합 한 편집기 유형을 선택 하는 데 도움이 됩니다.

- 응용 프로그램이 데이터를 파일에 저장 합니까? 데이터를 파일에 저장 하는 경우 사용자 지정 또는 표준 형식이 되나요?

   표준 파일 형식을 사용 하는 경우 프로젝트와 다른 프로젝트 형식에서 데이터를 열고 읽고 쓸 수 있습니다. 그러나 사용자 지정 파일 형식을 사용 하는 경우 프로젝트 형식만 데이터를 열고 읽고 쓸 수 있습니다.

   프로젝트에서 파일을 사용 하는 경우 표준 편집기를 사용자 지정 해야 합니다. 프로젝트에서 파일을 사용 하지 않고 데이터베이스 또는 다른 리포지토리의 항목을 사용 하는 경우 사용자 지정 편집기를 만들어야 합니다.

- 편집기에서 ActiveX 컨트롤을 호스트 해야 하나요?

   편집기에서 ActiveX 컨트롤을 호스트 하는 경우 [내부 활성화](/visualstudio/misc/in-place-activation?view=vs-2015)에 설명 된 대로 내부 활성화 편집기를 구현 합니다. ActiveX 컨트롤을 호스팅하지 않는 경우 간단한 포함 편집기를 사용 하거나 기본 편집기를 사용자 지정 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 합니다.

- 편집기에서 여러 뷰를 지원 하나요? 편집기의 뷰가 기본 편집기와 동시에 표시 되도록 하려면 여러 뷰를 지원 해야 합니다.

   편집기에서 여러 뷰를 지원 해야 하는 경우 편집기에 대 한 문서 데이터 및 문서 뷰 개체는 별도의 개체 여야 합니다. 자세한 내용은 [다중 문서 뷰 지원](../extensibility/supporting-multiple-document-views.md)을 참조 하세요.

   편집기에서 여러 뷰를 지 원하는 경우 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 문서 데이터 개체에 대해 핵심 편집기의 텍스트 버퍼 구현 (개체)을 사용할 계획 입니까? 즉, 편집기 뷰를 핵심 편집기와 나란히 지원 하 시겠습니까 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ? 이 작업을 수행 하는 기능은 폼 디자이너의 기반이 됩니다.

- 외부 편집기를 호스트 해야 하는 경우 편집기를 내부에 포함할 수 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 있습니까?

   포함할 수 있는 경우 외부 편집기에 대 한 호스트 창을 만든 다음 메서드를 호출 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 고 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 열거형 값을로 설정 해야 합니다 `DP_External` . 편집기를 포함할 수 없는 경우 IDE에서 자동으로 별도의 창을 만듭니다.

## <a name="in-this-section"></a>섹션 내용

[연습: 사용자 지정 편집기 만들기](../extensibility/walkthrough-creating-a-custom-editor.md)\
사용자 지정 편집기를 만드는 방법을 설명 합니다.

[연습: 사용자 지정 편집기에 기능 추가](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
사용자 지정 편집기에 기능을 추가 하는 방법에 대해 설명 합니다.

[디자이너 초기화 및 메타 데이터 구성](../extensibility/designer-initialization-and-metadata-configuration.md)\
디자이너를 초기화 하는 방법을 설명 합니다.

[디자이너에 실행 취소 지원 제공](../extensibility/supplying-undo-support-to-designers.md)\
디자이너에 대 한 실행 취소 지원을 제공 하는 방법을 설명 합니다.

[사용자 지정 편집기의 구문 색 지정](../extensibility/syntax-coloring-in-custom-editors.md)\
핵심 편집기와 사용자 지정 편집기에서 구문 색 지정의 차이점을 설명 합니다.

[사용자 지정 편집기의 문서 데이터 및 문서 보기](../extensibility/document-data-and-document-view-in-custom-editors.md)\
사용자 지정 편집기에서 문서 데이터와 문서 뷰를 구현 하는 방법을 설명 합니다.

## <a name="related-sections"></a>관련 단원

[편집기의 레거시 인터페이스](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
레거시 API를 통해 핵심 편집기에 액세스 하는 방법을 설명 합니다.

[레거시 언어 서비스 개발](../extensibility/internals/developing-a-legacy-language-service.md)\
언어 서비스를 구현 하는 방법을 설명 합니다.

[Visual Studio의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)\
의 나머지와 일치 하는 UI 요소를 만드는 방법을 설명 합니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
