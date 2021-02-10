---
title: 현재 프로세스 설정
description: 현재 프로세스 설정 명령에 대해 알아보고 지정한 프로세스를 디버거의 활성 프로세스로 설정하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cef9475e9336acd5c10cee604d453706ea7321c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957805"
---
# <a name="set-current-process"></a>현재 프로세스 설정
디버거에서 지정한 프로세스를 활성 프로세스로 설정합니다.

## <a name="syntax"></a>구문

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>인수
`index`

필수 요소. 프로세스의 인덱스입니다.

## <a name="remarks"></a>설명
디버그하는 동안 여러 프로세스에 연결할 수 있지만 한 번에 프로세스 하나만 디버거에서 활성화됩니다. `SetCurrentProcess` 명령을 사용하여 활성 프로세스를 설정할 수 있습니다.

## <a name="example"></a>예제

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
