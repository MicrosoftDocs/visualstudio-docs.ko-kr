---
title: 편집기 및 언어 서비스 확장 | Microsoft Docs
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
ms.openlocfilehash: 155c703ebbeb2705ac7abbba5cd2c095f520c698
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584557"
---
# <a name="extend-the-editor-and-language-services"></a>편집기 및 언어 서비스 확장
언어 서비스 기능 (예: IntelliSense)을 사용자의 편집기에 추가 하 고 Visual Studio 코드 편집기의 기능을 대부분 확장할 수 있습니다.  확장할 수 있는 항목의 전체 목록은 [언어 서비스 및 편집기 확장 요소](../extensibility/language-service-and-editor-extension-points.md)를 참조 하세요.

 MEF (Managed Extensibility Framework)를 사용 하 여 대부분의 편집기 기능을 확장 합니다. 예를 들어 확장 하려는 편집기 기능이 구문 색 지정 인 경우에는 다른 색 지정을 원하는 분류 및 처리 방법을 정의 하는 MEF *구성 요소 부분* 을 작성할 수 있습니다. 편집기는 동일한 기능의 여러 확장도 지원 합니다.

 편집기 프레젠테이션 계층은 WPF (Windows Presentation Framework)를 기반으로 합니다. WPF는 유연한 텍스트 서식 지정을 위한 그래픽 라이브러리를 제공 하며 그래픽 및 애니메이션과 같은 시각화도 제공 합니다.

 Visual Studio SDK는 이전 버전용으로 작성 된 Vspackage를 지원 하기 위해 *shim* 이라는 어댑터를 제공 합니다. 그럼에도 불구 하 고 기존 VSPackage 있는 경우 더 나은 성능과 안정성을 얻기 위해 새 기술로 업데이트 하는 것이 좋습니다.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[언어 서비스 및 편집기 확장 시작](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|편집기에 확장을 만드는 방법에 대해 설명 합니다.|
|[편집기 내부](../extensibility/inside-the-editor.md)|편집기의 일반 구조를 설명 하 고 해당 기능 중 일부를 나열 합니다.|
|[편집기에서 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|편집기에서 MEF (Managed Extensibility Framework)를 사용 하는 방법을 설명 합니다.|
|[언어 서비스 및 편집기 확장 위치](../extensibility/language-service-and-editor-extension-points.md)|편집기의 확장 요소를 나열 합니다. 확장 지점은 확장할 수 있는 편집기 기능을 나타냅니다.|
|[연습: 뷰 장식, 명령 및 설정 만들기 (열 안내선)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|특정 표시 너비로 코드를 유지 하는 데 도움이 되는 열 안내선을 그리는 뷰 장식을 빌드하는 방법을 설명 합니다.  또한 명령 창에서 호출할 수 있는 명령 선언 및 구현 뿐만 아니라 읽기 및 쓰기 설정을 보여 줍니다.|
|[편집기 가져오기](../extensibility/editor-imports.md)|확장에서 가져올 수 있는 서비스를 나열 합니다.|
|[편집기에 레거시 코드 조정](../vs-2015/extensibility/adapting-legacy-code-to-the-editor.md?view=vs-2015&preserve-view=true)|레거시 코드 (Visual Studio 2010 이전)를 조정 하 여 편집기를 확장 하는 다양 한 방법을 설명 합니다.|
|[레거시 언어 서비스 마이그레이션](../extensibility/internals/migrating-a-legacy-language-service.md)|VSPackage 기반 언어 서비스를 마이그레이션하는 방법에 대해 설명 합니다.|
|[연습: 파일 이름 확장명에 콘텐츠 형식 연결](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|콘텐츠 형식을 파일 이름 확장명에 연결 하는 방법을 보여 줍니다.|
|[연습: 여백 문자 모양 만들기](../extensibility/walkthrough-creating-a-margin-glyph.md)|여백에 아이콘을 추가 하는 방법을 보여 줍니다.|
|[연습: 텍스트 강조 표시](../extensibility/walkthrough-highlighting-text.md)|*태그* 를 사용 하 여 텍스트를 강조 표시 하는 방법을 보여 줍니다.|
|[연습: 개요 추가](../extensibility/walkthrough-outlining.md)|특정 종류의 중괄호에 대 한 개요를 추가 하는 방법을 보여 줍니다.|
|[연습: 일치 하는 중괄호 표시](../extensibility/walkthrough-displaying-matching-braces.md)|일치 하는 중괄호를 강조 표시 하는 방법을 보여 줍니다.|
|[연습: QuickInfo 도구 설명 표시](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|속성, 메서드 및 이벤트와 같은 코드 요소를 설명 하는 QuickInfo 돌출을 표시 하는 방법을 보여 줍니다.|
|[연습: 서명 도움말 표시](../extensibility/walkthrough-displaying-signature-help.md)|시그니처의 매개 변수 수와 형식에 대 한 정보를 제공 하는 팝업을 표시 하는 방법을 보여 줍니다.|
|[연습: 명령문 완성 표시](../extensibility/walkthrough-displaying-statement-completion.md)|문 완성을 구현 하는 방법을 보여 줍니다.|
|[연습: 코드 조각 구현](../extensibility/walkthrough-implementing-code-snippets.md)|코드 조각 확장을 구현 하는 방법을 보여 줍니다.|
|[연습: 전구 제안 표시](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|코드 제안의 밝은 전구을 표시 하는 방법을 보여 줍니다.|
|[연습: 편집기 확장에서 셸 명령 사용](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|VSPackage의 메뉴 명령을 MEF 구성 요소와 연결 하는 방법을 보여 줍니다.|
|[연습: 편집기 확장에서 바로 가기 키 사용](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|VSPackage의 메뉴 바로 가기를 MEF 구성 요소와 연결 하는 방법을 보여 줍니다.|
|[MEF(Managed Extensibility Framework)](/dotnet/framework/mef/index)|MEF (Managed Extensibility Framework)에 대 한 정보를 제공 합니다.|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|WPF (Windows Presentation Foundation)에 대 한 정보를 제공 합니다.|

## <a name="reference"></a>참조
 Visual Studio 편집기에는 다음 네임 스페이스가 포함 되어 있습니다.

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