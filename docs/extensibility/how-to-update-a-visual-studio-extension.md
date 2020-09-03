---
title: '방법: Visual Studio 확장 업데이트 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee81fe30e10253239bc51dd9d2f199340debc65a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905617"
---
# <a name="how-to-update-a-visual-studio-extension"></a>방법: Visual Studio 확장 업데이트
업데이트 된 버전을 설치 하기 위해 **확장 및 업데이트** 를 사용 하 여 시스템에서 Visual Studio 확장을 업데이트할 수 있습니다. 업데이트 된 버전의 확장을 만드는 경우 VSIX 매니페스트의 버전 번호를 증가 시켜 업데이트 된 것으로 나타낼 수 있습니다.

 업데이트는 들어오는 확장의 VSIX 매니페스트가 설치 된 것과 동일 `ID` 하 고 더 높은 값을 가진 경우에 설치 됩니다 `Version` . `Version`숫자가 같거나 작으면 패키지를 설치할 수 없습니다. `ID`값이 일치 하지 않는 경우 아직 설치 되지 않은 패키지는 별도의 확장으로 인식 됩니다.

 개발 중에 충돌을 방지 하려면 이전 버전의 확장을 제거 하는 것이 좋습니다. 또한 충돌 하는 다른 확장 프로그램을 제거 하거나 사용 하지 않도록 설정 하는 것이 좋습니다.

## <a name="to-update-an-extension-on-your-system"></a>시스템에서 확장을 업데이트 하려면

1. **도구** 메뉴에서 **확장 및 업데이트**를 클릭합니다.

2. 왼쪽 창에서 **업데이트**를 클릭 합니다.

3. 가운데 창에서 설치 하려는 업데이트를 클릭 합니다.

     업데이트 된 확장의 버전 번호는 오른쪽 창에 다른 정보와 함께 표시 됩니다.

4. 오른쪽 창 맨 아래에서 **업데이트**를 클릭 합니다.

## <a name="to-publish-an-update-of-an-extension"></a>확장의 업데이트를 게시 하려면

1. Visual Studio에서 업데이트 하려는 확장에 대 한 솔루션을 엽니다. 변경을 수행 합니다.

    > [!IMPORTANT]
    > 서명 되지 않은 모든 사용자 확장은 자동으로 업데이트 되지 않습니다. 항상 확장에 서명 해야 합니다.

2. **솔루션 탐색기**에서 *소스 확장명 .manifest*를 엽니다.

3. 매니페스트 디자이너에서 **버전** 필드의 숫자 값을 늘립니다.

4. 솔루션을 저장 하 고 빌드합니다.

5. 새 *.vsix* 파일 (프로젝트의 * \bin\debug 폴더에 있는 \* )을 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) 웹 사이트에 업로드 합니다.

     이전 버전의 확장을 사용 하는 사용자가 **확장 및 업데이트**를 열면 도구에서 자동으로 업데이트를 찾도록 설정 된 새 버전이 **업데이트** 목록에 표시 됩니다.

     **업데이트 창의 맨** 아래에서 업데이트에 대 한 자동 확인을 사용 하거나 사용 하지 않도록 설정할 수 있습니다 .이는**사용 가능한 업데이트의 자동 검색을 사용 하거나 사용 하지 않도록**설정 하 여 **도구** **Check for updates**  >  **옵션**  >  **환경**  >  **확장 및 업데이트**에서 업데이트 확인 설정을 변경 합니다.

    > [!NOTE]
    > Visual Studio 2015 업데이트 2부터 **Tools**  >  **Options**  >  **Environment**  >  사용자별 확장, 모든 사용자 확장 또는 둘 다 (기본 설정)에 대해 자동 업데이트를 사용할지 여부를 도구 옵션 환경**확장 및 업데이트**에서 지정할 수 있습니다.

## <a name="see-also"></a>추가 정보
- [VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)
- [Visual Studio 확장 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)
