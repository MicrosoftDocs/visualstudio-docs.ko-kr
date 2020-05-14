---
title: '연습: 콘텐츠 유형을 파일 이름 확장명에 연결 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 328be013b5d522938cd7450fc53d4866c632abb3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697078"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>연습: 콘텐츠 유형을 파일 이름 확장명에 연결
사용자 고유의 콘텐츠 유형을 정의하고 MEF(관리되는 확장성 프레임워크) 확장명을 사용하여 파일 이름 확장명을 링크할 수 있습니다. 경우에 따라 파일 이름 확장명은 이미 언어 서비스에 의해 정의됩니다. 그러나 MEF와 함께 사용하려면 콘텐츠 형식에 계속 연결해야 합니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. Visual Studio 설정에서 선택적 기능으로 포함되어 있습니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-mef-project"></a>MEF 프로젝트 만들기

1. C# VSIX 프로젝트를 만듭니다. 새 **프로젝트** 대화 상자에서 **시각적 C# / 확장성**, **VSIX 프로젝트를**선택합니다. 솔루션 `ContentTypeTest`이름을 지정합니다.

2. **source.extension.vsixmanifest** 파일에서 **자산** 탭으로 이동하여 **유형** 필드를 **Microsoft.VisualStudio.MefComponent,** **현재 솔루션의 프로젝트로** **의 소스** 필드, **프로젝트** 필드로 프로젝트 이름으로 설정합니다.

## <a name="define-the-content-type"></a>콘텐츠 유형 정의

1. 클래스 파일을 추가하고 이름을 `FileAndContentTypes`로 지정합니다.

2. 다음 어셈블리에 대한 참조를 추가합니다.

    1. System.ComponentModel.Composition

    2. 마이크로소프트.비주얼 스튜디오.텍스트.로직

    3. 마이크로소프트.비주얼 스튜디오.코어유틸리티

3. 다음 `using` 지시문을 추가합니다.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. 정의가 포함된 정적 클래스를 선언합니다.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. 이 클래스에서 명명된 <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> "hid"를 내보내고 기본 정의를 "텍스트"로 선언합니다.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>파일 이름 확장명을 콘텐츠 유형에 연결합니다.

- 이 콘텐츠 유형을 파일 이름 확장명에 <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> 매핑하려면 *확장명 .hid와* 콘텐츠 유형 "hid"가 있는 a를 내보냅니다.

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

1. 편집기 확장을 만듭니다. 예를 들어 연습에서 설명한 여백 문말 확장을 사용할 수 [있습니다.](../extensibility/walkthrough-creating-a-margin-glyph.md)

2. 이 절차에서 정의한 클래스를 추가합니다.

3. 확장 클래스를 내보낼 때 <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "hid" 형식을 추가합니다.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>참조
- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
