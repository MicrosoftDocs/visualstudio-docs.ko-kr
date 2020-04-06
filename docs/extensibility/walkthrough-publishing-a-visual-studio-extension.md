---
title: '연습: 비주얼 스튜디오 확장 게시 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a34260124baedeba297dbd64e8a2c1856b55ec5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697135"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>연습: 비주얼 스튜디오 확장 게시

이 연습에서는 Visual Studio 마켓플레이스에 Visual Studio 확장을 게시하는 방법을 보여 주며 이 연습에서는 Visual Studio 확장 프로그램을 게시하는 방법을 보여 주며, 이 연습에서는 Visual Studio 마켓플레이스에 게시하는 방법을 보여 주며, 이 연습에서는 Visual Studio 확장 프로그램을 게시하는 방법을 마켓플레이스에 확장을 추가하면 개발자는 **확장 및 업데이트를** 사용하여 새 확장 및 업데이트된 확장을 찾아볼 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-visual-studio-extension"></a>비주얼 스튜디오 확장 만들기

이 문서에서는 기본 VSPackage 확장을 사용 하지만 단계는 모든 종류의 확장에 대 한 유효 합니다.

1. 메뉴 명령이 있는 이름의 `TestPublish` C#에서 VSPackage를 만듭니다. 자세한 내용은 [첫 번째 확장 프로그램 만들기: Hello World](../extensibility/extensibility-hello-world.md)를 참조하십시오.

## <a name="package-your-extension"></a>확장 패키지

1. 제품 이름, 작성자 및 버전에 대한 올바른 정보로 확장 *.vsixmanifest를* 업데이트합니다.

   ![업데이트 확장 vsixmanifest](media/update-extension-vsixmanifest.png)

2. **릴리스** 모드에서 확장을 빌드합니다. 이제 확장이 \bin\Release 폴더에서 VSIX로 패키징됩니다.

3. VSIX를 두 번 클릭하여 설치를 확인할 수 있습니다.

## <a name="test-the-extension"></a>확장 테스트

 확장을 배포하기 전에 빌드하고 테스트하여 Visual Studio의 실험 인스턴스에 올바르게 설치되었는지 확인합니다.

1. Visual Studio에서 디버깅을 시작하여 Visual Studio의 실험인스턴스를 엽니다.

2. 실험 인스턴스에서 **도구** 메뉴로 이동하여 **확장 및 업데이트를 클릭합니다.** TestPublish 확장은 가운데 창에 나타나고 활성화되어야 합니다.

3. **도구** 메뉴에서 테스트 명령이 표시되는지 확인합니다.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>비주얼 스튜디오 마켓플레이스에 확장 게시

1. 확장의 릴리스 버전을 빌드하 고 최신 인지 확인 합니다.

