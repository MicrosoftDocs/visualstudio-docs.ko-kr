---
title: 문자열 길이에 대 한 제한 사항 | Microsoft Docs
description: 소스 제어 플러그 인 API에 의해 적용 되는 다양 한 함수에 사용 되는 문자열의 길이에 대 한 제한에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b7526494f5d64f7e02e63e5ec3012297af730e87
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068416"
---
# <a name="restrictions-on-string-lengths"></a>문자열 길이에 대 한 제한 사항
소스 제어 플러그 인 API는 다양 한 함수에 사용 되는 문자열의 길이를 제한 합니다.

## <a name="string-length-values"></a>문자열 길이 값

|상수|값|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> 길이는 종료를 포함 하지 않습니다 `null` . "_LEN" 대신 "_SIZE" 접미사가 있는 다른 상수에는 종료를 위한 공간이 포함 됩니다 `null` .

|상수|값|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>참조
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
