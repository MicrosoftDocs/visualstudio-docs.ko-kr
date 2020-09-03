---
title: 옵션 대화 상자, 환경, 자동 복구 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPag.Environment.AutoRecover
- VS.DialogAutoRestore
- VS.ToolsOptionsPages.Environment.AutoRecover
- VS.ToolsOptionsPages.Environment.Auto_Save_and_Restore
helpviewer_keywords:
- files, recovering
- AutoRecover page
- saving files, automatically
- files, saving automatically
ms.assetid: 397e5e44-4bbe-4289-94d1-642b466c9111
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 743543e03806a842eabc2bbfc69011d63b1264d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660972"
---
# <a name="autorecover-environment-options-dialog-box"></a>옵션 대화 상자, 환경, 자동 저장
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[옵션] 대화 상자의 이 페이지를 사용하여 파일을 자동으로 백업할지 여부를 지정합니다. 이 페이지에서는 IDE(통합 개발 환경)가 예기치 않게 종료될 때 수정된 파일을 복원할지 여부를 지정할 수도 있습니다. 이 대화 상자에 액세스하려면 **도구** 메뉴, **옵션**, **환경** 폴더, **자동 복구** 페이지를 차례로 선택합니다. 이 페이지가 목록에 나타나지 않으면 **옵션** 대화 상자에서 **모든 설정 표시**를 선택합니다.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 도구 메뉴에서 설정 가져오기 및 내보내기를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

 **매 \<n> 분 마다 자동 복구 정보 저장** 편집기에서 파일이 자동으로 저장 되는 빈도를 사용자 지정 하려면이 옵션을 사용 합니다. 이전에 저장 한 파일의 경우 파일의 복사본이 \\ ..\My documents\visual Studio \<*version*> \backup files \\ < *projectname*>에 저장 됩니다. 파일을 새로 만들고 수동으로 저장하지 않은 경우 파일은 임의로 생성된 파일 이름을 사용하여 자동 저장됩니다.

 ** \<n> 며칠 동안 자동 저장 정보 유지** 이 옵션을 사용 하면 Visual Studio에서 자동으로 생성 되는 파일을 유지할 기간을 지정할 수 있습니다.

## <a name="see-also"></a>관련 항목
 [옵션 대화 상자](../../ide/reference/options-dialog-box-visual-studio.md)
