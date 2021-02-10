---
title: 모듈 목록 표시 명령
description: 모듈 목록 표시 명령 및 현재 프로세스에 대한 모듈을 나열하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4a38a5423568528d267fd92894b8b06b4e5667c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852065"
---
# <a name="list-modules-command"></a>모듈 목록 표시 명령
현재 프로세스에 대한 모듈을 나열합니다.

## <a name="syntax"></a>구문

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>매개 변수
/Address:`yes|no`

선택 사항입니다. 모듈의 메모리 주소를 표시할지 여부를 지정합니다. 기본값은 `yes`여야 합니다.

/Name:`yes|no`

선택 사항입니다. 모듈의 이름을 표시할지 여부를 지정합니다. 기본값은 `yes`여야 합니다.

/Order:`yes|no`

선택 사항입니다. 모듈의 순서를 표시할지 여부를 지정합니다. 기본값은 `no`여야 합니다.

/Path:`yes|no`

선택 사항입니다. 모듈의 경로를 표시할지 여부를 지정합니다. 기본값은 `yes`여야 합니다.

/Process:`yes|no`

선택 사항입니다. 모듈의 프로세스를 표시할지 여부를 지정합니다. 기본값은 `no`여야 합니다.

/SymbolFile:`yes|no`

선택 사항입니다. 모듈의 기호 파일을 표시할지 여부를 지정합니다. 기본값은 `no`여야 합니다.

/SymbolStatus:`yes|no`

선택 사항입니다. 모듈의 기호 상태를 표시할지 여부를 지정합니다. 기본값은 `yes`여야 합니다.

/Timestamp:`yes|no`

선택 사항입니다. 모듈의 타임스탬프를 표시할지 여부를 지정합니다. 기본값은 `no`여야 합니다.

/Version:`yes|no`

선택 사항입니다. 모듈의 버전을 표시할지 여부를 지정합니다. 기본값은 `no`여야 합니다.

## <a name="example"></a>예제
이 예제에서는 현재 프로세스의 모듈 이름, 주소 및 타임스탬프를 나열합니다.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>추가 정보

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [방법: 모듈 창 사용](../../debugger/how-to-use-the-modules-window.md)
