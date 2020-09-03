---
title: '연습: Visual Studio 확장 게시 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6bd7a5d9622f7aea7382522dcf69ce660b61ae7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904737"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>연습: Visual Studio 확장 게시

이 연습에서는 Visual Studio Marketplace에 Visual Studio 확장을 게시 하는 방법을 보여 줍니다. Marketplace에 확장을 추가 하면 개발자가 **확장 및 업데이트** 를 사용 하 여 새 확장과 업데이트 된 확장을 찾아볼 수 있습니다.

## <a name="prerequisites"></a>전제 조건

 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-visual-studio-extension"></a>Visual Studio 확장 만들기

이 문서에서는 기본 VSPackage 확장을 사용 하지만 단계는 모든 종류의 확장에 대해 유효 합니다.

1. 이라는 c #에서 `TestPublish` 메뉴 명령을 포함 하는 VSPackage를 만듭니다. 자세한 내용은 [첫 번째 확장 만들기: Hello World](../extensibility/extensibility-hello-world.md)를 참조 하세요.

## <a name="package-your-extension"></a>확장 패키지

1. 제품 이름, 저자 및 버전에 대 한 올바른 정보로 *source.extension.vsixmanifest* 를 업데이트 합니다.

   ![확장 source.extension.vsixmanifest 업데이트](media/update-extension-vsixmanifest.png)

2. **릴리스** 모드에서 확장을 빌드합니다. 이제 확장이 \bin\Release 폴더에 VSIX로 패키지 됩니다.

3. VSIX를 두 번 클릭 하 여 설치를 확인할 수 있습니다.

## <a name="test-the-extension"></a>확장 테스트

 확장을 배포 하기 전에 빌드 및 테스트 하 여 Visual Studio의 실험적 인스턴스에 제대로 설치 되었는지 확인 합니다.

1. Visual Studio에서 디버깅을 시작 하 여 Visual Studio의 실험적 인스턴스를 엽니다.

2. 실험적 인스턴스에서 **도구** 메뉴로 이동 하 고 **확장 및 업데이트**를 클릭 합니다. TestPublish 확장은 가운데 창에 표시 되 고 사용 하도록 설정 되어야 합니다.

3. **도구** 메뉴에서 테스트 명령이 표시 되는지 확인 합니다.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Visual Studio Marketplace 확장을 게시 합니다.

1. 확장의 릴리스 버전을 빌드하고 최신 버전 인지 확인 해야 합니다.

2. 웹 브라우저에서 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) 웹 사이트를 엽니다.

3. 오른쪽 위 모서리에서 **로그인**을 클릭 합니다.

4. Microsoft 계정을 사용하여 로그인합니다. Microsoft 계정 없는 경우이 시점에서 새로 만들 수 있습니다.

5. **확장 게시**를 클릭 합니다.  이 옵션은 모든 확장에 대 한 관리 페이지로 이동 합니다. 게시자 계정이 없는 경우 지금 만들 수 있는 메시지가 표시 됩니다.

   ![Marketplace에 업로드](media/upload-to-marketplace.png)

6. 확장을 업로드 하는 데 사용 하려는 게시자를 선택 합니다. 왼쪽에 나열 된 게시자 이름을 클릭 하 여 게시자를 변경할 수 있습니다. **새 확장** 을 클릭 하 고 **Visual Studio**를 선택 합니다.

7. **1: 업로드 확장**에서 VSIX 파일을 Visual Studio Marketplace에 직접 업로드 하거나 자체 웹 사이트에 링크를 추가 하도록 선택할 수 있습니다. 이 예제에서는 *Testpublish .vsix* 확장을 업로드 합니다. 확장을 끌어서 놓거나 **클릭** 링크를 사용 하 여 파일을 찾습니다. 프로젝트의 \bin\Release 폴더에서 확장을 찾습니다.  **계속**을 클릭합니다.

