---
title: 설정 가져오기 및 내보내기 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e3ee8549fd8cf1a4551818c013551ba24128f95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671045"
---
# <a name="import-and-export-settings-command"></a>설정 가져오기 및 내보내기 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 설정을 가져오거나, 내보내거나, 다시 설정합니다.

## <a name="syntax"></a>구문

```
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>스위치
 `filename`내보내기(선택 사항). 현재 설정을 지정된 파일로 내보냅니다.

 /import: `filename` 선택 사항입니다. 지정된 파일의 설정을 가져옵니다.

 /reset 선택 사항입니다. 현재 설정을 다시 설정합니다.

## <a name="remarks"></a>설명
 스위치 없이 이 명령을 실행하면 **설정 가져오기 및 내보내기** 마법사가 열립니다. 자세한 내용은 [방법: 컴퓨터 또는 Visual Studio 버전 간 설정 공유](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882)을 참조하세요.

## <a name="example"></a>예
 다음 명령은 현재 설정을 `MyFile.vssettings` 파일로 내보냅니다.

```
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>관련 항목
 [Visual studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [visual studio 명령](../../ide/reference/visual-studio-commands.md)
