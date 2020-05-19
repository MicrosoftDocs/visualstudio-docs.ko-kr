---
title: 부실 코드 경고 대화 상자 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dba38e5b5d9f7a2be710cad58d6f2297dd03a412
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729537"
---
# <a name="stale-code-warning-dialog-box"></a>부실 코드 경고 대화 상자

이 대화 상자는 네이티브 코드에서 **편집하며 계속하기**가 즉시 적용될 수 없는 변경을 수행했을 때 표시됩니다. 그 결과 현재 스택 프레임의 일부 네이티브 코드가 만료되어 부실 코드가 됩니다. 자세한 내용은 [편집하며 계속하기(C++)](edit-and-continue-visual-cpp.md)를 참조하세요.

**이 대화 상자를 다시 표시 안 함**

이 확인란을 선택하면 이후에는 편집하며 계속하기에서 권한을 확인하지 않고 코드 변경 내용을 적용합니다. **옵션** 대화 상자로 이동하여 **디버깅** 폴더를 열고 **편집하며 계속하기** 페이지를 클릭한 다음, **부실 코드 경고**를 선택하면 다시 이 경고를 설정할 수 있습니다.

## <a name="see-also"></a>참조

- [지원되는 코드 변경(C++)](supported-code-changes-cpp.md)
- [옵션 대화 상자, 디버깅, 편집하며 계속하기](edit-and-continue.md)