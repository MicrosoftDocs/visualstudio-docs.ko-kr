---
title: 확장 게시 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5238274d66296a21e15b47d1a090ab01c1a1299d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201976"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>연습: Visual Studio 확장 기능 게시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**참고**: Visual Studio 갤러리가 Visual Studio Marketplace로 대체 되 고 있습니다. 자세한 내용은이 항목의 최신 버전을 참조 하세요.

이 연습에서는 visual studio 확장을 Visual studio 갤러리에 게시 하는 방법을 보여 줍니다. 갤러리에 확장을 추가 하면 개발자가 **확장 및 업데이트** 를 사용 하 여 새 확장과 업데이트 된 확장을 찾을 수 있습니다.

## <a name="prerequisites"></a>사전 준비 사항
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-visual-studio-extension"></a>Visual Studio 확장 만들기
 이 경우에는 기본 VSPackage 확장을 사용 하지만 동일한 단계는 모든 종류의 확장에 대해 유효 합니다.

1. 이라는 c #에서 `TestPublishing` 메뉴 명령을 포함 하는 VSPackage를 만듭니다. 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.

## <a name="test-the-extension"></a>확장 테스트
 확장을 배포 하기 전에 빌드 및 테스트 하 여 Visual Studio의 실험적 인스턴스에 제대로 설치 되었는지 확인 합니다.

1. Visual Studio에서 디버깅을 시작 합니다. Visual Studio의 실험적 인스턴스를 엽니다.

2. 실험적 인스턴스에서 **도구** 메뉴로 이동 하 여 **확장 관리자**를 클릭 합니다. TestPublishing 확장 프로그램은 가운데 창에 표시 되 고 사용 하도록 설정 되어야 합니다.

3. **도구** 메뉴에서 테스트 명령이 표시 되는지 확인 합니다.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Visual Studio 갤러리에 확장을 게시 합니다.
 이제 Visual Studio 갤러리에 확장을 게시할 수 있습니다.

1. 확장의 릴리스 버전을 빌드하고 최신 버전 인지 확인 해야 합니다.

2. 웹 브라우저에서 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트를 엽니다.

3. 오른쪽 위 모서리에서 **로그인**을 클릭 합니다.

4. Microsoft 계정을 사용하여 로그인합니다. Microsoft 계정 없는 경우이 시점에서 새로 만들 수 있습니다.

5. **업로드**를 클릭합니다.

6. **1 단계: 확장 형식**에서 **도구** 를 선택 하 고 **다음**을 클릭 합니다.

7. **2 단계: 업로드**에서 Visual Studio 갤러리에 직접 업로드 하거나 고유한 웹 사이트에 링크를 추가 하도록 선택할 수 있습니다. 이 경우 **내 도구를 업로드**합니다 .를 선택 합니다. **컨트롤 선택** 상자가 표시 됩니다. **찾아보기** 를 클릭 한 다음 프로젝트의 \bin\Release 폴더에서 testpublish .vsix를 선택 합니다. **다음**을 클릭합니다.

8. **3 단계: 기본 정보**에서는 source.extension.vsixmanifest 파일의 필드가 표시 됩니다. 사용자가 확장을 찾는 데 도움이 되도록 적절 한 **범주** 를 선택 하 고 **태그** 를 추가 합니다. 보다 자세한 요약 및 설명을 추가할 수 있습니다 (설명은 280 자 이상 이어야 함). **확장 형식은** **Microsoft 확장** 및 **비용 범주가** 아닌 **평가판**으로 그대로 둡니다.

9. 페이지 맨 아래에 있는 기여 규약을 읽고 **동의 함**을 선택 합니다.

10. **기여 만들기**를 클릭 합니다. 그러면 Visual Studio 갤러리에 확장명이 있는 페이지가 표시 되 고 페이지가 아직 게시 되지 않은 메시지가 표시 됩니다.

11. **게시**를 클릭합니다.

12. Visual Studio 갤러리에서 확장을 검색 합니다. TestPublish 확장의 목록이 표시 됩니다.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Visual Studio 갤러리에서 확장을 설치 합니다.
 이제 확장이 게시 되었으므로 Visual Studio에 설치 하 고 테스트 합니다.

1. Visual Studio의 **도구** 메뉴에서 **확장 및 업데이트**를 클릭 합니다.

2. **온라인** 을 클릭 한 다음 testpublish를 검색 합니다. TestPublish 확장의 목록이 표시 됩니다.

3. **다운로드**를 클릭합니다. 확장을 다운로드한 후 **설치**를 클릭합니다.

4. 설치를 완료 하려면 Visual Studio를 다시 시작 합니다.

## <a name="removing-the-extension"></a>확장 제거
 Visual Studio 갤러리와 컴퓨터에서 확장을 제거할 수 있습니다.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Visual Studio 갤러리에서 확장을 제거 하려면

1. [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트를 엽니다.

2. 오른쪽 위 모서리에서 **내 Extenions**를 클릭 합니다. TestPublish에 대 한 목록이 표시 됩니다.

3. **삭제**를 클릭합니다.

#### <a name="to-remove-the-extension-from-your-computer"></a>컴퓨터에서 확장을 제거 하려면

1. Visual Studio의 **도구** 메뉴에서 **확장 관리자**를 클릭합니다.

2. TestPublish를 선택 하 고 **제거**를 클릭 합니다.

3. 제거를 완료 하려면 Visual Studio를 다시 시작 합니다.
