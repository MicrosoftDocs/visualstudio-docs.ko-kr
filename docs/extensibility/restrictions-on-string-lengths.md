---
title: 문자열 길이에 대 한 제한 사항 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80701483"
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

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
