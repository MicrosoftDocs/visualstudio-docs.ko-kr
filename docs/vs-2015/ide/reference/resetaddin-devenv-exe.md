---
title: -ResetAddin(devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9958e6e9a540dce1a405df8991780600b8f4a702
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665595"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin(devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정된 추가 기능과 연결된 명령 및 명령 UI를 제거합니다.

## <a name="syntax"></a>구문

```
Devenv /ResetAddin AddIn
```

## <a name="arguments"></a>인수
 `AddIn` 선택 사항입니다. 추가 기능의 명령 이름입니다.

## <a name="remarks"></a>설명
 기본적으로 추가 기능에 대 한 명령 이름은와 같습니다 *\<AddInSolutionName>* . Connect<em>. \<AddInSolutionName> </em>및는 Connect.cs에 `commandName` 메서드의 매개 변수로 표시 됩니다. `Exec` 먼저 Visual Studio의 명령 창에 추가 기능 이름을 입력하고 IntelliSense를 사용하여 나머지 부분을 입력하는 방식으로 명령 이름을 확인할 수도 있습니다.

## <a name="example"></a>예
 다음 예제에서는 Visual Studio를 시작하고 `MyAddin` 추가 기능이 시작 시 실행되지 않도록 합니다.

```
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin
```

## <a name="see-also"></a>관련 항목
 Visual Studio [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md) [에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)
