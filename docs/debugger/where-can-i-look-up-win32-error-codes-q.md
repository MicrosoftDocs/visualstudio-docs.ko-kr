---
title: Win32 오류 코드를 어디에서 찾을 수 있습니까? | Microsoft 문서
description: Win32 오류 코드를 조회하려면 조사식 또는 간략한 조사식에 입력합니다. 예를 들면 “0x80000004,hr”입니다. 오류 코드 정의는 INCLUDE\WINERROR.H에 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44a006be3b6ecad3ef723c00154354cb35df0049
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149289"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Win32 오류 코드를 어디에서 찾을 수 있습니까?
기본 시스템 설치의 INCLUDE 디렉터리에 있는 WINERROR.H에는 Win32 API 함수에 대한 오류 코드 정의가 포함되어 있습니다.

 **조사식** 창이나 **간략한 조사식** 대화 상자에 코드를 입력하면 오류 코드를 찾을 수 있습니다. 예를 들어:

`0x80000004,hr`

## <a name="see-also"></a>참조
- [네이티브 코드 디버그 FAQ](../debugger/debugging-native-code-faqs.md)
- [네이티브 코드 디버그](../debugger/debugging-native-code.md)