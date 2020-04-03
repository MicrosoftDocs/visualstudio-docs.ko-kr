---
title: 색 테마 및 글꼴 설정
ms.date: 03/23/2020
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c0b7b4e439f33e4e2eed8609d7e85e098068aea
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233146"
---
# <a name="personalize-the-visual-studio-ide-and-editor"></a>Visual Studio IDE 및 편집기 개인 설정

5~10분이 걸리는 이 자습서에서는 어두운 테마를 선택하여 Visual Studio 색 테마를 사용자 지정하겠습니다. 또한 텍스트 편집기에서 두 가지 형식의 텍스트에 대한 색을 사용자 지정합니다.

::: moniker range="vs-2017"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

::: moniker range=">=vs-2019"

아직 Visual Studio를 설치하지 않은 경우 [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads) 페이지로 이동하여 체험용으로 설치합니다.

::: moniker-end

## <a name="set-the-color-theme"></a>색 테마 설정

Visual Studio의 기본 색 테마는 **파랑**이라고 합니다. **어두운**으로 변경해 보겠습니다.

1. **파일** 및 **편집**과 같은 메뉴의 행인 메뉴 모음에서 **도구** > **옵션**을 선택합니다.

1. **환경** > **일반** 옵션 페이지에서 **색 테마** 선택을 **어둡게**로 변경하고 **확인**을 선택합니다.

   전체 Visual Studio 개발 환경(IDE)에 대한 색 테마가 **어둡게**로 변경됩니다.

   ::: moniker range="vs-2017"

   ![어두운 테마의 Visual Studio 2017](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![어두운 테마의 Visual Studio 2019](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)에서 **Visual Studio 색 테마 편집기**를 설치하여 미리 정의된 추가 테마를 설치할 수 있습니다. 이 도구를 설치하면 **색 테마** 드롭다운 목록에 추가 색 테마가 나타납니다.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)에서 제공되는 **Visual Studio Color Theme Designer**를 설치하여 사용자 자체 테마를 만들 수도 있습니다.

::: moniker-end

## <a name="change-text-color"></a>텍스트 색 변경

이제 편집기의 일부 텍스트 색을 사용자 지정해 보겠습니다. 먼저 XML 파일을 만들어 기본 색을 확인하겠습니다.

1. 메뉴 모음에서 **파일** > **새로 만들기** > **파일**을 차례로 선택합니다.

1. **새 파일** 대화 상자의 **일반** 범주 아래에서 **XML 파일**을 선택한 다음 **열기**를 선택합니다.

1. `<?xml version="1.0" encoding="utf-8"?>`를 포함하는 줄 아래에 다음 XML을 붙여넣습니다.

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   줄 번호는 옥색이며, XML 특성(예: `id="bk101"`)은 연한 파랑색입니다. 이러한 항목의 텍스트 색을 변경해 보겠습니다.

   ![XML 파일 글꼴 색](media/quickstart-personalize-xml-file.png)

1. **옵션** 대화 상자를 열려면 메뉴 모음에서 **도구** > **옵션**을 선택합니다.

1. **환경** 아래에서 **글꼴 및 색** 범주를 선택합니다.

   **설정 표시** 아래의 텍스트에 **텍스트 편집기**&mdash;라고 표시됩니다. 이것이 우리가 원하는 설정입니다. 드롭다운 목록을 확장하여 글꼴 및 텍스트 색을 사용자 지정할 수 있는 위치의 광범위한 목록을 표시할 수 있습니다.

1. 줄 번호 텍스트의 색을 변경하려면 **표시 항목** 목록에서 **줄 번호**를 선택합니다. **항목 전경** 상자에서 **올리브**를 선택합니다.

   ![옵션 대화 상자, 글꼴 및 색 범주](media/quickstart-personalize-line-number-color.png)

   일부 언어에는 고유한 특정 글꼴 및 색 설정이 있습니다. 예를 들어 C++ 개발자가 함수에 사용되는 색을 변경하려는 경우 **항목 표시** 목록에서 **C++ 함수**를 찾을 수 있습니다.

1. 대화 상자를 종료하기 전에 XML 특성의 색도 변경해 보겠습니다. **표시 항목** 목록에서 **XML 특성**이 표시될 때까지 아래로 스크롤하여 선택합니다. **항목 전경** 상자에서 **라임**을 선택합니다. **확인**을 선택하여 선택 항목을 저장하고 대화 상자를 닫습니다.

   이제 줄 번호는 올리브색이며, XML 특성은 밝은 라임 녹색입니다. C++ 또는 C# 코드 파일과 같은 다른 파일 형식을 열면 해당 줄 번호도 올리브색으로 표시됩니다.

   ![새 글꼴 색이 적용된 XML 파일](media/quickstart-personalize-xml-file-new-colors.png)

Visual Studio에서 색을 사용자 지정하는 몇 가지 방법을 살펴보았습니다. **옵션** 대화 상자에서 다른 사용자 지정 옵션도 탐색하여 자신에게 맞게 Visual Studio를 설정하시기 바랍니다.

## <a name="see-also"></a>참고 항목

- [편집기 사용자 지정](../ide/how-to-change-text-case-in-the-editor.md)
- [Visual Studio IDE 개요](../get-started/visual-studio-ide.md)
