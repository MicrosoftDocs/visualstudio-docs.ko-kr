---
title: '방법: 비주얼 스튜디오 확장 업데이트 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 266c0a49db1bca03cec0eb68301445102173df3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710662"
---
# <a name="how-to-update-a-visual-studio-extension"></a>방법: 비주얼 스튜디오 확장 업데이트
**확장 및 업데이트를** 사용하여 업데이트된 버전을 설치하여 시스템에서 Visual Studio 확장을 업데이트할 수 있습니다. 확장의 업데이트된 버전을 만드는 경우 VSIX 매니페스트의 버전 번호를 증분하여 업데이트된 것으로 나타낼 수 있습니다.

 들어오는 확장의 VSIX 매니페스트가 설치된 확장및 `ID` 더 높은 `Version` 번호와 같을 때 업데이트가 설치됩니다. `Version` 숫자가 같거나 낮으면 패키지를 설치할 수 없습니다. `ID` 값이 일치하지 않으면 아직 설치되지 않은 패키지가 별도의 확장으로 인식됩니다.

 개발 중에 충돌을 방지하려면 진행 중인 이전 버전의 확장을 제거하고 충돌가능성이 있는 다른 확장 프로그램을 제거하거나 사용하지 않도록 설정하는 것이 좋습니다.

## <a name="to-update-an-extension-on-your-system"></a>시스템의 확장을 업데이트하려면

1. **도구** 메뉴에서 **확장 및 업데이트**를 클릭합니다.

2. 왼쪽 창에서 **업데이트를**클릭합니다.

3. 중간 창에서 설치하려는 업데이트를 클릭합니다.

     업데이트된 확장의 버전 번호는 다른 정보와 함께 오른쪽 창에 표시됩니다.

4. 오른쪽 창 하단에서 **업데이트를**클릭합니다.

## <a name="to-publish-an-update-of-an-extension"></a>확장 의 업데이트를 게시하려면

1. Visual Studio에서 업데이트할 확장에 대한 솔루션을 엽니다. 변경합니다.

    > [!IMPORTANT]
    > 서명되지 않은 모든 사용자 확장은 자동으로 업데이트되지 않습니다. 항상 확장에 서명해야 합니다.

2. **솔루션 탐색기에서**open *source.extension.manifest*.

3. 매니페스트 디자이너에서 **버전** 필드의 숫자 값을 늘립니다.

4. 솔루션을 저장하고 빌드합니다.

5. 새 *.vsix* 파일(프로젝트의 *\bin\디버그\* 폴더)을 Visual [Studio 마켓플레이스](https://marketplace.visualstudio.com/vs) 웹 사이트에 업로드합니다.

     이전 버전의 확장이 있는 사용자가 **확장 및 업데이트를**열면 도구가 자동으로 업데이트를 찾도록 설정된 경우 새 버전이 **업데이트** 목록에 표시됩니다.

      > **Options** **[옵션** **Updates**  > **Environment** > 환경 확장 및 업데이트]에서 **업데이트 확인** 설정을 변경하는 업데이트 창 하단의 업데이트 자동 검사(사용 가능한**업데이트자동 검색 사용/비활성화)를**사용하거나 비활성화할 수**있습니다.**

    > [!NOTE]
    > Visual Studio 2015 업데이트 2부터 사용자별 확장, 모든 사용자 확장 또는 둘 다(기본 설정)에 대한 자동 업데이트 여부를 지정할 수 있습니다(도구 **Tools** > **옵션** > **환경** > **확장 및 업데이트).**

## <a name="see-also"></a>참조
- [VSIX 패키지의 해부학](../extensibility/anatomy-of-a-vsix-package.md)
- [비주얼 스튜디오 확장 프로그램 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)
