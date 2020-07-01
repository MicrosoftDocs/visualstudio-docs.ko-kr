---
title: UWP 앱 새로 고침 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: dd38a758a69b2e19079a2bc2511e7edf5cbfb0ab
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348160"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Visual Studio에서 UWP 앱 새로 고침

 디버그하는 동안 코드를 변경한 다음, **디버그** 도구 모음에서 **Windows 앱 새로 고침** 단추를 선택하여 JavaScript를 사용하여 UWP 앱을 새로 고칠 수 있습니다. 이 단추를 선택하면 디버거를 중지하여 다시 시작하지 않고 응용 프로그램을 다시 로드합니다. 새로 고침 기능을 사용하면 HTML, CSS 및 JavaScript 코드를 수정하고 결과를 빠르게 확인할 수 있습니다. 이 기능은 UWP 앱에서 지원됩니다.

 새로 고침을 수행하면 응용 프로그램 상태가 유지되지 않으며 응용 프로그램에 다음 변경 사항이 반영됩니다.

- 패키지 매니페스트에서 지정한 이미지에 대한 변경을 포함하는 패키지 매니페스트 파일 변경.

- SDK 참조 추가 또는 제거와 같은 참조 변경 또는 Windows 런타임 구성 요소에 대한 변경(.winmd 파일).

- .resjson 파일의 문자열에 대한 변경과 같은 리소스 변경.

- 경로 이름 변경, 새 프로젝트 파일 또는 삭제된 파일이 발생되는 프로젝트 파일 변경.

- 선택한 디버깅 디바이스에 대한 변경 또는 파일의 패키지 작업(속성 창)에 대한 변경과 같은 프로젝트 및 항목 속성 변경.

> [!IMPORTANT]
> 참조 또는 패키지 매니페스트를 변경하거나 앞의 목록에 지정된 기타 변경 사항을 수행한 경우, 디버거를 중지했다가 다시 시작해야 HTML, CSS 및 JavaScript 소스 파일이 업데이트됩니다.

### <a name="to-refresh-an-app"></a>응용 프로그램을 새로 고치려면

1. Visual Studio에서 UWP 프로젝트를 열고 디버그 대상으로 **로컬 머신**을 선택합니다.

     ![디버그 대상 목록 선택](../debugger/media/js_select_target.png "JS_Select_Target")

3. F5 키를 눌러 디버그 모드에서 응용 프로그램을 실행합니다.

4. Visual Studio로

5. UWP 앱의 홈페이지에서 HTML의 일부를 편집합니다.

7. 다음과 같이 표시되는 **Windows 앱 새로 고침** 단추를 클릭합니다. ![Windows 앱 새로 고침 단추](../debugger/media/js_refresh.png "JS_Refresh"). 또는 F4 키를 누릅니다.

8. 응용 프로그램으로 전환합니다. 앱이 다시 로드되고 업데이트된 HTML은 앱을 렌더링하는 데 사용됩니다.

## <a name="see-also"></a>참조
- [빠른 시작: HTML 및 CSS 디버그](../debugger/quickstart-debug-html-and-css.md)