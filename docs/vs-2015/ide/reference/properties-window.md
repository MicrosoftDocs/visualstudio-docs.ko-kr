---
title: 속성 창 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 959bd36995ca4086bf64020816b00aee6f777fbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662082"
---
# <a name="properties-window"></a>속성 창
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 창을 사용하여 편집기 및 디자이너에 있는 디자인 타임 속성 및 선택된 개체의 이벤트를 변경할 수 있습니다. **속성** 창을 사용하여 파일, 프로젝트 및 솔루션 속성을 편집하고 볼 수도 있습니다. **보기** 메뉴에서 **속성 창**을 찾을 수 있습니다. F4 키를 누르거나 **빠른 실행** 창에서 **속성**을 입력하여 열 수도 있습니다.

 **속성** 창에는 특정 속성의 필요 여부에 따라 다른 유형의 편집 필드가 표시됩니다. 이러한 편집 필드에는 편집 상자, 드롭다운 목록 및 사용자 지정 편집기 대화 상자에 대한 링크가 포함됩니다. 회색으로 표시된 속성은 읽기 전용입니다.

## <a name="uielement-list"></a>UIElement 목록
 개체 이름 현재 선택 된 개체를 나열 합니다. 활성 편집기 또는 디자이너의 개체만 표시됩니다. 여러 개체를 선택하면 선택한 모든 개체에 공통 속성만이 표시됩니다.

 항목별 선택한 개체의 모든 속성 및 속성 값을 범주별로 나열 합니다. 범주를 축소하여 표시되는 속성의 수를 줄일 수 있습니다. 범주를 확장하거나 축소할 경우 범주 이름 왼쪽에 있는 더하기(+) 또는 빼기(-) 기호를 각각 사용합니다. 범주는 사전순으로 나열됩니다.

 사전순 사전순 사전순으로 선택한 개체의 모든 디자인 타임 속성 및 이벤트를 정렬 합니다. 뚜렷한 속성을 편집하려면 마우스 오른쪽 버튼으로 셀을 클릭하고 변경 내용을 입력합니다.

 속성 페이지 선택한 항목에 대 한 **속성 페이지** 대화 상자 또는 **프로젝트 디자이너** 를 표시 합니다. 속성 페이지는 **속성** 창에서 사용 가능한 속성과 동일하거나 상위 집합인 하위 집합을 표시합니다. 이 단추를 사용하여 프로젝트의 활성 구성에 관련된 속성을 보고 편집합니다.

 속성 개체의 속성을 표시 합니다. 대부분의 개체에는 **속성** 창을 사용하여 볼 수 있는 이벤트가 있습니다.

 상속, 적용 된 스타일 및 바인딩과 같은 소스로 속성 소스 그룹 속성을 기준으로 정렬 합니다. 디자이너에서 XAML 파일을 편집하는 경우에만 사용할 수 있습니다.

 이벤트 개체에 대 한 이벤트를 표시 합니다.

> [!NOTE]
> 이 **속성** 창 도구 모음 컨트롤은 폼 또는 컨트롤 디자이너가 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 프로젝트의 컨텍스트에서 활성 상태인 경우에만 사용 가능합니다. XAML 파일을 편집할 때 이벤트는 속성 창의 별도 탭에 표시됩니다.

 메시지 모든 Windows 메시지를 표시 합니다. 선택한 클래스에 제공되는 메시지에 지정된 처리기 함수를 추가하거나 삭제할 수 있습니다.

> [!NOTE]
> 이 **속성** 창 도구 모음 컨트롤은 **클래스 뷰**가 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 프로젝트의 컨텍스트에서 활성 창인 경우에만 사용 가능합니다.

 재정의는 선택한 클래스에 대 한 모든 가상 함수를 나열 하 고 재정의 함수를 추가 하거나 삭제할 수 있습니다.

> [!NOTE]
> 이 **속성** 창 도구 모음 컨트롤은 **클래스 뷰**가 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 프로젝트의 컨텍스트에서 활성 창인 경우에만 사용 가능합니다.

 설명 창 속성 유형과 속성에 대 한 간단한 설명을 표시 합니다. 바로 가기 메뉴에서 설명 명령을 사용하여 속성에 대한 설명을 켜고 끌 수 있습니다.

> [!NOTE]
> 이 **속성** 창 도구 모음 컨트롤은 디자이너에서 XAML 파일을 편집할 경우에 사용할 수 없습니다.

 미리 보기 뷰 디자이너에서 XAML 파일을 편집할 때 현재 선택 된 요소를 시각적으로 표시 합니다.

 검색은 디자이너에서 XAML 파일을 편집할 때 속성 및 이벤트에 대 한 검색 기능을 제공 합니다. 검색 상자는 부분 단어 검색에 응답하고 입력한 대로 검색 결과를 업데이트합니다.

## <a name="see-also"></a>관련 항목
 [프로젝트 속성 참조](../../ide/reference/project-properties-reference.md) [창 레이아웃 사용자 지정](../../ide/customizing-window-layouts-in-visual-studio.md)
