---
description: Visual Studio 설정을 가져오거나, 내보내거나, 다시 설정합니다. vssettings 파일 확장명
title: 설정 가져오기 및 내보내기 명령
ms.date: 05/28/2021
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
ms.openlocfilehash: dba50cf598c3c74f6c9407fbef5d55f938941a11
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687647"
---
# <a name="import-and-export-settings-command-vssettings-file"></a>설정 가져오기 및 내보내기 명령(.vssettings 파일)

Visual Studio 설정 파일 `.vssettings`를 가져오거나, 내보내거나, 다시 설정합니다.

파일의 스키마가 열려 있습니다. 가장 일반적으로 스키마는 각 범주가 태그인 XML 구조를 따르며, 태그 자체에는 하위 범주 태그가 포함될 수 있습니다. 이러한 하위 범주 태그에는 속성 값 태그가 포함될 수 있습니다. 대부분의 패키지는 공통 구조를 사용하지만 Visual Studio의 모든 패키지는 선택한 스키마를 사용하여 파일에 임의 XML을 제공할 수 있습니다.

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
