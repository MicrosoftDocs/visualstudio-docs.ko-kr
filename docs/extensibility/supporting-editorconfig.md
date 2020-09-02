---
title: EditorConfig를 지원 하도록 언어 서비스를 확장 합니다.
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfe0e30904d000b4fd70c85371d29a2ee486932
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699578"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>언어 서비스에 대 한 EditorConfig 지원

[Editorconfig](https://editorconfig.org/) 파일을 사용 하면 프로젝트별로 들여쓰기 크기와 같은 일반적인 텍스트 편집기 옵션을 설명할 수 있습니다. Visual Studio의 EditorConfig 파일 지원에 대 한 자세한 내용은 [EditorConfig를 사용 하 여 이식 가능한 편집기 설정 만들기](../ide/create-portable-custom-editor-options.md)를 참조 하세요.

대부분의 경우 Visual Studio 언어 서비스를 구현할 때 EditorConfig 유니버설 속성을 지원하기 위해 추가 작업이 필요하지 않습니다. 사용자가 파일을 열면 코어 편집기에서 .editorconfig 파일을 자동으로 검색하여 읽은 다음 적절한 텍스트 버퍼와 보기 옵션을 설정합니다. 그러나 탭 및 공백과 같은 편집의 경우 일부 언어 서비스는 전역 설정을 사용 하는 대신 적절 한 상황에 맞는 텍스트 보기 옵션을 사용 하도록 선택 합니다. 이러한 경우 EditorConfig 파일을 지원하도록 언어 서비스를 업데이트해야 합니다.

다음은 Web.config 파일을 지원 하기 위해 언어 서비스를 업데이트 하는 데 필요한 변경 사항으로, 전역 _언어별_ 옵션을 _상황별_ 옵션으로 대체 합니다.

## <a name="indent-style"></a>들여쓰기 스타일

언어별 옵션 | 상황별 옵션
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>들여쓰기 크기

언어별 옵션 | 상황별 옵션
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>탭 크기

언어별 옵션 | 상황별 옵션
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>추가 정보

- [EditorConfig를 사용 하 여 이식 가능한 편집기 설정 만들기](../ide/create-portable-custom-editor-options.md)
- [편집기 및 언어 서비스 확장](../extensibility/extending-the-editor-and-language-services.md)
