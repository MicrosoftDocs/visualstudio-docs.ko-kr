---
title: 기호 경로 명령
description: 기호 경로 명령에 대해 알아보고 디버거에서 기호를 검색할 디렉터리 목록을 설정하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 72e69300e9dc621ea346c05923168c33bc7065c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967165"
---
# <a name="symbol-path-command"></a>기호 경로 명령
디버거에서 기호를 검색할 디렉터리 목록을 설정합니다.

## <a name="syntax"></a>구문

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>인수
`pathname`

선택 사항입니다. 디버거가 기호를 검색할 경로의 세미콜론으로 구분된 목록입니다.

## <a name="remarks"></a>설명
`pathname`을 지정하지 않으면 이 명령은 현재 기호 경로를 나열합니다.

## <a name="example-1"></a>예 1
이 예제에서는 기호 디렉터리 목록에 두 개의 경로를 추가합니다.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example-2"></a>예제 2
이 예제에서는 현재 기호 경로의 세미콜론으로 구분된 목록을 표시합니다.

```
Debug.SymbolPath
```

## <a name="see-also"></a>참고 항목

- [명령 창](../../ide/reference/command-window.md)
- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
