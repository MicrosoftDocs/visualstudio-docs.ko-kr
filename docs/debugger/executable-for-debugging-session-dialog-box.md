---
title: 디버깅 세션에 사용할 실행 파일 대화 상자 | Microsoft Docs
description: DLL을 디버그하려면 DLL을 호출하는 실행 파일을 지정해야 합니다. 실행 파일을 지정하지 않는 경우 표시되는 대화 상자에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 20f97c7597dc266fbb4334daf27d3660b351f35a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870833"
---
# <a name="executable-for-debugging-session-dialog-box"></a>디버깅 세션에 사용할 실행 파일 대화 상자

이 대화 상자는 실행 파일이 지정되지 않은 DLL을 디버깅하려고 할 때 나타납니다. Visual Studio는 DLL을 직접 시작할 수 없으며, 대신에 지정된 실행 파일을 시작합니다. DLL이 실행 파일에서 호출되면 DLL을 디버그할 수 있습니다.

 **실행 파일 이름** - 디버그할 DLL을 호출하는 실행 파일의 경로 이름을 입력합니다.

 **프로젝트에 액세스할 수 있는 URL(ATL 서버 전용)** - ATL 서버 DLL을 디버그하는 경우 프로젝트를 찾을 수 있는 URL을 입력합니다.

 입력한 설정은 프로젝트 속성 페이지에 저장되므로 이후 디버깅 세션에서 다시 입력할 필요가 없습니다. 설정을 변경해야 하는 경우에는 속성 페이지를 열고 값을 변경할 수 있습니다. 디버깅 세션의 실행 파일 지정에 대한 자세한 내용은 [DLL 디버깅](../debugger/how-to-debug-from-a-dll-project.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 디버깅](../debugger/index.yml)
- [디버거 소개](../debugger/debugger-feature-tour.md)