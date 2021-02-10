---
title: 중단점이 적중될 때 대화 상자 | Microsoft Docs
description: 중단점이 적중될 때를 사용하여 중단 시 작업을 지정합니다. 메시지를 인쇄하고 이후 실행을 계속하도록 지정할 수 있습니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bfb5099bd0fab17cd983af4e16a435fd192a1668
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883872"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>중단점이 적중될 때 대화 상자
이 대화 상자에서는 중단점이 적중될 때 발생하는 작업을 사용자 지정할 수 있습니다.

## <a name="uielement-list"></a>UI 요소 목록
 **메시지 인쇄** DebuggerDisplay 구문을 사용하여 메시지를 인쇄합니다. 자세한 내용은 [DebuggerDisplay 특성 사용](../debugger/using-the-debuggerdisplay-attribute.md)을 참조하세요.

 이 텍스트 상자는 자체적으로 또는 DebuggerDisplay 식의 중괄호 안에 사용할 수 있는 특수 키워드(예: $ADDRESS)도 지원합니다. 사용 가능한 키워드는 대화 상자에 나열됩니다.

 **계속 실행** 이 컨트롤은 **메시지 인쇄** 를 선택한 경우에만 사용할 수 있습니다. 이 컨트롤을 선택하면 위치 적중 시 중단하는 방법 대신 중단점을 추적점으로 사용하여 프로그램 실행을 추적할 수 있습니다.

## <a name="see-also"></a>참조
- [중단점 사용](../debugger/using-breakpoints.md)
- [DebuggerDisplay 특성 사용](../debugger/using-the-debuggerdisplay-attribute.md)