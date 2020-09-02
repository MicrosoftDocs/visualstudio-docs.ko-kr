---
title: -Diff | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fd76b0803f43a7694ec0d689eeb8489f491f8464
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657765"
---
# <a name="diff"></a>/Diff
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

두 파일을 비교합니다. 차이점은 특별한 Visual Studio 창에 표시됩니다.

## <a name="syntax"></a>구문

```
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]
```

## <a name="arguments"></a>인수
 `SourceFile` 필수입니다. 비교할 첫 번째 파일의 전체 경로와 이름입니다.

 `TargetFile` 필수입니다. 비교할 두 번째 파일의 전체 경로와 이름입니다.

 `SourceDisplayName` 선택 사항입니다. 첫 번째 파일의 표시 이름입니다.

 `TargetDisplayName` 선택 사항입니다. 두 번째 파일의 표시 이름입니다.
