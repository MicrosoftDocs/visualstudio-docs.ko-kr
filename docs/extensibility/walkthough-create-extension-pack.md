---
title: 확장 팩 항목 템플릿으로 확장 팩 만들기 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697743"
---
# <a name="walkthrough-create-an-extension-pack"></a>연습: 확장 팩 만들기

확장 팩은 함께 설치할 수 있는 확장 집합입니다. 확장 팩을 사용하면 좋아하는 확장을 다른 사용자와 쉽게 공유하거나 특정 시나리오에 대해 확장 집합을 함께 번들로 묶을 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

Visual Studio 2015에서 시작하여 Visual Studio SDK는 Visual Studio 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

확장 팩 기능은 Visual Studio 15.8 미리 보기 2부터 사용할 수 있습니다.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>확장 팩 항목 템플릿으로 확장 만들기

확장 팩 항목 템플릿은 함께 설치할 수 있는 확장 집합이 있는 확장 팩을 만듭니다.

1. 새 **프로젝트** 대화 상자에서 "vsix"를 검색하고 **VSIX 프로젝트를**선택합니다. **프로젝트 이름에**대해 "테스트 확장 팩"을 입력합니다. **만들기**를 선택합니다.

2. 솔루션 **탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고**새 항목** **추가를** > 선택합니다. 시각적 C# **확장성** 노드로 이동하여 **확장 팩을**선택합니다. 기본 파일 이름(ExtensionPack1.cs)을 둡니다.

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

4. 확장 팩에 포함할 확장의 vsixid는 Visual [Studio 마켓플레이스에서](https://marketplace.visualstudio.com/)찾을 수 있습니다. 포함할 확장을 찾아 **복사 ID를**클릭합니다. 위의 파일에서 기존 **vsixId를** 업데이트하거나 목록에 다른 확장프로그램을 추가할 수 있습니다.

    ![마켓플레이스에서 VsixId 복사](media/vsixid-marketplace.png)

5. 프로젝트를 빌드하고 확장 프로그램을 마켓플레이스에 업로드합니다. [Visual Studio 확장 게시를](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)참조하십시오.

> [!NOTE]
> 확장 팩은 [Visual Studio 마켓플레이스](https://marketplace.visualstudio.com/) 또는 [개인 갤러리에서](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)사용할 수 있는 확장만 설치할 수 있습니다.

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>비주얼 스튜디오 마켓플레이스에서 확장 팩 설치

이제 확장이 게시되었으므로 Visual Studio에 설치하고 테스트합니다.

::: moniker range="vs-2017"

1. 비주얼 스튜디오에서 **도구** 메뉴에서 **확장 및 업데이트를 클릭합니다.**

::: moniker-end

::: moniker range=">=vs-2019"

1. 비주얼 스튜디오에서 **확장** 메뉴에서 **관리되는 확장 을 클릭합니다.**

::: moniker-end

2. **온라인을** 클릭한 다음 "테스트 확장 팩"을 검색합니다.

3. **다운로드**를 클릭합니다. 확장 팩에 포함된 확장 및 확장 목록은 설치일정이 잡습니다.

4. 다음은 **확장 관리** 대화 상자의 샘플 확장 팩 다운로드 보기입니다. 확장 팩에 포함된 확장 중 일부만 설치하려는 경우 **설치 예약된**에서 확장 목록을 수정할 수 있습니다.

    ![마켓플레이스에서 확장 팩 다운로드](media/vside-extensionpack.png)

5. 설치를 완료하려면 Visual Studio의 모든 인스턴스를 닫습니다.

## <a name="remove-the-extension"></a>확장 제거

컴퓨터에서 확장을 제거하려면 다음을 수행합니다.

::: moniker range="vs-2017"

1. 비주얼 스튜디오에서 **도구** 메뉴에서 **확장 및 업데이트를 클릭합니다.**

::: moniker-end

::: moniker range=">=vs-2019"

1. 비주얼 스튜디오에서 **확장** 메뉴에서 **관리되는 확장 을 클릭합니다.**

::: moniker-end

2. **테스트 확장 팩을** 선택한 다음 **제거를**클릭합니다. 확장 팩에 포함된 확장 및 확장 목록은 제거를 위해 예약됩니다.

3. 제거를 완료하려면 Visual Studio의 모든 인스턴스를 닫습니다.
