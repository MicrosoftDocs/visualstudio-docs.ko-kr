---
title: 옵션, 텍스트 편집기, C-C++, 서식 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ad06dfb32c301985eb4976f6c89c7be1e0e68da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662336"
---
# <a name="options-text-editor-cc-formatting"></a>옵션, 텍스트 편집기, C/C++, 서식
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

C 또는 C++로 프로그래밍할 때 코드 편집기의 기본 동작을 변경할 수 있습니다.

 이 페이지에 액세스하려면 왼쪽 창의 **옵션** 대화 상자에서 **텍스트 편집기**, **C/C++** 를 차례로 확장한 다음 **서식**을 클릭합니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

## <a name="cc-options"></a>C/C++ 옵션
 **자동 요약 정보 도구 설명 사용** 요약 정보 IntelliSense 기능을 사용 하거나 사용 하지 않도록 설정 합니다.

## <a name="inactive-code"></a>비활성 코드
 **비활성 코드 블록 표시** 선언으로 인해 비활성화 된 코드는 `#ifdef` 쉽게 식별할 수 있도록 다른 색으로 표시 됩니다.

 **비활성 코드 불투명 사용 안 함** 비활성 코드는 투명도 대신 색을 사용 하 여 식별할 수 있습니다.

 **비활성 코드 불투명도 (%** ) 비활성 코드 블록에 대 한 불투명도 수준은 사용자 지정할 수 있습니다.

## <a name="indentation"></a>들여쓰기
 **중괄호 들여쓰기** 코드 블록 (예: 함수 또는 루프)을 시작한 후 ENTER 키를 누르면 괄호가 정렬 되는 방식을 구성할 수 있습니다 `for` . 중괄호는 코드 블록 또는 들여쓴 첫 번째 문자에 정렬할 수 있습니다.

 **탭에서 자동 들여쓰기** TAB 키를 누르면 현재 코드 줄에 발생 하는 작업을 구성할 수 있습니다. 줄이 들여쓰기되거나 탭이 삽입됩니다.

## <a name="miscellaneous"></a>기타
 **작업 목록 창에서 주석 열거** 편집기는 주석의 미리 설정 된 단어에 대 한 오픈 소스 파일을 검색할 수 있습니다. **작업 목록** 창에서 발견한 모든 키워드에 대한 항목을 만듭니다.

 **일치 토큰 강조 표시** 커서가 중괄호 옆에 있을 때 편집기는 포함 된 코드를 보다 쉽게 볼 수 있도록 짝이 되는 중괄호를 강조 표시할 수 있습니다.

## <a name="outlining"></a>개요
 **개요 모드로 파일 열기** 텍스트 편집기에서 파일을 가져올 때 개요 기능을 사용 하도록 설정할 수 있습니다. 자세한 내용은 [개요](../../ide/outlining.md)를 참조하세요. 이 옵션을 선택하고 파일을 열면 개요 기능이 활성화됩니다.

 **#Pragma 영역 블록 자동 개요** 이 옵션을 선택 하면 [pragma 지시문](https://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) 에 대 한 자동 개요 표시를 사용할 수 있습니다. 개요 모드에서 이 pragma 영역 블록을 확장하거나 축소할 수 있습니다.

 **문 블록 자동 개요** 이 옵션을 선택 하면 다음 문 구문에 대해 자동 개요를 사용할 수 있습니다.

- [if-else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)

- [switch 문 (c + +)](https://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)

- [while 문(C++)](https://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)

## <a name="see-also"></a>관련 항목
 [IntelliSense를 사용 하](../../ide/using-intellisense.md) 는 [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)
