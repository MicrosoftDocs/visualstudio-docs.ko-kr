---
title: Blend에서 XAML 디버그 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 29a37182-2a2c-47e4-a4a9-2d5412738fed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: d5d40878e40641b9a54a411af122f6207a02a7a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331043"
---
# <a name="debug-xaml-in-blend"></a>Blend에서 XAML 디버그

Blend for Visual Studio의 도구를 사용 하 여 앱에서 XAML을 디버그할 수 있습니다. 프로젝트를 빌드할 때 모든 오류는 **결과** 패널에 표시됩니다. 오류를 두 번 클릭하여 오류와 관련된 태그를 찾습니다. 작업할 공간이 더 필요한 경우 **F12**키를 눌러 **결과** 패널을 숨길 수 있습니다.

## <a name="syntax-errors"></a>구문 오류

구문 오류는 XAML 또는 코드 숨김 파일이 언어의 서식 설정 규칙을 준수하지 않는 경우에 발생합니다. 오류 설명을 보면 오류 해결 방법을 파악할 수 있습니다. 오류가 발생하는 파일의 이름 및 줄 번호도 함께 설명됩니다. XAML 오류는 **결과** 패널의 **태그** 탭에 나열되어 있습니다.

> [!TIP]
> XAML은 XML을 기반으로 하는 태그 언어로 XML 구문 규칙을 따릅니다.

XAML 구문 오류의 몇 가지 일반적인 원인은 다음과 같습니다.

- 키워드에 맞춤법 오류가 있거나 대문자 표시가 잘못되었습니다.

- 특성 또는 텍스트 문자열 주위에 따옴표가 없습니다.

- XAML 요소에 닫는 태그가 없습니다.

- XAML 요소가 허용되지 않는 위치에 있습니다.

공용 XAML 구문에 대한 자세한 내용은 [기본 XAML 구문 가이드](/windows/uwp/xaml-platform/xaml-syntax-guide)를 참조하십시오.

Blend에서 간단한 코드 숨겨진 구문 오류, 컴파일 오류 및 런타임 오류를 식별 하 고 해결할 수도 있습니다. 하지만 코드 숨김 오류는 Visual Studio에서 더욱 쉽게 식별 및 해결할 수 있습니다.

### <a name="debugging-sample-xaml-code"></a>디버깅 샘플 XAML 코드

다음 예제에서는 Blend에서 간단한 XAML 디버깅 세션을 안내 합니다.

#### <a name="to-create-a-project"></a>프로젝트를 만들려면

1. Blend에서 **파일** 메뉴를 열고 **새 프로젝트**를 클릭 합니다.

    **새 프로젝트** 대화 상자의 왼쪽에 프로젝트 형식 목록이 표시됩니다. 프로젝트 형식을 클릭하면 해당 프로젝트와 연결된 프로젝트 템플릿이 오른쪽에 표시됩니다.

2. 프로젝트 형식 목록에서 **Windows 유니버설**을 클릭 합니다.

3. 프로젝트 템플릿 목록에서 **비어 있는 앱 (유니버설 Windows)** 을 클릭 합니다.

4. **이름** 텍스트 상자에을 입력 `DebuggingSample` 합니다.

5. **위치** 텍스트 상자에서 프로젝트 위치를 확인합니다.

6. **언어** 목록에서 **Visual C#** 을 클릭한 다음, **확인**을 클릭하여 프로젝트를 만듭니다.

7. 디자인 화면을 마우스 오른쪽 단추로 클릭한 다음, **원본 보기**를 클릭하여 **분할** 보기로 전환합니다.

8. 코드의 오른쪽 상단에 있는 **복사** 링크를 클릭하여 다음 코드를 복사합니다.

   ```xml
   <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
        <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
        <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
   </Grid>
   ```

9. 기본 **그리드**를 찾아 여는 **그리드** 태그와 닫는 태그 사이에 코드를 붙여 넣습니다. 작업을 마치면 코드가 다음과 같이 됩니다.

    ```xml
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">
         <Grid HorizontalAlignment="Left" Height="222" VerticalAlignment="Top>
              <Button content="Button" x:Mame="Home" HorizontalAlignment="Left" VerticalAlignment="Top"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,38,0,0">
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,75,0,0"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="0,112,0,0"/>
              <Button Content="Button" HorizontalAlignment="Left" VerticalAlignment="Top Margin="0,149,0,0"/>
         </Grid>
    </Grid>
    ```

10. **Ctrl** + **Shift** + **B** 를 눌러 프로젝트를 빌드합니다.

    프로젝트를 빌드할 수 없음을 경고하는 오류 메시지가 표시되고, 오류를 나열하는 **결과** 패널이 앱 맨 아래에 나타납니다.

    ![Blend for Visual Studio에서 XAML 디버그](../debugger/media/blend_debugxaml_xaml.png "blend_debugXAML_XAML")

