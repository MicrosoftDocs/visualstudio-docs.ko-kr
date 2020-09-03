---
title: -Setup (devenv.exe) | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a923d1f3532548ebc6ed651a0739e0e5792f7967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663527"
---
# <a name="setup-devenvexe"></a>/Setup(devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 가 모든 사용 가능한 VSPackages에서 메뉴, 도구 모음 및 명령 그룹을 설명하는 리소스 메타데이터를 병합하도록 합니다.

## <a name="syntax"></a>구문

```
devenv /setup
```

## <a name="remarks"></a>설명
 이 스위치는 인수가 필요 없습니다. `devenv /setup` 명령은 일반적으로 설치 프로세스의 마지막 단계로 표시됩니다. `/setup` 스위치의 사용이 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]를 시작하지는 않습니다.

 `devenv` 및 [devenv](../../ide/reference/setup-devenv-exe.md) 스위치를 사용하려면 관리자 권한으로 [devenv](../../ide/reference/installvstemplates-devenv-exe.md) 를 실행해야 합니다.

## <a name="example"></a>예
 이 예는 VSPackages를 포함하는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 버전의 설치에서 마지막 단계를 보여 줍니다.

```
devenv /setup
```

## <a name="see-also"></a>관련 항목
 [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md)
