---
title: CommandName 요소 | Microsoft Docs
description: CommandName 요소는 옵션 대화 상자의 키보드 범주와 사용자 지정 대화 상자의 명령 목록에 표시되는 텍스트를 지정합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandName element (VSCT XML schema)
- VSCT XML schema elements, CommandName
ms.assetid: a338b767-aa7e-4536-9908-e19a50ab60ac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 193e97880fbc543568636e1979a847877e42db14
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902009"
---
# <a name="commandname-element"></a>CommandName 요소
`CommandName`요소는 **옵션** 대화 상자의 키보드 범주 및 **사용자 지정** 대화 상자의 **명령** 목록에 표시되는 텍스트를 지정합니다.

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

|요소|설명|
|-------------|-----------------|
|[Strings 요소](../extensibility/strings-element.md)|및 와 같은 텍스트 요소를 `ButtonText` `CommandName` 그룹화합니다.|

## <a name="see-also"></a>참조
- [Visual Studio 명령 테이블(.vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