2. 웹 브라우저에서 Visual [Studio 마켓플레이스](https://marketplace.visualstudio.com/vs) 웹 사이트를 엽니다.

3. 오른쪽 위 모서리에서 **로그인을 클릭합니다.**

4. Microsoft 계정을 사용하여 로그인합니다. Microsoft 계정이 없는 경우 이 시점에서 계정을 만들 수 있습니다.

5. **확장 게시를 클릭합니다.**  이 옵션은 모든 확장에 대한 관리 페이지로 이동합니다. 게시자 계정이 없는 경우 현재 계정을 만들라는 메시지가 표시됩니다.

   ![마켓플레이스에 업로드](media/upload-to-marketplace.png)

6. 확장 프로그램을 업로드하는 데 사용할 게시자를 선택합니다. 왼쪽에 나열된 게시자 이름을 클릭하여 게시자를 변경할 수 있습니다. 새 **확장을** 클릭하고 **Visual Studio를**선택합니다.

7. **1: 확장 자 업로드**, Visual Studio 마켓플레이스에 직접 VSIX 파일을 업로드하거나 자신의 웹 사이트에 대한 링크를 추가하도록 선택할 수 있습니다. 이 예제에서는 확장, *TestPublish.vsix가* 업로드됩니다. 확장 프로그램을 드래그 앤 드롭하거나 **클릭** 링크를 사용하여 파일을 찾아봅슬합니다. 프로젝트의 \bin\Release 폴더에서 확장을 찾습니다.  **Continue(계속)** 를 클릭합니다.

8. **2: 확장 세부 정보를 제공,** 일부 필드는 *확장자에서 source.extension.vsixmanifest* 파일에서 자동 채워집니다. 아래에서 각각에 대한 자세한 내용을 찾아보십시오.

    * **내부 이름은** 확장의 세부 정보 페이지의 URL에 사용됩니다. 예를 들어 게시자 이름 "myname"에 확장을 게시하고 내부 이름을 "내 확장"으로 지정하면 확장 세부\.정보 페이지에 "marketplace.visualstudio com/items?itemName=myname.myextension"의 URL이 표시됩니다.

    * 확장 프로그램의 **이름을 표시합니다.** 이 이름은 *source.extension.vsixmanifest* 파일에서 자동으로 채워집니다.

    * 업로드하는 확장 프로그램의 **버전** 번호입니다. 이 버전은 *source.extension.vsixmanifest* 파일에서 자동으로 채워집니다.

    * **VSIX ID는** Visual Studio에서 확장에 사용하는 고유 식별자입니다. 확장을 자동으로 업데이트하려면 이 식별자가 필요합니다. 이 식별자는 *source.extension.vsixmanifest* 파일에서 자동으로 채워집니다.

    * 확장에 사용되는 **로고입니다.** 이 로고는 제공된 경우 *source.extension.vsixmanifest* 파일에서 자동으로 채워집니다.

    * 확장 이 수행하는 기능에 대한 **간략한 설명입니다.** 이 설명은 *source.extension.vsixmanifest* 파일에서 자동으로 채워집니다.

    * **개요는** 스크린샷과 광고 확장이 수행하는 일에 대한 자세한 정보를 포함하는 좋은 장소입니다.

    * **지원되는 Visual Studio 버전을** 사용하면 확장 프로그램이 작동할 Visual Studio 버전을 선택할 수 있습니다. 확장 프로그램은 해당 버전에만 설치됩니다.

    * ** 지원되는 비주얼 스튜디오 에디션을 사용하면 확장 프로그램이 작동할 Visual Studio 버전을 선택할 수 있습니다. 확장 프로그램은 해당 버전에만 설치됩니다.

    * **유형** - 확장의 가장 일반적인 유형은 **도구**입니다.

    * **범주**. 확장에 가장 적합한 3개까지 픽업할 수 있습니다.

    * **태그는** 사용자가 광고 확장을 찾는 데 도움이 되는 키워드입니다. 태그는 마켓플레이스에서 광고 확장의 검색 관련성을 높이는 데 도움이 될 수 있습니다.

    * **가격 카테고리는** 확장 비용입니다.

    * **소스 코드 리포지토리를** 사용하면 소스 코드에 대한 링크를 커뮤니티와 공유할 수 있습니다.

    * **확장에 대한 Q&A 허용을** 사용하면 사용자가 확장 항목 페이지에 질문을 남길 수 있습니다.

9. **& 업로드 저장을**클릭합니다. 이 옵션을 사용하면 게시자 관리 페이지로 돌아갑니다. 광고 확장이 아직 게시되지 않았습니다. 내선 프로그램을 게시하려면 광고 확장을 마우스 오른쪽 단추로 클릭하고 **공개 하기 를**선택합니다. **[보기]** 에서 확장 보기를 선택하여 마켓플레이스에서 확장이 어떻게 보이는지 볼 수 있습니다. 획득 번호의 경우 **보고서를**클릭합니다. 확장을 변경하려면 **편집을**클릭합니다.

   ![확장 항목 메뉴](media/extension-entry-menu.png)

10. **공개를**클릭하면 확장이 공개됩니다. 확장에 대한 비주얼 스튜디오 마켓플레이스를 검색합니다.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>게시자 계정을 관리하는 사용자를 추가합니다.

Marketplace는 게시자 계정에 액세스하고 관리할 수 있는 추가 사용자에게 권한을 부여하는 것을 지원합니다.

1. 사용자를 추가하려는 게시자 계정으로 이동합니다.

2. **멤버를** 선택하고 **추가**를 클릭합니다.

   ![추가 사용자 추가](media/add-users.png)

3. 그런 다음 추가하려는 사용자의 전자 메일 주소를 지정하고 **역할 선택에서**적절한 액세스 수준을 부여할 수 있습니다.  다음 옵션 중에서 선택할 수 있습니다.

   * **작성자**: 사용자는 확장을 게시할 수 있지만 다른 사용자가 게시한 확장을 보거나 관리할 수는 없습니다.

   * **Reader**: 사용자는 확장을 볼 수 있지만 확장을 게시하거나 관리할 수는 없습니다.

   * **기여자**: 사용자는 확장을 게시하고 관리할 수 있지만 게시자 설정을 편집하거나 액세스를 관리할 수는 없습니다.

   * **소유자**: 사용자는 확장을 게시 및 관리하고 게시자 설정을 편집하고 액세스를 관리할 수 있습니다.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>비주얼 스튜디오 마켓플레이스에서 확장 설치

이제 확장이 게시되었으므로 Visual Studio에 설치하고 테스트합니다.

1. 비주얼 스튜디오에서 **도구** 메뉴에서 **확장 및 업데이트를 클릭합니다.**

2. **온라인을** 클릭한 다음 **테스트 게시**를 검색합니다.

3. **다운로드**를 클릭합니다. 그런 다음 확장이 설치될 예정입니다.

4. 설치를 완료하려면 Visual Studio의 모든 인스턴스를 닫습니다.

## <a name="remove-the-extension"></a>확장 제거

Visual Studio 마켓플레이스와 컴퓨터에서 확장을 제거할 수 있습니다.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>비주얼 스튜디오 마켓플레이스에서 확장을 제거하려면

1. 비주얼 [스튜디오 마켓플레이스](https://marketplace.visualstudio.com/vs) 웹 사이트를 엽니다.

2. 오른쪽 상단 모서리에서 광고 확장 **게시를** 클릭합니다. **테스트 게시를**게시하는 데 사용한 게시자를 선택합니다. **테스트 게시에** 대한 목록이 나타납니다.

3. 내선 항목에서 마우스 오른쪽 단추를 클릭하고 **제거를**클릭합니다. 확장을 제거할지 확인하라는 메시지가 표시됩니다. **확인**을 클릭합니다.

### <a name="to-remove-the-extension-from-your-computer"></a>컴퓨터에서 확장을 제거하려면

1. 비주얼 스튜디오에서 **도구** 메뉴에서 **확장 및 업데이트를 클릭합니다.**

2. **테스트 게시를** 선택한 다음 **제거 를**클릭합니다. 그런 다음 확장을 제거할 수 있습니다.

3. 제거를 완료하려면 Visual Studio의 모든 인스턴스를 닫습니다.
