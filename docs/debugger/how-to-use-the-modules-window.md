---
title: DLL 및 실행 파일 보기
titleSuffix: Visual Studio Modules window
ms.custom: seodec18
ms.date: 11/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fa284a44f75503a2890a15981d2b4f9947be2fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348680"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>모듈 창에서 DLL 및 실행 파일 보기(C#, C++, Visual Basic, F#)

Visual Studio 디버깅 중에 **모듈** 창에는 앱에서 사용하는 DLL 및 실행 파일( *.exe* 파일)에 대한 정보가 나열되고 표시됩니다.

> [!NOTE]
> SQL 또는 스크립트 디버깅에는 모듈 창을 사용할 수 없습니다.

## <a name="use-the-modules-window"></a>모듈 창 사용

모듈 창을 열려면 디버깅 중에 **디버그** > **창** > **모듈**을 선택합니다(또는 **Ctrl+Alt+U**를 누름).

기본적으로 **모듈** 창에서는 모듈이 로드 순서대로 정렬됩니다. 임의의 창 열을 기준으로 정렬하려면 열의 맨 위에 있는 헤더를 선택합니다.

## <a name="load-symbols"></a>기호 로드

**모듈** 창의 **기호 상태** 열에는 어느 모듈이 디버그 기호를 로드했는지 표시됩니다. 상태가 **기호를 로드하지 않고 건너뛰었습니다.** , **PDB 파일을 찾거나 열 수 없습니다.** 또는 **포함/제외 설정으로 로드가 비활성화되었습니다.** 인 경우 기호를 수동으로 로드할 수 있습니다. 기호를 로드하고 사용하는 방법에 대한 자세한 내용은 [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)을 참조하세요.

**기호를 수동으로 로드하려면**

1. **모듈** 창에서 기호가 로드되지 않은 모듈을 마우스 오른쪽 단추로 클릭합니다.

   - 기호가 로드되지 않는 이유에 대한 자세한 내용을 보려면 **기호 로드 정보**를 선택합니다.

   - 기호를 수동으로 로드하려면 **기호 로드**를 선택합니다.

1. 기호가 로드되지 않는 경우 **기호 설정**을 선택하여 **옵션** 대화 상자를 열고 기호 로드 위치를 지정하거나 변경합니다.

   공용 Microsoft 기호 서버 또는 다른 서버에서 기호를 다운로드하거나 컴퓨터의 폴더에서 기호를 로드할 수 있습니다. 자세한 내용은 [기호 위치 및 로드 동작 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)을 참조하세요.

**기호 로드 동작 설정을 변경하려면:**

1. **모듈** 창에서 모듈을 마우스 오른쪽 단추로 클릭합니다.

1. **기호 설정**을 선택합니다.

1. **모든 기호 로드**를 선택하거나, 포함하거나 제외할 모듈을 선택합니다.

1. **확인**을 선택합니다. 변경 내용은 다음 디버그 세션에서 적용됩니다.

**특정 모듈에 대한 기호 로드 동작을 변경하려면:**

1. **모듈** 창에서 모듈을 마우스 오른쪽 단추로 클릭합니다.

1. 오른쪽 클릭 메뉴에서 **항상 자동으로 로드**를 선택하거나 선택 취소합니다. 변경 내용은 다음 디버그 세션에서 적용됩니다.

## <a name="see-also"></a>참조
- [실행 중단](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)
- [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)