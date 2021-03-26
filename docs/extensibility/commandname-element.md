---
title: CommandName 요소 | Microsoft Docs
description: CommandName 요소는 옵션 대화 상자의 키보드 범주에 표시 되는 텍스트와 사용자 지정 대화 상자의 명령 목록에 표시 되는 텍스트를 지정 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommandName element (VSCT XML schema)
- VSCT XML schema elements, CommandName
ms.assetid: a338b767-aa7e-4536-9908-e19a50ab60ac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ba74c0a61ddf01407f2af6ebb8053e2f1e4fe6ac
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089630"
---
# <a name="commandname-element"></a>CommandName 요소
`CommandName`요소는 **옵션** 대화 상자의 키보드 범주에 표시 되는 텍스트와 **사용자 지정** 대화 상자의 **명령** 목록에 표시 되는 텍스트를 지정 합니다.

## <a name="syntax"></a>구문

```
<CommandName>MyCommand</CommandName>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[Strings 요소](../extensibility/strings-element.md)|및 등의 텍스트 요소를 `ButtonText` 그룹화 `CommandName` 합니다.|

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블 (.vvsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
