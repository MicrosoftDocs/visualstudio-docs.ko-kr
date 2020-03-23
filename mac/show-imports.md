---
title: 가져오기 항목 표시
description: 가져오기 항목 표시를 사용하여 Mac용 Visual Studio에서 IntelliSense를 확장합니다.
author: cobey
ms.author: cobey
ms.date: 03/29/2019
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.custom: video
ms.openlocfilehash: 964fbbf2f46e2495184b01c47cba888a93f24ea8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75439105"
---
# <a name="show-import-items"></a>가져오기 항목 표시

프로젝트에 가져오지 않은 경우에도 Mac용 Visual Studio가 IntelliSense 완성 목록에 사용 가능한 모든 형식을 표시할 수 있습니다. 가져오지 않은 항목을 선택하면 올바른 `using` 문이 소스 파일에 추가됩니다.

![가져오기 항목 표시 개요](media/importitems-overview.gif)

## <a name="how-to-enable"></a>사용 방법

이 기능을 사용하려면 **Visual Studio** > **기본 설정**을 통해 **기본 설정**을 열고 **텍스트 편집기** > **IntelliSense**로 이동합니다. **가져오기 항목 표시** 상자를 선택하여 IntelliSense에서 추가 항목을 사용하도록 설정합니다.

![가져오기 항목 표시 옵션](media/show-import-items.png)

## <a name="usage"></a>사용법

**가져오기 항목 표시**를 사용하도록 설정하면 이 기능을 사용하여 항목을 가져오는 프로세스가 IntelliSense 내의 일반적인 작업과 유사합니다. 코드를 입력할 때 유효한 항목이 완성 목록에 채워집니다. 여기에는 아직 가져오지 않은 항목이 포함됩니다. 가져오지 않은 항목의 전체 네임스페이스는 항목의 오른쪽에 표시되므로 프로젝트에 끌어오는 가져오기를 확인할 수 있습니다.

![가져오기 항목 표시 목록](media/show-import-items-list.png)

IntelliSense 목록에서 네임스페이스는 현재 `using` 문에서 참조하지 않는 멤버 옆에 표시됩니다. 목록에서 이러한 항목 중 하나를 선택하면 코드에 멤버가 추가됩니다. _그리고_ `using` 문이 파일 맨 위에 추가됩니다. 코드에서 이미 참조된 형식의 멤버는 IntelliSense에 해당 네임스페이스가 표시되지 않습니다.

## <a name="see-also"></a>참조

- [빠른 작업(Windows의 Visual Studio)](/visualstudio/ide/quick-actions)
- [코드 리팩터링(Windows의 Visual Studio)](/visualstudio/ide/refactoring-in-visual-studio)
