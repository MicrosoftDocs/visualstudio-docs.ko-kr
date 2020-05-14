---
title: 문자열 길이 제한 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df6e068ba612d5e8876e4fa01fbc0751759d5a80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701483"
---
# <a name="restrictions-on-string-lengths"></a>문자열 길이 제한
소스 제어 플러그인 API는 다양한 함수에 사용되는 문자열의 길이를 제한합니다.

## <a name="string-length-values"></a>문자열 길이 값

|상수|값|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> 길이는 종료를 포함하지 `null`않습니다. "_LEN" 대신 "_SIZE" 접미사가 있는 다른 상수에는 종료를 `null`위한 공간이 포함됩니다.

|상수|값|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>참조
- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md)
