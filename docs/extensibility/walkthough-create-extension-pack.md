---
title: 확장 팩 만들기
description: 확장 팩 항목 템플릿을 사용하여 확장 팩을 만드는 방법 알아보기
ms.custom: SEO-VS-2020
ms.date: 07/27/2018
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: leslierichardson95
ms.author: lerich
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 213e3e71503ebea8074594bbc88a06980e3e64b4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905139"
---
# <a name="walkthrough-create-an-extension-pack"></a>연습: 확장 팩 만들기

확장 팩은 함께 설치할 수 있는 확장 세트입니다. 확장 팩을 사용하면 다른 사용자와 좋아하는 확장을 쉽게 공유하거나 특정 시나리오에 대한 확장 세트를 함께 번들로 묶을 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

Visual Studio 2015부터 Visual Studio SDK는 Visual Studio 설정에서 선택적 기능으로 포함됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조하세요.

확장 팩 기능은 Visual Studio 15.8 미리 보기 2부터 사용할 수 있습니다.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>확장 팩 항목 템플릿을 사용하여 확장 만들기

확장 팩 항목 템플릿은 함께 설치할 수 있는 확장 세트가 있는 확장 팩을 만듭니다.

1. **새 프로젝트** 대화 상자에서 “vsix”를 검색하고 **VSIX 프로젝트** 를 선택합니다. **프로젝트 이름** 에 “테스트 확장 팩”을 입력합니다. **만들기** 를 선택합니다.

2. **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목** 을 선택합니다. Visual C# **확장성** 노드로 이동하고 **확장 팩** 을 선택합니다. 기본 파일 이름(ExtensionPack1.cs)을 그대로 둡니다.

3. 다음 코드를 포함하는 ExtensionPack1.vsext 파일이 추가됩니다.

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. 확장 팩에 포함할 확장의 vsixid는 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)에서 찾을 수 있습니다. 포함할 확장을 찾고 **ID 복사** 를 클릭합니다. 위 파일에서 기존 **vsixId** 를 업데이트하거나 목록에 다른 확장을 추가할 수 있습니다.

    ![Marketplace에서 VsixId 복사](media/vsixid-marketplace.png)

5. 프로젝트를 빌드하고 Marketplace에 확장을 업로드합니다. [Visual Studio 확장 게시](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)를 참조하세요.

> [!NOTE]
> 확장 팩은 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 또는 [프라이빗 갤러리](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)에서 사용할 수 있는 확장만 설치할 수 있습니다.

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace에서 확장 팩 설치

확장이 게시되었으므로 이제 확장을 Visual Studio에 설치하고 테스트합니다.

::: moniker range="vs-2017"

1. Visual Studio의 **도구** 메뉴에서 **확장 및 업데이트** 를 클릭합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio의 **확장** 메뉴에서 **관리형 확장** 을 클릭합니다.

::: moniker-end

2. **온라인** 을 클릭한 다음, “테스트 확장 팩”을 검색합니다.

3. **다운로드** 를 클릭합니다. 이후 확장 팩에 포함된 확장 및 확장 목록이 설치를 위해 예약됩니다.

4. 다음은 **확장 관리** 대화 상자의 샘플 확장 팩 다운로드 보기입니다. 확장 팩에 포함된 확장 중 일부만 설치하려는 경우 **설치 예약됨** 에서 확장 목록을 수정할 수 있습니다.

    ![Marketplace에서 확장 팩 다운로드](media/vside-extensionpack.png)

5. 설치를 완료하려면 Visual Studio의 모든 인스턴스를 닫습니다.

## <a name="remove-the-extension"></a>확장 제거

컴퓨터에서 확장을 제거하려면:

::: moniker range="vs-2017"

1. Visual Studio의 **도구** 메뉴에서 **확장 및 업데이트** 를 클릭합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio의 **확장** 메뉴에서 **관리형 확장** 을 클릭합니다.

::: moniker-end

2. **테스트 확장 팩** 을 선택한 다음, **제거** 를 클릭합니다. 이후 확장 팩에 포함된 확장 및 확장 목록이 제거를 위해 예약됩니다.

3. 제거를 완료하려면 Visual Studio의 모든 인스턴스를 닫습니다.
