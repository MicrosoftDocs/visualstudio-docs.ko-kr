---
title: 디버거에서 레지스터 값 보기 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: afcada407060af2072e3cf1c30e86153762890b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906003"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>레지스터 창에서 레지스터 값 보기(C#, C++, Visual Basic, F#)

**레지스터** 창에는 Visual Studio 디버깅 동안의 레지스터 콘텐츠가 표시됩니다. 레지스터의 개념 및 **레지스터** 창에 대한 간략한 소개는 [디버깅 기본 사항을 참조하세요. 레지스터 창](../debugger/debugging-basics-registers-window.md)

> [!NOTE]
> 스크립트나 SQL 앱의 경우에는 레지스터 정보를 사용할 수 없습니다.

디버깅 중에는 앱에서 코드가 실행될 때 레지스터 값이 변경됩니다. 최근에 변경된 값은 **레지스터** 창에 빨간색으로 표시됩니다.

**레지스터** 창에서는 레지스터를 플랫폼 및 프로세서 유형에 따라 각각 다른 그룹으로 구성하여 간단하게 표시합니다. 레지스터 그룹은 표시하거나 숨길 수 있습니다. 자세한 내용은 [방법: 레지스터 그룹 표시 및 숨기기](../debugger/how-to-display-and-hide-register-groups.md)를 참조하세요.

**레지스터** 창에 표시되는 플래그에 대한 자세한 내용은 [레지스터 창 정보](../debugger/debugging-basics-registers-window.md)를 참조하세요.

레지스터 값은 편집할 수 있습니다. 자세한 내용은 [방법: 레지스터 값 편집](../debugger/how-to-edit-a-register-value.md)을 참조하세요.

**레지스터 창을 열려면**

1. **도구**(또는 **디버그**) > **옵션** > **디버깅**에서 **주소 수준 디버깅 사용**을 선택하여 주소 수준 디버깅을 사용하도록 설정합니다.

1. 디버깅이 실행되는 동안 또는 중단점에서 **디버그** > **Windows** > **레지스터**를 선택하거나 **Alt**+**5**를 누릅니다.

>[!NOTE]
>대화 상자와 메뉴 명령은 Visual Studio 버전 또는 설정에 따라 다를 수도 있습니다. 설정을 변경하려면 Visual Studio **도구** 메뉴에서 **가져오기 및 내보내기 설정**을 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

### <a name="see-also"></a>참조

- [디버깅 기본 사항: 레지스터 창](../debugger/debugging-basics-registers-window.md)
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
