---
title: 옵션 대화 상자, 키보드 설정, Office Word 키보드
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5180aa2f4c5022cedcba2c5377d2ff2ac14ffb28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66835988"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>옵션 대화 상자, 키보드 설정 Microsoft Office Microsoft Office Word 키보드
  Word와 Visual Studio Microsoft Office 모두 바로 가기 키를 처리 합니다. Word 및 Visual Studio의 다른 명령에 대해 동일한 바로 가기 키 조합을 사용할 수 있습니다. Visual Studio의 문서 수준 프로젝트에서 Word가 열려 있는 경우 한 번에 한 응용 프로그램만 바로 가기 키 명령을 받습니다. 기본적으로 Visual Studio는 모든 바로 가기 키 명령을 받지만 **동적 키보드 구성표**를 선택 하 여 문서에 포커스가 있을 때 Word를 받도록 할 수 있습니다.

 현재 바로 가기 키를 처리 중인 응용 프로그램의 명령에 할당 되지 않은 바로 가기 키를 사용 하는 경우 바로 가기 키가 다른 응용 프로그램에 전달 됩니다.

 사용자가 선택 하는 옵션은 변경 될 때까지 Word 프로젝트에 계속 적용 됩니다. 선택은 Excel 프로젝트 Microsoft Office에 영향을 주지 않습니다. Microsoft Office Excel 키보드 옵션을 사용 하 여 Excel에 대 한 변경 작업을 수행 해야 합니다.

## <a name="uielement-list"></a>UI 요소 목록
 **Visual Studio 키보드 구성표** Visual Studio는 Word 문서에 포커스가 있는 경우에도 모든 바로 가기 키 명령을 받습니다. 예를 들어, 문서에 포커스가 있는 상태에서 **f5** 키를 누르면 Visual Studio에서 솔루션 디버깅이 시작 됩니다.

 **동적 키보드 구성표** Visual Studio에 포커스가 있는 경우에만 바로 가기 키 명령이 수신 됩니다. Word 문서에 포커스가 있으면 Word에 모든 바로 가기 키 명령이 수신 됩니다. 예를 들어 Word 문서에 포커스가 있을 때 함수 키 **f5** 키를 누르면 **이동** 탭이 선택 된 상태로 **찾기 및 바꾸기** 대화 상자가 열립니다. Visual Studio에 포커스가 있는 상태에서 **f5** 키를 누르면 visual studio에서 솔루션 디버깅이 시작 됩니다.

## <a name="see-also"></a>추가 정보
- [옵션 대화 상자, 키보드 설정 Microsoft Office Microsoft Office Excel 키보드](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
