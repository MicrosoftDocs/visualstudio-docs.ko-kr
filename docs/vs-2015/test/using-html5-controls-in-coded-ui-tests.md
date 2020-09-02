---
title: 코딩된 UI 테스트에서 HTML5 컨트롤 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 2000b214-ae92-4334-b549-aa0eb4f45fe1
caps.latest.revision: 19
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 029b547102863f4798ad261deb678c4d98596916
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657199"
---
# <a name="using-html5-controls-in-coded-ui-tests"></a>코딩된 UI 테스트에서 HTML5 컨트롤 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코딩된 UI 테스트에는 Internet Explorer 9 및 Internet Explorer 10에 포함된 일부 HTML5 컨트롤에 대한 지원이 포함됩니다.

 **요구 사항**

- Visual Studio Enterprise

> [!WARNING]
> Internet Explorer 10 이전 버전에서는 Internet Explorer 프로세스의 권한에 비해 더 높은 권한 수준으로 코딩된 UI 테스트를 실행할 수 있었습니다. Internet Explorer 10에서 코딩된 UI 테스트를 실행하는 경우 코딩된 UI 테스트와 Internet Explorer 프로세스가 모두 같은 권한 수준에 있어야 합니다. 이는 Internet Explorer 10의 더 안전한 AppContainer 기능 때문입니다.

> [!WARNING]
> Internet Explorer 10에서 코딩된 UI 테스트를 만드는 경우 Internet Explorer 9 또는 Internet Explorer 8을 사용하여 실행하지 못할 수 있습니다. Internet Explorer 10에는 오디오, 비디오, 진행률 표시줄 및 슬라이더와 같은 HTML5 컨트롤이 포함되기 때문입니다. 이러한 HTML5 컨트롤은 Internet Explorer 9 또는 Internet Explorer 8로 인식되지 않습니다. 마찬가지로, Internet Explorer 9를 사용하여 코딩된 UI 테스트는 Internet Explorer 8에서 인식되지 않는 일부 HTML5 컨트롤을 포함할 수 있습니다.

## <a name="supported-html5-controls"></a>지원되는 HTML5 컨트롤
 코딩된 UI 테스트에는 다음 HTML5 컨트롤의 기록, 재생 및 유효성 검사에 대한 지원이 포함됩니다.

