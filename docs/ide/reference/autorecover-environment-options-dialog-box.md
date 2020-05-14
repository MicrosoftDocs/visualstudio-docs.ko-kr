---
title: 옵션 대화 상자, 환경, 자동 저장
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81493379cf847251124d2ab4fd0a978abd96af8f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585667"
---
# <a name="autorecover-environment-options-dialog-box"></a>자동 복구, 환경, 옵션 대화 상자

**옵션** 대화 상자의 이 페이지를 사용하여 파일을 자동으로 백업할지 여부를 지정합니다. Visual Studio가 예기치 않게 종료된 경우 수정된 파일을 복원할지 여부를 지정할 수도 있습니다.

**도구** 메뉴를 선택하고 **옵션**을 선택한 다음, **환경** > **자동 복구**를 선택하여 이 대화 상자에 액세스합니다. 이 페이지가 목록에 나타나지 않으면 **옵션** 대화 상자에서 **모든 설정 표시**를 선택합니다.

**자동 복구 정보 저장 간격: [n]분**

편집기에서 파일이 자동으로 저장되는 빈도를 사용자 지정하려면 이 옵션을 사용합니다. 이전에 저장된 파일의 경우 파일 복사본은 *%USERPROFILE%\Documents\Visual Studio\\[version]\Backup Files\\[projectname]* 에 저장됩니다. 파일을 새로 만들고 아직 저장하지 않은 경우 임의로 생성된 파일 이름을 사용하여 파일이 자동 저장됩니다.

**자동 복구 정보 보관 기간: [n]일**

Visual Studio에서 자동 복구를 위해 생성된 파일을 보관할 기간을 지정하려면 이 옵션을 사용합니다.

### <a name="see-also"></a>참고 항목

- [옵션 대화 상자](../../ide/reference/options-dialog-box-visual-studio.md)