8. **2: 확장 세부 정보 제공**에서 일부 필드는 확장의 *source.extension.vsixmanifest* 파일에서 자동으로 채워집니다. 아래 각 항목에 대 한 자세한 내용을 확인 하세요.

    * **내부 이름은** 확장 세부 정보 페이지의 URL에 사용 됩니다. 예를 들어 게시자 이름 "myname" 아래에 확장을 게시 하 고 내부 이름을 "my extension"으로 지정 하면 \. 확장의 세부 정보 페이지에 대 한 "marketplace. visualstudio com/items? itemName = myname" 라는 URL이 생성 됩니다.

    * 확장의 **표시 이름** 입니다. 이 이름은 *source.extension.vsixmanifest* 파일에서 자동으로 채워집니다.

    * 업로드할 확장의 **버전** 번호입니다. 이 버전은 *source.extension.vsixmanifest* 파일에서 자동으로 채워집니다.

    * **VSIX ID** 는 Visual Studio에서 확장에 사용 하는 고유 식별자입니다. 이 식별자는 확장을 자동으로 업데이트 하려는 경우에 필요 합니다. 이 식별자는 *source.extension.vsixmanifest* 파일에서 자동으로 채워집니다.

    * 확장에 사용 되는 **로고** 입니다. 이 로고는 제공 된 경우 *source.extension.vsixmanifest* 파일에서 자동으로 채워집니다.

    * 확장의 용도에 대 한 **간단한 설명** 입니다. 이 설명은 *source.extension.vsixmanifest* 파일에서 자동으로 채워집니다.

    * **개요** 는 스크린샷 및 확장의 용도에 대 한 자세한 정보를 포함 하는 좋은 장소입니다.

    * **지원 되는 Visual studio 버전** 에서는 확장이 작동 하는 visual studio 버전을 선택할 수 있습니다. 확장은 해당 버전에만 설치 됩니다.

    * * * 지원 되는 Visual Studio 버전에서는 확장이 작동 하는 Visual Studio 버전을 선택할 수 있습니다. 확장은 해당 버전에만 설치 됩니다.

    * **Type**. 가장 일반적인 확장 유형은 **도구**입니다.

    * **범주**. 확장에 가장 적합 한 최대 3 개까지 선택 합니다.

    * **태그** 는 사용자가 확장을 찾는 데 도움이 되는 키워드입니다. 태그를 통해 Marketplace에서 확장의 검색 관련성을 높일 수 있습니다.

    * **가격 책정 범주** 는 확장의 비용입니다.

    * **소스 코드 리포지토리** 를 사용 하 여 소스 코드에 대 한 링크를 커뮤니티와 공유할 수 있습니다.

    * 사용자 **확장에 대 한 질문&을 허용** 하면 확장 입력 페이지에서 질문을 남길 수 있습니다.

9. **저장 & 업로드**를 클릭 합니다. 이 옵션은 게시자 관리 페이지로 돌아갑니다. 확장이 아직 게시 되지 않았습니다. 확장을 게시 하려면 확장을 마우스 오른쪽 단추로 클릭 하 고 **공개로 설정**을 선택 합니다. **확장 보기**를 선택 하 여 Marketplace에서 확장이 어떻게 표시 되는지 볼 수 있습니다. 취득 번호의 경우 **보고서**를 클릭 합니다. 확장을 변경 하려면 **편집**을 클릭 합니다.

   ![확장 항목 메뉴](media/extension-entry-menu.png)

10. 공용으로 **설정**을 클릭 하면 확장이 이제 공개입니다. 확장 프로그램에 대 한 Visual Studio Marketplace를 검색 합니다.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>사용자를 추가 하 여 게시자 계정 관리

Marketplace에서는 게시자 계정에 액세스 하 고 관리할 수 있는 추가 사용자 권한을 부여 하는 것을 지원 합니다.

1. 사용자를 추가 하려는 게시자 계정으로 이동 합니다.

2. **멤버** 를 선택 하 고 **추가**를 클릭 합니다.

   ![추가 사용자 추가](media/add-users.png)

3. 그런 다음 추가 하려는 사용자의 메일 주소를 지정 하 고 **역할 선택**에서 올바른 액세스 수준을 부여할 수 있습니다.  다음 옵션 중에서 선택할 수 있습니다.

   * **작성자**: 사용자는 확장을 게시할 수 있지만 다른 사용자가 게시 한 확장을 보거나 관리할 수는 없습니다.

   * **읽기 권한자**: 사용자는 확장을 볼 수 있지만 확장을 게시 하거나 관리할 수 없습니다.

   * **참가자**: 사용자는 확장을 게시 및 관리할 수 있지만 게시자 설정을 편집 하거나 액세스를 관리할 수는 없습니다.

   * **소유자**: 사용자는 확장을 게시 및 관리 하 고, 게시자 설정을 편집 하 고, 액세스를 관리할 수 있습니다.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace에서 확장을 설치 합니다.

이제 확장이 게시 되었으므로 Visual Studio에 설치 하 고 테스트 합니다.

1. Visual Studio의 **도구** 메뉴에서 **확장 및 업데이트**를 클릭 합니다.

2. **온라인** 을 클릭 한 다음 **testpublish**를 검색 합니다.

3. **다운로드**를 클릭합니다. 그러면 확장이 설치 되도록 예약 됩니다.

4. 설치를 완료 하려면 Visual Studio의 모든 인스턴스를 닫습니다.

## <a name="remove-the-extension"></a>확장 제거

Visual Studio Marketplace 및 컴퓨터에서 확장을 제거할 수 있습니다.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace에서 확장을 제거 하려면

1. [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) 웹 사이트를 엽니다.

2. 오른쪽 위 모서리에서 확장 **게시** 를 클릭 합니다. **Testpublish**를 게시 하는 데 사용한 게시자를 선택 합니다. **Testpublish** 에 대 한 목록이 표시 됩니다.

3. 확장 항목을 마우스 오른쪽 단추로 클릭 하 고 **제거**를 클릭 합니다. 확장의 제거 여부를 확인 하는 메시지가 표시 됩니다. **확인**을 클릭합니다.

### <a name="to-remove-the-extension-from-your-computer"></a>컴퓨터에서 확장을 제거 하려면

1. Visual Studio의 **도구** 메뉴에서 **확장 및 업데이트**를 클릭 합니다.

2. **Testpublish** 를 선택 하 고 **제거**를 클릭 합니다. 그런 다음 확장이 제거 되도록 예약 됩니다.

3. 제거를 완료 하려면 Visual Studio의 모든 인스턴스를 닫습니다.
