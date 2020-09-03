---
title: 확장 팩 항목 템플릿을 사용 하 여 확장 팩 만들기 | Microsoft Docs
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: acangialosi
ms.author: anthc
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: fa1c141e18a3870eaad4b155d816e30ee207f45d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697743"
---
# <a name="walkthrough-create-an-extension-pack"></a>연습: 확장 팩 만들기

확장 팩은 함께 설치할 수 있는 확장 집합입니다. 확장 팩을 사용 하면 즐겨 찾는 확장을 다른 사용자와 쉽게 공유 하거나 특정 시나리오에 맞게 확장 집합을 묶을 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

Visual studio 2015부터 visual studio SDK는 visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

Visual Studio 15.8 Preview 2부터 확장 팩 기능을 사용할 수 있습니다.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>확장 팩 항목 템플릿을 사용 하 여 확장 만들기

확장 팩 항목 템플릿은 함께 설치할 수 있는 확장 집합을 사용 하 여 확장 팩을 만듭니다.

1. **새 프로젝트** 대화 상자에서 "vsix"를 검색 하 고 **vsix 프로젝트**를 선택 합니다. **프로젝트 이름**에 "Test Extension Pack"을 입력 합니다. **만들기**를 선택합니다.

2. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **Add**  >  **새 항목**추가를 선택 합니다. Visual c # **확장성** 노드로 이동 하 고 **확장 팩**을 선택 합니다. 기본 파일 이름 (ExtensionPack1.cs)을 그대로 둡니다.

3. 다음 코드를 포함 하는 vsext 파일이 추가 ExtensionPack1.

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

4. 확장 팩에 포함할 확장의 vsixid [Visual Studio Marketplace](https://marketplace.visualstudio.com/)에서 찾을 수 있습니다. 포함 하려는 확장을 찾고 **복사 ID**를 클릭 합니다. 위의 파일에서 기존 **vsixId** 를 업데이트 하거나 목록에 다른 확장을 추가할 수 있습니다.

    ![Marketplace에서 VsixId 복사](media/vsixid-marketplace.png)

5. 프로젝트를 빌드하고 Marketplace에 확장을 업로드 합니다. [Visual Studio 확장 게시를](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)참조 하세요.

> [!NOTE]
> 확장 팩은 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 또는 [전용 갤러리](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)에서 사용할 수 있는 확장만 설치할 수 있습니다.

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace에서 확장 팩을 설치 합니다.

이제 확장이 게시 되었으므로 Visual Studio에 설치 하 고 테스트 합니다.

::: moniker range="vs-2017"

1. Visual Studio의 **도구** 메뉴에서 **확장 및 업데이트**를 클릭 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio의 **확장** 메뉴에서 **관리 되는 확장**을 클릭 합니다.

::: moniker-end

2. **온라인** 을 클릭 한 다음 "테스트 확장 팩"을 검색 합니다.

3. **다운로드**를 클릭합니다. 확장 팩에 포함 된 확장 및 확장 목록에는 설치를 위해 예약 됩니다.

4. 다음은 **확장 관리** 대화 상자의 샘플 확장 팩 다운로드 뷰입니다. 확장 팩에 포함 된 확장 중 일부만 설치 하려는 경우에는 **설치 예약**됨에서 확장 목록을 수정할 수 있습니다.

    ![Marketplace에서 확장 팩 다운로드](media/vside-extensionpack.png)

5. 설치를 완료 하려면 Visual Studio의 모든 인스턴스를 닫습니다.

## <a name="remove-the-extension"></a>확장 제거

컴퓨터에서 확장을 제거 하려면 다음을 수행 합니다.

::: moniker range="vs-2017"

1. Visual Studio의 **도구** 메뉴에서 **확장 및 업데이트**를 클릭 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio의 **확장** 메뉴에서 **관리 되는 확장**을 클릭 합니다.

::: moniker-end

2. **테스트 확장 팩** 을 선택 하 고 **제거**를 클릭 합니다. 확장 팩에 포함 된 확장 및 확장명 목록에 제거를 예약 합니다.

3. 제거를 완료 하려면 Visual Studio의 모든 인스턴스를 닫습니다.
