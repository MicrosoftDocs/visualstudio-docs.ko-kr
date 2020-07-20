---
title: Just-In-Time 디버거를 사용하지 않도록 설정 | Microsoft Docs
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3155c2cdc9ea3dc5208a52e5fe37f697a4ad5ef6
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386123"
---
# <a name="disable-the-just-in-time-debugger"></a>Just-In-Time 디버거를 사용하지 않도록 설정

실행 중인 앱에서 오류가 발생하고 앱을 계속할 수 없는 경우 Just-In-Time 디버거 대화 상자가 열릴 수 있습니다.

Just-In-Time 디버거를 사용하면 Visual Studio를 시작하여 오류를 디버그할 수 있습니다. 오류에 대한 자세한 정보를 보거나 오류를 디버그하려면 Visual Studio 또는 다른 선택한 디버거가 설치되어 있어야 합니다.

이미 Visual Studio 사용자이고 오류를 디버그하려면 [Just-In-Time 디버거를 사용하여 디버그](../debugger/debug-using-the-just-in-time-debugger.md)를 참조하세요. 오류를 해결할 수 없거나 Just-In-Time 디버거가 열리지 않도록 하려면 [Visual Studio에서 Just-In-Time 디버깅을 사용하지 않도록 설정](debug-using-the-just-in-time-debugger.md#BKMK_Enabling)할 수 있습니다.

Visual Studio를 설치했지만 더 이상 설치하지 않을 경우 [Windows 레지스트리에서 Just-In-Time 디버깅을 사용하지 않도록 설정](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry)해야 할 수 있습니다.

Visual Studio가 설치되어 있지 않으면 스크립트 디버깅 또는 서버 쪽 디버깅을 사용하지 않도록 설정하여 Just-In-Time 디버깅을 방지할 수 있습니다.

- 웹앱을 실행하려면 스크립트 디버깅을 사용하지 않도록 설정합니다.

  Windows **제어판** > **네트워크 및 인터넷** > **인터넷 옵션**에서 **스크립트 디버깅 사용 안 함(Internet Explorer)** 및 **스크립트 디버깅 사용 안 함(기타)** 을 선택합니다. 정확한 단계와 설정은 Windows 버전 및 브라우저에 따라 달라집니다.

  ![JIT 인터넷 옵션](../debugger/media/jitinternetoptions.png "JIT 인터넷 옵션")

- IIS에서 ASP.NET 웹앱을 호스트하는 경우 서버 쪽 디버깅을 사용하지 않도록 설정합니다.

  1. IIS 관리자 **기능 보기**의 **ASP.NET** 섹션에서 **.NET 컴파일**을 두 번 클릭하거나 선택한 다음, **작업** 창에서 **기능 열기**를 선택합니다.
  1. **동작** > **디버그**에서 **False**를 선택합니다. 이전 버전의 IIS에서는 단계가 다릅니다.

Just-In-Time 디버깅을 사용하지 않도록 설정한 이후에 앱에서 오류를 처리하고 정상적으로 실행할 수 있습니다.

앱에 아직 처리되지 않은 오류가 있으면 오류 메시지가 표시되거나, 앱에서 크래시 또는 응답 중지 현상이 발생할 수 있습니다. 오류가 해결될 때까지 앱이 정상적으로 실행되지 않습니다. 앱 소유자에게 연락하여 문제를 해결하도록 요청할 수 있습니다.
