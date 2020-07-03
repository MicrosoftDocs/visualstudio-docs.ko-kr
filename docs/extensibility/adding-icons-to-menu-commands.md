---
title: 메뉴 명령에 아이콘 추가 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9f038dc43c1705a7cef47eb09a17607c535e307
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903440"
---
# <a name="add-icons-to-menu-commands"></a>메뉴 명령에 아이콘 추가
메뉴와 도구 모음 모두에 명령이 표시 될 수 있습니다. 도구 모음에서 일반적으로 명령을 사용 하 여 공간을 절약 하기 위해 명령을 표시 하는 것이 일반적입니다. 명령에는 일반적으로 아이콘과 텍스트가 모두 표시 됩니다.

 아이콘은 16 픽셀 너비의 16 픽셀이 며 8 비트 색 농도 (256 색) 또는 32 비트 색 농도 (트루 컬러) 일 수 있습니다. 32 비트 색 아이콘이 기본 설정 되어 있습니다. 아이콘은 일반적으로 여러 비트맵이 허용 되지만 단일 가로 행으로 정렬 됩니다. 이 비트맵은 비트맵에서 사용할 수 있는 개별 아이콘과 함께 *vsct* 파일에 선언 됩니다. 자세한 내용은 [비트맵 요소](../extensibility/bitmaps-element.md) 에 대 한 참조를 참조 하세요.

## <a name="add-an-icon-to-a-command"></a>명령에 아이콘 추가
 다음 절차에서는 기존 VSPackage 프로젝트에 메뉴 명령을 사용 한다고 가정 합니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)를 참조 하세요.

1. 32 비트 색 농도를 사용 하 여 비트맵을 만듭니다. 아이콘은 항상 16 x 16 이므로이 비트맵의 높이는 16 픽셀이 고 너비가 16 픽셀의 배수 여야 합니다.

     각 아이콘은 단일 행에서 각 아이콘 옆에 있는 비트맵에 배치 됩니다. 알파 채널을 사용 하 여 각 아이콘의 투명도 위치를 표시 합니다.

     8 비트 색 농도를 사용 하는 경우 투명도로 마젠타를 사용 `RGB(255,0,255)` 합니다. 그러나 32 비트 색 아이콘이 기본 설정 되어 있습니다.

2. 아이콘 파일을 VSPackage 프로젝트의 *Resources* 디렉터리에 복사 합니다. **솔루션 탐색기**에서 프로젝트에 아이콘을 추가 합니다. **리소스**를 선택 하 고 상황에 맞는 메뉴에서 **추가**를 클릭 한 다음 **기존 항목**을 클릭 하 고 아이콘 파일을 선택 합니다.

3. 편집기에서 *vsct* 파일을 엽니다.

4. `GuidSymbol`이름이 **testicon**인 요소를 추가 합니다. Guid**를 만들고 guid**  >  를**만든**다음 **레지스트리 형식을** 선택 하 고 **복사**를 클릭 하 여 특성에 붙여넣습니다 `value` . 결과는 다음과 같습니다.

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. `<IDSymbol>`아이콘에를 추가 합니다. `name`특성은 아이콘의 ID 이며,은 스트립의 `value` 해당 위치를 나타냅니다 (있는 경우). 아이콘이 하나만 있는 경우 1을 추가 합니다. 결과는 다음과 같습니다.

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. 아이콘을 `<Bitmap>` 포함 하는 `<Bitmaps>` 비트맵을 나타내기 위해 *vsct* 파일의 섹션에를 만듭니다.

    - 값을 `guid` `<GuidSymbol>` 이전 단계에서 만든 요소의 이름으로 설정 합니다.

    - 값을 `href` 비트맵 파일의 상대 경로 (이 경우 **리소스 \\<아이콘 파일 이름 \> **)로 설정 합니다.

    - 값을 `usedList` 앞에서 만든 IDSymbol로 설정 합니다. 이 특성은 VSPackage에서 사용할 아이콘의 쉼표로 구분 된 목록을 지정 합니다. 목록에 없는 아이콘은 양식 컴파일이 제외 됩니다.

         비트맵 블록은 다음과 같습니다.

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. 기존 요소에서 `<Button>` 요소를 앞에서 `Icon` 만든 GUIDSymbol 및 idsymbol 값으로 설정 합니다. 다음은 이러한 값을 포함 하는 Button 요소의 예입니다.

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. 아이콘을 테스트 합니다. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스에서 명령을 찾습니다. 추가한 아이콘이 표시 됩니다.

## <a name="see-also"></a>참조
- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
- [VSCT XML 스키마 참조](../extensibility/vsct-xml-schema-reference.md)
