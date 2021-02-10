---
title: 레지스터 그룹 표시 및 숨기기 | Microsoft Docs
description: 주소 수준 디버깅을 사용하는 경우에 사용할 수 있는 레지스터 창은 레지스터를 그룹으로 구성합니다. 표시되는 그룹을 설정하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.registergroups
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, displaying and hiding register groups
- register groups, displaying and hiding
ms.assetid: 6be5dfb4-4cfe-4daf-b538-60405640857d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dee270bc4c4f9417bdf412974a12d687635e312f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899275"
---
# <a name="how-to-display-and-hide-register-groups-c-c-visual-basic-f"></a>방법: 레지스터 그룹 표시 및 숨기기(C#, C++, Visual Basic, F#)

**레지스터** 창은 **옵션** 대화 상자, **디버깅** 노드, **일반** 범주에서 주소 수준 디버깅을 설정한 경우에만 사용할 수 있습니다.

**레지스터** 창에서는 레지스터를 그룹으로 구성하여 간단하게 표시합니다. **레지스터** 창을 마우스 오른쪽 단추로 클릭하면 레지스터 그룹을 포함하는 바로 가기 메뉴가 나타나며, 아래의 절차에 따라 레지스터 그룹을 표시하거나 숨길 수 있습니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [재설정 설정](../ide/environment-settings.md#reset-settings)을 참조하세요.

## <a name="display-or-hide-register-groups"></a>레지스터 그룹 표시 또는 숨기기

1. **레지스터** 창을 마우스 오른쪽 단추로 클릭합니다.

2. 바로 가기 메뉴에서 표시하거나 숨기려는 레지스터 그룹을 선택합니다.

     디버깅하고 있는 하드웨어에서 지원하지 않는 레지스터 그룹은 바로 가기 메뉴에서 비활성화되므로 선택할 수 없습니다.

## <a name="see-also"></a>참조

- [방법: 레지스터 창 사용](../debugger/how-to-use-the-registers-window.md)