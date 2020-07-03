---
title: '연습: 파일 이름 확장명에 콘텐츠 형식 연결 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b4e5ba3cd82090b5fad76d48c4600e0814bd91eb
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904683"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>연습: 파일 이름 확장명에 콘텐츠 형식 연결
사용자 고유의 콘텐츠 형식을 정의 하 고 MEF (편집기 Managed Extensibility Framework) 확장을 사용 하 여 파일 이름 확장명을 연결할 수 있습니다. 일부 경우에는 파일 이름 확장명이 언어 서비스에 의해 이미 정의 되어 있습니다. 그러나 MEF에서 사용 하려면 콘텐츠 형식에 연결 해야 합니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 되어 있습니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

1. C # VSIX 프로젝트를 만듭니다. ( **새 프로젝트** 대화 상자에서 **Visual c #/확장성**, **VSIX 프로젝트**를 차례로 선택 합니다.) 솔루션 이름을로 `ContentTypeTest` 합니다.

2. **Source.extension.vsixmanifest** 파일에서 **자산** 탭으로 이동 하 여 **Type** 필드를 **VisualStudio**로 설정 하 고, **원본** 필드를 **현재 솔루션의 프로젝트로**설정 하 고, **프로젝트** 필드를 프로젝트 이름으로 설정 합니다.

## <a name="define-the-content-type"></a>콘텐츠 형식 정의

1. 클래스 파일을 추가하고 이름을 `FileAndContentTypes`로 지정합니다.

2. 다음 어셈블리에 대한 참조를 추가합니다.

    1. System.ComponentModel.Composition

    2. VisualStudio.

    3. VisualStudio. CoreUtility

3. 다음 지시문을 추가 `using` 합니다.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. 정의를 포함 하는 정적 클래스를 선언 합니다.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. 이 클래스에서 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> "hid" 라는를 내보내고 해당 기본 정의를 "text"로 선언 합니다.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>파일 이름 확장명을 콘텐츠 형식에 연결 합니다.

- 이 콘텐츠 형식을 파일 이름 확장명에 매핑하려면 확장명이. n a 인을 내보내고 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 콘텐츠 형식이 *.hid* "hid"입니다.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
         [Export]
         [Name("hid")]
         [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;

         [Export]
         [FileExtension(".hid")]
         [ContentType("hid")]
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;
    }
    ```

## <a name="add-the-content-type-to-an-editor-export"></a>편집기 내보내기에 콘텐츠 형식 추가

1. 편집기 확장을 만듭니다. 예를 들어 [연습: 여백 문자 모양 만들기](../extensibility/walkthrough-creating-a-margin-glyph.md)에 설명 된 여백 문자 모양 확장을 사용할 수 있습니다.

2. 이 절차에서 정의한 클래스를 추가 합니다.

3. 확장 클래스를 내보낼 때 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "hid" 형식의를 추가 합니다.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>참조
- [언어 서비스 및 편집기 확장 위치](../extensibility/language-service-and-editor-extension-points.md)
