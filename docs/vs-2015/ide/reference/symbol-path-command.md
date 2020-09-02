---
title: 기호 경로 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d02d4cfede6ed3499d09ff58e4454c1ef9cbe0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651012"
---
# <a name="symbol-path-command"></a>기호 경로 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버거에서 기호를 검색할 디렉터리 목록을 설정합니다.

## <a name="syntax"></a>구문

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>인수
 `pathname` 선택 사항입니다. 디버거가 기호를 검색할 경로의 세미콜론으로 구분된 목록입니다.

## <a name="remarks"></a>설명
 `pathname`을 지정하지 않으면 이 명령은 현재 기호 경로를 나열합니다.

## <a name="example"></a>예제
 이 예제에서는 기호 디렉터리 목록에 두 개의 경로를 추가합니다.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>예제
 이 예제에서는 현재 기호 경로의 세미콜론으로 구분된 목록을 표시합니다.

```
Debug.SymbolPath
```

## <a name="see-also"></a>관련 항목
 [명령 창](../../ide/reference/command-window.md) [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
