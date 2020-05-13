---
title: 웹 브라우저 표시 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8c97659cc6036433c5bcf2547a9f88aee56f451
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747722"
---
# <a name="showwebbrowser-command"></a>웹 브라우저 표시 명령

IDE(통합 개발 환경) 내부 또는 외부의 웹 브라우저 창에서 지정하는 URL을 표시합니다.

## <a name="syntax"></a>구문

```cmd
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>인수
`URL`

필수 사항입니다. 웹 사이트의 URL(Uniform Resource Locator)입니다.

## <a name="switches"></a>스위치
/new

(선택 사항) 웹 브라우저의 새 인스턴스에 페이지가 표시되도록 지정합니다.

/ext

(선택 사항) IDE 외부의 기본 웹 브라우저에 페이지가 표시되도록 지정합니다.

## <a name="remarks"></a>설명
**ShowWebBrowser** 명령의 별칭은 **navigate** 또는 **nav**입니다.

## <a name="example"></a>예제
다음 예제에서는 IDE 외부의 웹 브라우저에서 Microsoft Docs 홈페이지를 표시합니다. 웹 브라우저의 인스턴스가 이미 열린 경우 이 인스턴스가 사용되고, 그렇지 않으면 새 인스턴스가 시작됩니다.

```cmd
>View.ShowWebBrowser https://docs.microsoft.com /ext
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)