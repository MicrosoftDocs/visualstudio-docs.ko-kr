---
title: -SafeMode(devenv.exe)
description: SafeMode devenv 명령줄 스위치를 사용하여 안전 모드에서 Visual Studio를 시작하고 기본 환경 및 서비스만 로드하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1626776ec41bdbdfe5ad2b611516e62ada4f15a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957870"
---
# <a name="safemode-devenvexe"></a>/SafeMode(devenv.exe)

안전 모드에서 Visual Studio를 시작하고 기본 환경 및 서비스만 로드합니다.

## <a name="syntax"></a>구문

```shell
devenv /SafeMode
```

## <a name="remarks"></a>설명

이 스위치는 Visual Studio가 시작될 때 모든 타사 VSPackages의 로드를 차단하여 안정적으로 실행될 수 있습니다.

## <a name="example"></a>예제

다음 예제에서는 안전 모드에서 Visual Studio를 시작합니다.

```shell
devenv /safemode
```

## <a name="see-also"></a>참고 항목

- [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
