---
title: 메서드 빠른 작업에 매개 변수 추가
description: 빠른 작업으로 사용량에 따라 매개 변수를 메서드에 자동으로 추가하고 선언하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c2582228426afcefdb2587d646a8668f622309c6
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871303"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>빠른 작업을 사용하여 메서드에 매개 변수 추가

이 코드 생성은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 사용법을 기준으로 메서드에 매개 변수를 자동으로 추가할 수 있습니다.

**시기:** 메서드에 매개 변수를 추가해야 하며, 자동으로 메서드를 제대로 선언하려고 합니다.

**이유:** 호출 전에 메서드 선언에 매개 변수를 추가할 수 있지만, 이 기능은 메서드 호출을 기준으로 자동으로 추가합니다.

## <a name="how-to-use-it"></a>사용 방법

1. 메서드 호출에 여분의 인수를 추가합니다.

   빨간색의 오류 표시선이 호출하는 메서드의 이름 아래에 나타납니다.

2. 빠른 작업 메뉴가 나타날 때까지 빨간색 오류 표시선을 포인터로 가리킵니다. 빠른 작업 메뉴에서 **아래쪽 화살표** 를 선택하고 **[메서드]에 매개 변수 추가** 를 선택합니다.

   ![Visual Studio의 메서드에 매개 변수 추가 빠른 작업](media/add-parameter-to-method.png)

   > [!TIP]
   > 메서드 호출 줄에 커서를 놓은 다음, **Ctrl**+ **.** 을 누르거나, (마침표) 파일 여백에 있는 전구 아이콘을 선택하여 빠른 작업 메뉴에 액세스할 수도 있습니다.

   Visual Studio에서 메서드 선언에 새 매개 변수를 추가합니다.

> [!NOTE]
> 메서드에 대한 다른 호출이 있는 경우, 새로 추가된 매개 변수에 대한 인수를 지정하지 않기 때문에 이 빠른 작업을 사용한 후 오류가 발생할 수 있습니다.

## <a name="see-also"></a>추가 정보

- [생성자에 매개 변수 추가](generate-constructor.md#addparameter)
