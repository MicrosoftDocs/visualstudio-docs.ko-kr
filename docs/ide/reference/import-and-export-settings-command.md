---
description: Visual Studio 설정을 가져오거나, 내보내거나, 다시 설정합니다.
title: 설정 가져오기 및 내보내기 명령
ms.date: 11/21/2018
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f2ea4811af2c44277b9a6dc285972c5267b28d7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223677"
---
# <a name="import-and-export-settings-command"></a>설정 가져오기 및 내보내기 명령

Visual Studio 설정을 가져오거나, 내보내거나, 다시 설정합니다.

## <a name="syntax"></a>Syntax

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>스위치

/export:`filename`

선택 사항입니다. 현재 설정을 지정된 파일로 내보냅니다.

/import:`filename`

선택 사항입니다. 지정된 파일의 설정을 가져옵니다.

/reset

선택 사항입니다. 현재 설정을 다시 설정합니다.

## <a name="remarks"></a>설명

스위치 없이 이 명령을 실행하면 **설정 가져오기 및 내보내기** 마법사가 열립니다. 자세한 내용은 [설정 동기화](../synchronized-settings-in-visual-studio.md) 및 [환경 설정](../environment-settings.md)을 참조하세요.

## <a name="example"></a>예제

다음 명령은 현재 설정을 `MyFile.vssettings` 파일로 내보냅니다.

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>추가 정보

- [환경 설정](../../ide/environment-settings.md)
- [설정 동기화](../../ide/synchronized-settings-in-visual-studio.md)
- [Visual Studio IDE 개인 설정](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
