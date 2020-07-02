---
title: XAML 오류 및 경고
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b740f0882edb2eae9f00bd7826543e7fe1b4597f
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817270"
---
# <a name="xaml-errors-and-warnings"></a>XAML 오류 및 경고

XAML을 작성하면 Visual Studio에서는 입력한 코드를 분석합니다. 오류가 검색되면 오류 표시선이 코드 줄에 나타납니다. 하지만 오류 표시선 위로 마우스를 가져가면 오류 또는 경고에 대한 자세한 정보를 제공합니다. 일부 오류 및 경고의 경우 빠른 작업 전구가 표시 되 고 **Ctrl**를 사용 합니다 + **.** 바로 가기 키는 문제를 해결하는 옵션을 표시합니다.

## <a name="error-types"></a>오류 유형

내부적으로 여러 도구는 병렬로 XAML을 분석합니다. XAML 오류는 오류를 검색하는 도구에 따라 다음 세 가지 형식 중 하나로 분류됩니다.

|**검색된 오류 기준**|**오류 코드 형식**|
| - |-----------------|
|XAML 언어 서비스(XAML 편집기)|XLSxxxx|
|XAML 디자이너|XDGxxxx|
|XAML 편집하며 계속하기|XECxxxx|

> [!Note]
> 일부 오류 또는 경고에는 해당 코드가 포함됩니다. 이러한 오류는 일반적으로 XAML 디자이너 오류입니다.

## <a name="suppress-xaml-designer-errors"></a>XAML 디자이너 오류 표시 안 함

**도구 > 옵션**을 선택하여 **옵션** 대화 상자를 연 다음, **텍스트 편집기 > XAML > 기타**를 선택합니다.

**XAML 디자이너에 의해 검색된 오류 표시** 확인란의 선택을 취소합니다.

![XAML 디자이너 오류 표시 안 함](media/suppress_xaml_designer_errors.png)
