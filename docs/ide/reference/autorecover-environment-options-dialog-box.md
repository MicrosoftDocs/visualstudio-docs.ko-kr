---
title: 옵션 대화 상자, 환경, 자동 저장
ms.date: 08/14/2020
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
ms.openlocfilehash: f35424089b293b858c609d19f59459693373eb4d
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250295"
---
# <a name="autorecover-environment-options-dialog-box"></a>자동 복구, 환경, 옵션 대화 상자

**옵션** 대화 상자의 이 페이지를 사용하여 파일을 자동으로 백업할지 여부를 지정합니다. Visual Studio가 예기치 않게 종료된 경우 수정된 파일을 복원할지 여부를 지정할 수도 있습니다.

이 대화 상자에 액세스하려면 **도구** > **옵션** > **환경** > **자동 복구**로 이동합니다.

:::image type="content" source="media/autorecover-options.png" alt-text="옵션 대화 상자의 자동 복구 섹션 스크린샷":::

**자동 복구 정보 저장 간격: [n]분**

::: moniker range="vs-2019"

편집기에서 파일이 자동으로 저장되는 빈도를 사용자 지정하려면 이 옵션을 사용합니다. 이전에 저장된 파일의 경우 Visual Studio 2019 버전 16.2 이상에서는 ***%LocalAppData%\Microsoft\VisualStudio\BackupFiles\\[projectname]*** 에 파일 사본이 저장됩니다. 파일을 새로 만들고 아직 저장하지 않은 경우 Visual Studio에서는 임의로 생성된 파일 이름을 사용하여 파일이 자동 저장됩니다.

> [!NOTE]
> Visual Studio 2019 버전 16.1 이상을 사용하는 경우 파일 위치는 *%USERPROFILE%\Documents\Visual Studio [version]\Backup Files\\[projectname]* 입니다. 자세한 내용은 [Visual Studio 2019 릴리스 정보 기록](/visualstudio/releases/2019/release-notes-history/) 페이지를 참조하세요.

::: moniker-end

::: moniker range="vs-2017"

편집기에서 파일이 자동으로 저장되는 빈도를 사용자 지정하려면 이 옵션을 사용합니다. 이전에 저장된 파일의 경우 Visual Studio 2017에서는 *%USERPROFILE%\Documents\Visual Studio [version]\Backup Files\\[projectname]* 에 파일 사본이 저장됩니다. 파일을 새로 만들고 아직 저장하지 않은 경우 Visual Studio에서는 임의로 생성된 파일 이름을 사용하여 파일이 자동 저장됩니다.

::: moniker-end

**자동 복구 정보 보관 기간: [n]일**

Visual Studio에서 자동 복구를 위해 생성된 파일을 보관할 기간을 지정하려면 이 옵션을 사용합니다.

### <a name="see-also"></a>참고 항목

- [옵션 대화 상자](../../ide/reference/options-dialog-box-visual-studio.md)
