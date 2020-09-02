---
title: 옵션 페이지, 텍스트 편집기 노드 속성 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Text Editor node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 19438302-0677-4f4d-9720-5667e6a22ab2
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 62dddacaea1846c8e5d5da404ad7a16fde90f209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662408"
---
# <a name="options-page-text-editor-node-properties"></a>옵션 페이지, 텍스트 편집기 노드 속성
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 문서에서는 **옵션** 대화 상자의 **텍스트 편집기** 범주, `DTE.Properties("TextEditor", <Property Page>)`와 연관된 일부 페이지(또는 속성 컬렉션)에 대해 설명합니다. 각 하위 단원의 제목은 `Properties` 컬렉션에 액세스하는 데 사용되는 호출이며, 각 하위 단원의 표에는 컬렉션의 속성이 나열되어 있습니다.

 [옵션 설정 제어](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)의 Visual Basic 매크로는 **옵션** 대화 상자의 각 페이지에 대해 현재 옵션과 해당 값을 표시하는 방법을 보여 줍니다.

## <a name="general"></a>일반
 `DTE.Properties("TextEditor", "General")`

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|GoToAnchorAfterEscape|Get/Set (Boolean)|`True`인 경우 선택 항목이 있는 상태에서 Esc 키를 누르면 선택 항목을 만든 작업이 시작된 위치로 삽입 지점이 이동합니다. `False`인 경우 선택 항목의 반대쪽 끝으로 삽입 지점이 이동합니다.|
|DragNDropTextEditing|Get/Set (Boolean)|선택된 텍스트 영역을 문서의 다른 위치로 끌어서 놓아 복사 또는 잘라내기/붙여넣기 작업을 수행할 수 있는지 여부를 지정합니다.|
|HorizontalScrollBar|Get/Set (Boolean)|편집기 창에 가로 스크롤 막대가 있는지 여부를 지정합니다.|
|VerticalScrollBar|Get/Set (Boolean)|편집기 창에 세로 스크롤 막대가 있는지 여부를 지정합니다.|
|SelectionMargin|Get/Set (Boolean)|중단점 아이콘 등을 그리는 특수한 선택 동작을 위해 텍스트 창 왼쪽에 공백이 삽입되는지 여부를 지정합니다.|
|MarginIndicatorBar|Get/Set (Boolean)|텍스트 창의 왼쪽 여백과 본문을 구분하는 세로줄이 있는지 여부를 지정합니다.|
|UndoCaretActions|Get/Set (Boolean)|`True`. 실행 취소 작업에 버퍼를 수정하는 편집 작업뿐 아니라 삽입 지점 동작, 선택 명령 등이 포함됩니다.|
|AutoDelimiterHighlighting|Get/Set (Boolean)|닫기 구분 기호를 입력할 때 편집기가 열기 구분 기호를 강조 표시하는지 여부를 지정합니다. 이 속성 값에 상관없이 편집기는 항상 열기 구분 기호를 굵게 표시합니다.|
|EditorEmulation|Get/Set(Enum)||
|DetectUTF8WithoutSignature|Get/Set (Boolean)|인코딩 시그니처가 없을 때 파일에 UTF-8 인코딩이 사용되는지 여부를 검색합니다.|
|TrackChanges|Get/Set (Boolean)||

## <a name="plain-text"></a>일반 텍스트
 `DTE.Properties("TextEditor", "PlainText")`

 `PlainText` 편집기 옵션은 텍스트 파일을 편집할 때 편집기 설정에 영향을 줍니다. 각 프로그래밍 언어와 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 패키지에는 고유한 자체 **텍스트 편집기** 설정이 있습니다. 예를 들어, [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 편집기 설정을 보거나 변경하려면 `DTE.Properties("TextEditor", "CSharp") or DTE.Properties("TextEditor", "CSharp-Specific")`를 사용합니다. **SQL 스크립트** 편집기 설정의 경우 `DTE.Properties("TextEditor", "SQL ")`를 사용합니다.

|속성 항목 이름|값|설명|
|------------------------|-----------|-----------------|
|AutoListMembers|Get/Set (Boolean)|사용자가 변수 참조 다음에 마침표를 입력하는 경우 사용할 수 있는 멤버 목록이 자동으로 나타나는지 여부를 지정합니다.|
|AutoListParams|Get/Set (Boolean)|사용자가 함수 이름 다음에 "("를 입력하는 경우 인수 목록에 대한 설명이 자동으로 나타나는지 여부를 지정합니다.|
|HideAdvancedMembers|Get/Set (Boolean)|문 완성에서 모든 멤버를 나열하는지 자주 사용되는 멤버만을 나열하는지 여부를 지정합니다.|
|VirtualSpace|Get/Set (Boolean)|공백 문자가 그래픽으로 표시되는지 여부를 지정합니다. 이 값을 `true`로 설정하면 이 목록의 `WordWrap` 속성 항목이 `false`로 설정됩니다.|
|WordWrap|Get/Set (Boolean)|긴 줄이 단어 경계에서 자동으로 줄 바꿈 하는지 여부를 지정합니다. 이 값을 `true`로 설정하면 이 목록의 `VirtualSpace` 속성 항목이 `false`로 설정됩니다.|
|WordWrapGlyphs|Get/Set (Boolean)|줄 끝의 문자 모양을 표시합니다. 이 값은 줄이 다음 줄로 줄바꿈됨을 나타냅니다.|
|EnableLeftClickForURLs|Get/Set (Boolean)|편집기에서 URL에 밑줄을 사용할지 여부와 마우스 왼쪽 단추를 한 번 클릭하여 시스템 등록 웹 브라우저에 있는 URL로 이동하는 동작을 사용할지 여부를 지정합니다.|
|IndentStyle|Get/Set (<xref:EnvDTE.vsIndentStyle>)|다음 들여쓰기 스타일을 지정합니다. 기본, 스마트 또는 없음|
|TabSize|Get/Set (Long)|탭과 같은 공백 수를 나타냅니다. 1 ~ 60 (포함) 범위를 벗어나는 정수를 설정 하지 못했습니다.|
|InsertTabs|Get/Set (Boolean)|`True`인 경우 들여쓰기에 탭 문자를 사용합니다.|
|IndentSize|Get/Set (Long)|들여쓰기 수준 하나에 해당하는 공백 수를 나타냅니다. 범위는 1에서 60까지의 정수이고, 이를 벗어난 값을 설정하면 동작이 실패합니다.|
|ShowLineNumbers|Get/Set (Boolean)|코어 편집기 문서의 뷰에서 왼쪽 여백을 따라 줄 번호가 표시되는지 여부를 지정합니다.|
|ShowNavigationBar|Get/Set (Boolean)|드롭다운 목록과 단추가 편집기 창의 상단에 나타나는지 여부를 지정합니다.|
|CutCopyBlankLines|Get/Set (Boolean)|선택하면 빈 줄을 잘라 내거나 복사합니다.|

## <a name="see-also"></a>관련 항목
 옵션 [설정 제어](https://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d) 옵션 페이지 옵션 페이지에서 [속성 항목의 이름 결정](https://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa) [, 환경 노드 속성](../../ide/reference/options-page-environment-node-properties.md) [옵션 페이지, 글꼴 및 색 노드 속성](../../ide/reference/options-page-fonts-and-colors-node-properties.md)
