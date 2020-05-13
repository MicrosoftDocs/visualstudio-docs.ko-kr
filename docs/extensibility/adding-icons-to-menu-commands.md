---
title: 메뉴 명령에 아이콘 추가 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: f4b71f981472451766f526cf62e975e571cf46da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740159"
---
# <a name="add-icons-to-menu-commands"></a>메뉴 명령에 아이콘 추가
명령은 메뉴와 도구 모음 모두에 나타날 수 있습니다. 도구 모음에서 명령은 아이콘(공간 절약)으로 표시되는 반면 메뉴에서는 일반적으로 명령이 아이콘과 텍스트로 모두 나타납니다.

 아이콘의 너비는 16픽셀 x 16픽셀이며 8비트 색상 깊이(256개 색상) 또는 32비트 색상 깊이(실제 색상)일 수 있습니다. 32비트 색상 아이콘이 선호됩니다. 아이콘은 일반적으로 여러 비트맵이 허용되지만 일반적으로 단일 비트맵의 단일 가로 행에 정렬됩니다. 이 비트맵은 비트맵에서 사용할 수 있는 개별 아이콘과 함께 *.vsct* 파일에 선언됩니다. 자세한 내용은 [비트맵 요소에](../extensibility/bitmaps-element.md) 대한 참조를 참조하십시오.

## <a name="add-an-icon-to-a-command"></a>명령에 아이콘 추가
 다음 절차에서는 메뉴 명령이 있는 기존 VSPackage 프로젝트가 있다고 가정합니다. 이 작업을 수행하는 방법을 알아보려면 [메뉴 명령을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-a-menu-command.md)참조하십시오.

1. 색상 깊이가 32비트인 비트맵을 만듭니다. 아이콘은 항상 16 x 16이므로 이 비트맵의 너비는 16픽셀이고 너비는 16픽셀이어야 합니다.

     각 아이콘은 한 행의 비트맵 옆에 배치됩니다. 알파 채널을 사용하여 각 아이콘의 투명도 를 나타냅니다.

     8비트 색상 깊이를 사용하는 경우 마젠타를 `RGB(255,0,255)`투명도로 사용합니다. 그러나 32비트 색상 아이콘이 선호됩니다.

2. VSPackage 프로젝트의 *리소스* 디렉토리에 아이콘 파일을 복사합니다. 솔루션 **탐색기에서**프로젝트에 아이콘을 추가합니다. (리소스 **Resources**를 선택하고 상황에 맞는 메뉴에서 **추가를**클릭한 다음 **기존 항목**, 아이콘 파일을 선택합니다.)

3. 편집기에서 *.vsct* 파일을 엽니다.

4. `GuidSymbol` **testIcon의**이름으로 요소를 추가 합니다. GUID 만들기 **(도구** > **GUID 만들기,** **레지스트리 형식** 및 **복사를**클릭)를 선택 하 고 특성에 `value` 붙여 넣습니다. 결과는 다음과 같아야 합니다.

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. 아이콘에 `<IDSymbol>` 대한 아이콘을 추가합니다. 속성은 `name` 아이콘의 ID이며, 있는 `value` 경우 스트립에서 해당 위치를 나타냅니다. 아이콘이 하나만 있는 경우 1을 추가합니다. 결과는 다음과 같아야 합니다.

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. *.vsct* `<Bitmaps>` 파일의 섹션에서 아이콘이 포함된 비트맵을 나타내기 위해 a를 `<Bitmap>` 만듭니다.

    - `guid` 값을 이전 단계에서 만든 `<GuidSymbol>` 요소의 이름으로 설정합니다.

    - 비트맵 파일의 상대 경로로 값을 설정합니다(이 경우 **\\ 리소스\><아이콘 파일 이름입니다.** `href`

    - `usedList` 이전에 만든 ID기호로 값을 설정합니다. 이 특성은 VSPackage에서 사용할 아이콘의 쉼표 구분 목록을 지정합니다. 목록에 없는 아이콘은 양식 컴파일에서 제외됩니다.

         비트맵 블록은 다음과 같아야 합니다.

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. 기존 `<Button>` 요소에서 `Icon` 요소를 GUIDSymbol 및 IDSymbol 값으로 설정합니다. 다음은 이러한 값을 가진 Button 요소의 예입니다.

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. 아이콘을 테스트합니다. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험 인스턴스에서 명령을 찾습니다. 추가한 아이콘이 표시됩니다.

## <a name="see-also"></a>참조
- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
- [VSCT XML 스키마 참조](../extensibility/vsct-xml-schema-reference.md)
