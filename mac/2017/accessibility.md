---
title: 액세스 가능성
description: 이 문서에서는 Mac용 Visual Studio의 액세스 가능성 기능과 사용하도록 설정하는 방법을 소개합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.topic: overview
ms.openlocfilehash: a2f151cbf593d2b8e26be7ac60eaf8ff3c687499
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85938927"
---
# <a name="accessibility"></a>액세스 가능성

macOS의 기능 및 유틸리티 외에도, Mac용 Visual Studio에는 다음과 같은 기능이 포함되어 있어서 장애가 있는 사용자도 더욱 쉽게 액세스할 수 있습니다.

- Solution Pad 및 Editor Pad의 텍스트 확대
- 편집기의 텍스트 크기 옵션
- 편집기의 색 사용자 지정
- 바로 가기 키 사용자 지정
- 메서드 및 매개 변수의 코드 완성

macOS의 내게 필요한 옵션 기능에 대한 자세한 내용은 [Apple 웹 사이트](https://www.apple.com/accessibility/mac/)를 참조하세요.

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Mac용 Visual Studio의 내게 필요한 옵션 기능 사용

Mac용 Visual Studio의 내게 필요한 옵션 기능은 기본적으로 꺼져 있습니다. 이 기능을 사용하도록 설정하려면 다음 단계를 수행합니다.

1. **Visual Studio > 기본 설정 > 기타 > 내게 필요한 옵션**으로 이동합니다.

2. 다음 그림과 같이 **내게 필요한 옵션 사용** 확인란을 선택합니다.

    ![내게 필요한 옵션 사용 확인란](media/accessibility-image1.png)

3. **Visual Studio 다시 시작** 단추를 눌러 내게 필요한 옵션 기능이 적용되도록 합니다.

또는 명령줄을 사용하여 내게 필요한 옵션 기능을 사용하도록 설정할 수도 있습니다. 이를 위해서는 터미널에 다음 명령을 입력합니다.

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

내게 필요한 옵션 기능을 켠 후 Visual Studio를 다시 시작해야 합니다.

## <a name="how-to-use-keyboard-navigation"></a>방법: 키보드 탐색 사용

**시스템 기본 설정 > 키보드 > 바로 가기**에서 전체 키보드 액세스 옵션을 **모든 컨트롤**로 설정하여 키보드 탐색을 사용하도록 설정할 수 있습니다.

![macOS의 시스템 기본 설정 패널](media/accessibility-image2.png)

전체 키보드 액세스를 설정하면 포커스 사각형이 켜집니다. 그런 후 다음을 사용하여 컨트롤을 선택할 수 있습니다.

- Tab 키: 컨트롤을 따라 앞으로 이동
- Shift+Tab: 컨트롤을 따라 뒤로 이동
- 화살표 키: 화살표 방향으로 컨트롤 간 이동

스페이스바를 누르면 포커스가 있는 컨트롤이 활성화됩니다.

## <a name="how-to-enable-and-use-voice-over"></a>방법: Voice Over 설정 및 사용

VoiceOver를 켜거나 끄려면 **Cmd+F5**를 누릅니다.

UI VoiceOver 명령을 탐색하려면 다음 명령을 사용합니다.

- 컨트롤 간에 VoiceOver 커서를 이동합니다. **Ctrl + Alt + 왼쪽 화살표 키 / 오른쪽 화살표 키**

   VoiceOver는 컨트롤의 이름, 일부 세부 정보 및 사용자가 해당 컨트롤로 수행할 수 있는 작업을 읽어줍니다.

- 그룹 및 컨트롤 입력(예: Solution Pad, 도구 상자 및 기타 패드): **Ctrl + Alt + Shift + 아래쪽 화살표**

   컨트롤 안에 있을 때 **Ctrl+Alt+화살표 키**를 사용하여 컨트롤 내부를 이동할 수 있습니다.

macOS에서의 VoiceOver 사용에 대한 일반적인 내용은 다음 설명서를 참조하세요.

- [VoiceOver 시작](https://help.apple.com/voiceover/info/guide/10.12/)
- [macOS의 VoiceOver 명령](https://lab.dotjay.com/notes/voiceover-commands/)

## <a name="see-also"></a>참조

- [Visual Studio의 액세스 가능성 기능(Windows에서)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)