- [오디오 컨트롤](#audio-control)

- [비디오 컨트롤](#video-control)

- [슬라이더](#slider)

- [ProgressBar](#progressbar)

### <a name="audio-control"></a>오디오 컨트롤
 **오디오 컨트롤:** HTML5 오디오 컨트롤에 대한 작업은 올바르게 기록되고 재생됩니다.

 ![HTML5 오디오 컨트롤](../test/media/codedui-html5-audio.png)

|작업|기록 중|생성된 코드|
|------------|---------------|--------------------|
|**오디오 재생**<br /><br /> 컨트롤 또는 컨트롤 상황에 맞는 메뉴에서 직접|00:00:00에서 \<name> 오디오 재생|HtmlAudio.Play(TimeSpan)|
|**오디오의 특정 시간까지 검색**|00:01:48까지 \<name> 오디오 검색|HtmlAudio.Seek(TimeSpan)|
|**오디오 일시 중지**<br /><br /> 컨트롤 또는 컨트롤 상황에 맞는 메뉴에서 직접|00:01:53에서 \<name>오디오 일시 중지|HtmlAudio.Pause(TimeSpan)|
|**오디오 음소거**<br /><br /> 컨트롤 또는 컨트롤 상황에 맞는 메뉴에서 직접|\<name> 오디오 음소거|HtmlAudio.Mute()|
|**오디오 음소거 해제**<br /><br /> 컨트롤 또는 컨트롤 상황에 맞는 메뉴에서 직접|\<name> 오디오 음소거 해제|HtmlAudio.Unmute()|
|**오디오 볼륨 변경**|\<name> 오디오 볼륨을 79%로 설정|HtmlAudio.SetVolume(float)|

 다음과 같은 속성을 HtmlAudio에 사용할 수 있으며 모든 속성에 어설션을 추가할 수 있습니다.

```
string AutoPlay
string Controls
string CurrentSrc
string CurrentTime
string CurrentTimeAsString
string Duration
string DurationAsString
string Ended
string Loop
string Muted
string Paused
string PlaybackRate
string ReadyState
string Seeking
string Src
string Volume
```

 **검색 속성:** `HtmlAudio`에 대한 검색 속성은 `Id`, `Name` 및 `Title`입니다.

 **필터 속성:** `HtmlAudio`에 대한 검색 속성은 `Src`, `Class`, `ControlDefinition` 및 `TagInstance`입니다.

> [!NOTE]
> 검색 및 일시 중지에 대한 시간은 중요할 수 있습니다. 재생하는 동안 코딩된 UI 테스트는 `(TimeSpan)`에 지정된 시간까지 기다린 후 오디오를 일시 중지합니다. 특수한 경우 일시 중지 명령을 누르기 전에 지정된 시간이 경과하면 예외가 throw됩니다.

### <a name="video-control"></a>비디오 컨트롤
 **비디오 컨트롤:** HTML5 비디오 컨트롤에 대한 작업은 올바르게 기록되고 재생됩니다.

 ![HTML5 비디오 컨트롤](../test/media/codedui-html5-video.png)

|작업|기록 중|생성된 코드|
|------------|---------------|--------------------|
|**비디오 재생**<br /><br /> 컨트롤 또는 컨트롤 상황에 맞는 메뉴에서 직접|00:00:00에서 \<name> 비디오 재생|HtmlVideo.Play(TimeSpan)|
|**비디오의 특정 시간까지 검색**|00:01:48까지 \<name> 비디오 검색|HtmlVideo.Seek(TimeSpan)|
|**비디오 일시 중지**<br /><br /> 컨트롤 또는 컨트롤 상황에 맞는 메뉴에서 직접|00:01:53에서 \<name>비디오 일시 중지|HtmlVideo.Pause(TimeSpan)|
|**비디오 음소거**<br /><br /> 컨트롤 또는 컨트롤 상황에 맞는 메뉴에서 직접|\<name> 비디오 음소거|HtmlVideo.Mute()|
|**비디오 음소거 해제**<br /><br /> 컨트롤 또는 컨트롤 상황에 맞는 메뉴에서 직접|\<name> 비디오 음소거 해제|HtmlVideo.Unmute()|
|**비디오의 볼륨 변경**|\<name> 비디오 볼륨을 79%로 설정||

 HtmlAudio의 모든 속성을 HtmlVideo에 사용할 수 있습니다. 다음 세가지 속성도 사용할 수 있습니다. 어설션은 모든 속성에 추가할 수 있습니다.

```
string Poster
string VideoHeight
string VideoWidth

```

 **검색 속성:** `HtmlVideo`에 대한 검색 속성은 `Id`, `Name` 및 `Title`입니다.

 **필터 속성:** `HtmlVideo`에 대한 검색 속성은 `Src`, `Poster`, `Class`, `ControlDefinition` 및 `TagInstance`입니다.

> [!NOTE]
> -30s 또는 +30s 레이블을 사용하여 비디오를 되감거나 빨리 감으면 적절한 시간까지 검색하도록 집계됩니다.

### <a name="slider"></a>슬라이더
 **슬라이더 컨트롤:** HTML5 슬라이더 컨트롤에 대한 작업은 올바르게 기록되고 재생됩니다.

 ![HTML5 슬라이더 컨트롤](../test/media/codedui-html5-slider.png)

|작업|기록 중|생성된 코드|
|------------|---------------|--------------------|
|**슬라이더의 위치 설정**|\<x>슬라이더에서 위치 설정 \<name>|HtmlSlider. 값 =\<x>|

 다음과 같은 속성을 HtmlSlider에 사용할 수 있으며 모든 속성에 어설션을 추가할 수 있습니다.

```
string Disabled
string Max
string Min
string Required
string Step
string ValueAsNumber
```

### <a name="progressbar"></a>ProgressBar
 **ProgressBar 컨트롤:** ProgressBar는 상호 작용할 수 없는 컨트롤입니다. 이 컨트롤의 `Value` 및 `Max` 속성에 어설션을 추가할 수 있습니다.

 ![HTML5 ProgressBar 컨트롤](../test/media/codedui-html5-progressbar.png)

## <a name="see-also"></a>참조

- [HTML 요소](https://www.w3schools.com/HTML/html_elements.asp)
- [UI 자동화를 사용 하 여 코드 테스트](../test/use-ui-automation-to-test-your-code.md)
- [코딩 된 UI 테스트 만들기](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [코딩된 UI 테스트 사용자 지정](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeCUITModify)
- [코딩 된 UI 테스트 및 작업 기록에 지원 되는 구성 및 플랫폼](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
