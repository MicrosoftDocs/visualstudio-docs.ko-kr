---
title: 에디터 및 언어 서비스 확장 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 239c638ec32cc0dc2b2e275a5dbe0c4213a3423e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711708"
---
# <a name="extend-the-editor-and-language-services"></a>편집기 및 언어 서비스 확장
자체 편집기에 언어 서비스 기능(예: IntelliSense)을 추가하고 Visual Studio 코드 편집기의 대부분의 기능을 확장할 수 있습니다.  확장할 수 있는 내용의 전체 목록은 [언어 서비스 및 편집기 확장 지점을](../extensibility/language-service-and-editor-extension-points.md)참조하십시오.

 관리되는 확장성 프레임워크(MEF)를 사용하여 대부분의 편집기 기능을 확장합니다. 예를 들어 확장하려는 편집기 기능이 구문 색지정인 경우 다른 색지정을 원하는 분류와 처리 방법을 정의하는 MEF *구성 요소 부분을* 작성할 수 있습니다. 편집기는 동일한 기능의 여러 확장을 지원합니다.

 편집기 프레젠테이션 계층은 WPF(Windows 프레젠테이션 프레임워크)를 기반으로 합니다. WPF는 유연한 텍스트 서식을 위한 그래픽 라이브러리를 제공하며 그래픽 및 애니메이션과 같은 시각화도 제공합니다.

 Visual Studio SDK는 이전 버전용으로 작성된 VSPackage를 지원하기 위해 *shims로* 알려진 어댑터를 제공합니다. 그럼에도 불구하고 기존 VSPackage가 있는 경우 더 나은 성능과 안정성을 얻으려면 새 기술로 업데이트하는 것이 좋습니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[언어 서비스 및 편집기 확장 시작](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|편집기확장을 만드는 방법을 설명합니다.|
|[편집기 내부](../extensibility/inside-the-editor.md)|편집기의 일반적인 구조를 설명하고 일부 기능을 나열합니다.|
|[편집기에서 관리되는 확장성 프레임워크](../extensibility/managed-extensibility-framework-in-the-editor.md)|편집기와 함께 관리되는 확장성 프레임워크(MEF)를 사용하는 방법을 설명합니다.|
|[언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)|편집기의 확장 점을 나열합니다. 확장 점은 확장할 수 있는 편집기 피쳐를 나타냅니다.|
|[연습: 뷰 장식, 명령 및 설정 만들기(열 안내선)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|코드를 특정 표시 너비로 유지하는 데 도움이 되는 열 안내선을 그리는 뷰 장식을 작성합니다.  또한 명령 창에서 호출할 수 있는 명령을 선언하고 구현할 뿐만 아니라 읽기 및 쓰기 설정도 표시됩니다.|
|[편집기 가져오기](../extensibility/editor-imports.md)|확장프로그램을 가져올 수 있는 서비스를 나열합니다.|
|[레거시 코드를 편집기로 조정](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|레거시 코드(Visual Studio 2010 이전)를 조정하여 편집기를 확장하는 다양한 방법을 설명합니다.|
|[레거시 언어 서비스 마이그레이션](../extensibility/internals/migrating-a-legacy-language-service.md)|VSPackage 기반 언어 서비스를 마이그레이션하는 방법을 설명합니다.|
|[연습: 콘텐츠 유형을 파일 이름 확장명에 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|콘텐츠 형식을 파일 이름 확장명에 연결하는 방법을 보여 주면 됩니다.|
|[연습: 여백 문말 만들기](../extensibility/walkthrough-creating-a-margin-glyph.md)|여백에 아이콘을 추가하는 방법을 보여 주면 됩니다.|
|[연습: 텍스트 강조 표시](../extensibility/walkthrough-highlighting-text.md)|태그를 사용하여 텍스트를 강조 표시하는 방법을 보여 *주시면* 됩니다.|
|[연습: 개요 추가](../extensibility/walkthrough-outlining.md)|특정 종류의 중괄호에 대한 개요를 추가하는 방법을 보여 주시면 됩니다.|
|[연습: 일치하는 중괄호 표시](../extensibility/walkthrough-displaying-matching-braces.md)|일치하는 중괄호를 강조 표시하는 방법을 보여 주시면 됩니다.|
|[연습: 빠른 정보 표시 도구 설명](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|속성, 메서드 및 이벤트와 같은 코드 요소를 설명하는 QuickInfo 팝업을 표시하는 방법을 보여 주었습니다.|
|[연습: 서명 도움말 표시](../extensibility/walkthrough-displaying-signature-help.md)|서명에서 매개 변수의 수와 유형에 대한 정보를 제공하는 팝업을 표시하는 방법을 보여 줍니다.|
|[연습: 명령문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)|문 완성을 구현하는 방법을 보여 주며|
|[연습: 코드 조각 구현](../extensibility/walkthrough-implementing-code-snippets.md)|코드 조각 확장을 구현하는 방법을 보여 주며|
|[연습: 전구 제안 표시](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|코드 제안에 대한 전구를 표시하는 방법을 보여 옵니다.|
|[연습: 편집기 확장이 있는 셸 명령 사용](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|VSPackage에서 메뉴 명령을 MEF 구성 요소와 연결하는 방법을 보여 줍니다.|
|[연습: 편집기 확장이 있는 바로 가기 키 사용](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|VSPackage의 메뉴 바로 가기를 MEF 구성 요소와 연결하는 방법을 보여 줍니다.|
|[MEF(Managed Extensibility Framework)](/dotnet/framework/mef/index)|관리되는 확장성 프레임워크(MEF)에 대한 정보를 제공합니다.|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|WPF(Windows 프레젠테이션 기반)에 대한 정보를 제공합니다.|

## <a name="reference"></a>참조
 Visual Studio 편집기에는 다음 네임스페이스가 포함됩니다.

 <xref:Microsoft.VisualStudio.Language.Intellisense>

 <xref:Microsoft.VisualStudio.Language.StandardClassification>

 <xref:Microsoft.VisualStudio.Editor>

 <xref:Microsoft.VisualStudio.Text>

 <xref:Microsoft.VisualStudio.Text.Adornments>

 <xref:Microsoft.VisualStudio.Text.Classification>

 <xref:Microsoft.VisualStudio.Text.Differencing>

 <xref:Microsoft.VisualStudio.Text.Document>

 <xref:Microsoft.VisualStudio.Text.Editor>

 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>

 <xref:Microsoft.VisualStudio.Text.Formatting>

 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>

 <xref:Microsoft.VisualStudio.Text.Operations>

 <xref:Microsoft.VisualStudio.Text.Outlining>

 <xref:Microsoft.VisualStudio.Text.Projection>

 <xref:Microsoft.VisualStudio.Text.Tagging>

 <xref:Microsoft.VisualStudio.Utilities>
