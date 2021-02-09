---
title: XAML 오류 및 경고
description: 오류를 범주화 하는 방법, 오류 정보를 가져오는 방법 및 문제를 해결 하기 위한 옵션을 찾는 방법을 비롯 하 여 Visual Studio의 XAML 오류 및 경고에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e33cdc11eb5531fd2325bd90912dc22a105711c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903646"
---
# <a name="xaml-errors-and-warnings"></a>XAML 오류 및 경고

XAML을 작성하면 Visual Studio에서는 입력한 코드를 분석합니다. 오류가 검색되면 오류 표시선이 코드 줄에 나타납니다. 하지만 오류 표시선 위로 마우스를 가져가면 오류 또는 경고에 대한 자세한 정보를 제공합니다. 일부 오류 및 경고의 경우 빠른 작업 전구가 표시 되 고 **Ctrl** 를 사용 합니다 + **.** 바로 가기 키는 문제를 해결하는 옵션을 표시합니다.

## <a name="error-types"></a>오류 유형

내부적으로 여러 도구는 병렬로 XAML을 분석합니다. XAML 오류는 오류를 검색하는 도구에 따라 다음 세 가지 형식 중 하나로 분류됩니다.

|**검색된 오류 기준**|**오류 코드 형식**|**Visual Studio 버전**|
| - |-----------------| - |
|XAML 언어 서비스(XAML 편집기)|XLSxxxx| 모든 버전 |
|XAML 디자이너|XDGxxxx| 모든 버전 | 
|XAML 편집하며 계속하기|XECxxxx| Visual Studio 2019 버전 16.1 이전 |
|XAML 핫 다시 로드 | XHRxxxx | Visual Studio 2019 버전 16.2 이상 |

Xaml 편집 &의 브랜드에 대 한 자세한 내용은 xaml 핫 다시 로드로 계속 하려면 [릴리스 정보](/visualstudio/releases/2019/release-notes-v16.2#wpfuwp-tooling) 를 참조 하세요.

> [!Note]
> 일부 오류 또는 경고에는 해당 코드가 포함됩니다. 이러한 오류는 일반적으로 XAML 디자이너 오류입니다.

## <a name="suppress-xaml-designer-errors"></a>XAML 디자이너 오류 표시 안 함

**도구 > 옵션** 을 선택하여 **옵션** 대화 상자를 연 다음, **텍스트 편집기 > XAML > 기타** 를 선택합니다.

**XAML 디자이너에 의해 검색된 오류 표시** 확인란의 선택을 취소합니다.

![XAML 디자이너 오류 표시 안 함](media/suppress_xaml_designer_errors.png)