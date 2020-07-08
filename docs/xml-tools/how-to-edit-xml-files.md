---
title: '방법: XML 파일 편집'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ce3e41b2fe9dfdb080e23fb4270454bbd57f7ef
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817205"
---
# <a name="how-to-edit-xml-files"></a>방법: XML 파일 편집

XML 편집기는 XML 파일을 위한 새 편집기입니다. 이 편집기는 독립 실행형 XML 파일 또는 Visual Studio 프로젝트에 연결된 파일에 사용할 수 있습니다. XML 편집기는 *.config*, *.dtd*, *.xml*, *.xsd*, *.xdr*, *.xsl*, *.xslt* 및 *.vssettings* 파일 확장명과 연결됩니다. 또한 등록된 특정 편집기가 없고 XML 또는 DTD 콘텐츠가 포함된 파일 형식과도 연결되어 있습니다.

> [!NOTE]
> XHTML 문서는 HTML 편집기에서 처리됩니다.

XML 파일을 편집하려면 편집할 파일을 두 번 클릭합니다.

## <a name="add-a-new-xml-file-to-a-project"></a>프로젝트에 새 XML 파일 추가

1. **프로젝트** 메뉴에서 **새 항목 추가**를 선택합니다.

2. **템플릿** 창에서 **XML 파일**을 선택합니다.

3. **이름** 필드에 파일 이름을 입력하고 **추가**를 누릅니다.

   XML 파일이 프로젝트에 추가되고 XML 편집기에서 열립니다. 파일에는 기본 XML 선언, `<?xml version="1.0" encoding="utf-8" ?>`이 포함됩니다.

## <a name="add-an-existing-xml-file-to-a-project"></a>프로젝트에 기존 XML 파일 추가

1. **프로젝트** 메뉴에서 **기존 항목 추가**를 선택합니다.

   **기존 항목 추가** 대화 상자가 나타납니다.

2. XML 파일을 선택하고 **추가**를 누릅니다.

## <a name="create-a-new-xml-or-xslt-file"></a>새 XML 또는 XSLT 파일 만들기

1. **파일** 메뉴에서 **새로 만들기**를 선택합니다.

   **새 파일** 대화 상자가 표시됩니다.

2. 새 XML 파일을 만들려면 **XML 파일**을 선택하고 새 XSLT 스타일시트를 만들려면 **XSLT 파일**을 선택합니다.

3. **열기**를 클릭합니다.

## <a name="create-an-empty-project-for-xml-files"></a>XML 파일에 대한 빈 프로젝트 만들기

::: moniker range="vs-2017"

1. **파일 메뉴**에서 **새로 만들기** > **프로젝트**를 선택합니다.

   **새 프로젝트** 대화 상자가 나타납니다.

2. 원하는 코드 언어를 선택한 다음, **빈 프로젝트(.NET Framework)** 템플릿을 선택합니다.

3. **확인**을 클릭합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. **파일 메뉴**에서 **새로 만들기** > **프로젝트**를 선택합니다.

2. 템플릿 검색 상자에 **빈 프로젝트**를 입력하고 **빈 프로젝트(.NET Framework)** 템플릿을 선택한 후 **다음**을 클릭합니다.

3. **만들기**를 클릭합니다.

::: moniker-end

4. 프로젝트에 XML 파일을 추가합니다.

   XML 편집기에서는 이 프로젝트에 추가한 스키마를 찾아서 이 프로젝트를 연 상태에서 편집하는 모든 XML, 스키마 또는 XSLT 파일의 유효성 검사 및 IntelliSense에 사용합니다.

## <a name="see-also"></a>참조

- [XML 편집기](../xml-tools/xml-editor.md)
- [XML 문서 속성, 속성 창](../xml-tools/xml-document-properties-properties-window.md)
- [방법: XML 문서에서 XML 스키마 만들기](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