### <a name="resolve-xaml-errors"></a>XAML 오류 해결

XAML 오류가 감지되면 디자인 화면에서 프로젝트에 잘못된 태그가 포함되어 있다는 경고를 표시합니다. 오류를 해결할 때 **결과** 패널의 오류 목록이 업데이트됩니다. 모든 오류를 해결하면 디자인 화면을 사용할 수 있게 되고 앱이 디자인 화면에 표시됩니다.

#### <a name="to-resolve-the-xaml-errors"></a>XAML 오류를 해결하려면

1. 목록에서 첫 번째 오류를 두 번 클릭합니다. 설명은 "값 ' < '은 (는) 특성에서 사용할 수 없습니다."입니다. 오류를 두 번 클릭하면 포인터가 코드에서 해당하는 위치를 찾습니다. `<` 앞의 `Button`은(는) 유효하지만 오류 메시지에서 제시한 대로 특성은 아닙니다. 코드의 이전 줄을 살펴보면 특성 `Top`의 닫는 따옴표가 누락되어 있습니다. 닫는 따옴표를 입력합니다. **결과** 패널의 오류는 변경 내용을 반영하여 업데이트됩니다.

2. "' 0 '은 (는) 이름 시작 부분에서 사용할 수 없습니다." 라는 설명을 두 번 클릭 합니다. `Margin="0,149,0,0"` 올바른 형식으로 표시 됩니다. 그러나 `Margin`의 색 코딩이 해당 코드에서 `Margin`의 다른 인스턴스와 일치하지 않습니다. 이전 이름/값 쌍(`VerticalAlignment="Top`)에 닫는 따옴표가 누락되어 있기 때문에, `Margin="`은 이전 특성 값의 일부분으로 읽고 0은 이름/값 쌍의 시작으로 읽습니다. `Top`의 닫는 따옴표를 입력합니다. **결과** 패널의 오류 목록은 변경 내용을 반영하도록 업데이트됩니다.

3. 나머지 오류 "닫는 XML 태그 '단추'가 일치하지 않습니다."를 두 번 클릭합니다. 포인터는 닫는 **그리드** 태그(`</Grid>`)에 있으므로 오류가 `Grid` 개체 안쪽에 있음을 나타냅니다. 두 번째 `Button` 개체에 닫는 태그가 누락되어 있습니다. 닫는 `/`를 추가한 후 **결과** 패널 목록이 업데이트됩니다. 이러한 초기 오류를 해결했으므로 두 가지의 추가 오류가 식별되었습니다.

4. "멤버 '콘텐츠'를 인식할 수 없거나 액세스할 수 없습니다."를 두 번 클릭합니다. `c`의 `content`는 대문자여야 합니다. 소문자 "c"를 대문자 "c"로 바꿉니다.

5. "' Mame ' 속성이 네임 스페이스에 없습니다."를 두 번 클릭 `http://schemas.microsoft.com/winfx/2006/xaml` 합니다. "Mame"의 "M"은 "N"이어야 합니다. "M"을 "N"으로 바꿉니다. XAML을 구문 분석할 수 있으므로 응용 프로그램이 디자인 화면에 나타납니다.

    ![Blend for Visual Studio에서 XAML 디버깅](../debugger/media/blend_debugartboard_xaml.png "blend_debugArtboard_XAML")

    **Ctrl** + **Shift** + **B** 를 눌러 프로젝트를 빌드하고 나머지 오류가 없는지 확인 합니다.

## <a name="debug-in-visual-studio"></a>Visual Studio에서 디버그

Visual Studio에서 Blend 프로젝트를 열어 앱에서 코드를 보다 쉽게 디버그할 수 있습니다. Visual Studio에서 Blend 프로젝트를 열려면 **프로젝트 패널에서 프로젝트를** 마우스 오른쪽 단추로 클릭 한 다음 **Visual studio에서 편집**을 클릭 합니다. Visual Studio에서 디버깅 세션을 마친 후 Ctrl + Shift + S를 눌러 변경 내용을 모두 저장 한 다음 Blend로 다시 전환 합니다. 프로젝트를 다시 로드할 것인지 묻는 메시지가 나타납니다. **모두 예를** 클릭 하 여 Blend에서 작업을 계속 진행 합니다.

앱을 디버깅 하는 방법에 대 한 자세한 내용은 [Visual Studio에서 UWP 앱 디버그](../debugger/debugging-windows-store-and-windows-universal-apps.md)를 참조 하세요.

## <a name="get-help"></a>도움말 보기

Blend 앱을 디버깅 하는 데 도움이 필요한 경우 [UWP 앱 커뮤니티 포럼](https://social.msdn.microsoft.com/Forums/windowsapps/home?category=windowsapps) 에서 문제와 관련 된 게시물을 검색 하거나 질문을 게시할 수 있습니다.
