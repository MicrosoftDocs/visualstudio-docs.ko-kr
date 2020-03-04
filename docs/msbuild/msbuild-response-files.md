---
title: MSBuild 지시 파일 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44d6e3c77fee53b15ec8d18cb74fd7355ee101a8
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633241"
---
# <a name="msbuild-response-files"></a>MSBuild 지시 파일

지시( *.rsp*) 파일은 *MSBuild.exe* 명령줄 스위치를 포함하는 텍스트 파일입니다. 각 스위치가 별도 줄에 있거나 모든 스위치가 한 줄에 있을 수 있습니다. 주석 줄의 앞에 **#** 기호가 붙습니다. **@** 스위치는 다른 지시 파일을 *MSBuild.exe*에 전달하는 데 사용됩니다.

## <a name="msbuildrsp"></a>MSBuild.rsp

자동 지시 파일은 프로젝트를 빌드할 때 자동으로 *MSBuild.exe*에서 사용하는 특별한 *.rsp* 파일입니다. *MSBuild.rsp*라는 파일은 *MSBuild.exe*와 같은 디렉터리에 있어야 합니다. 그렇지 않으면 찾을 수 없습니다. 이 파일을 편집하여 *MSBuild.exe*에 대한 기본 명령줄 스위치를 지정할 수 있습니다. 예를 들어 프로젝트를 빌드할 때마다 동일한 로거를 사용하는 경우 **-logger** 스위치를 *MSBuild.rsp*에 추가할 수 있습니다. 그러면 *MSBuild.exe*는 프로젝트가 빌드될 때마다 로거를 사용합니다.

## <a name="directorybuildrsp"></a>Directory.Build.rsp

버전 15.6 이상에서는 MSBuild가 프로젝트의 부모 디렉터리에서 *Directory.Build.rsp*라는 파일을 검색합니다.  이 기능은 소스 코드 리포지토리에서 명령줄 빌드 중에 기본 인수를 제공하는 데 도움이 될 수 있습니다.  또한 호스팅된 빌드의 명령줄 인수를 지정하는 데 사용할 수 있습니다.

## <a name="see-also"></a>참조

- [MSBuild 참조](../msbuild/msbuild-reference.md)
- [명령줄 참조](../msbuild/msbuild-command-line-reference.md)
