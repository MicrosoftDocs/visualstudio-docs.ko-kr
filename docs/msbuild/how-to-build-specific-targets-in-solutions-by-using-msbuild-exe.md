---
title: MSBuild.exe를 사용하여 솔루션의 특정 대상 빌드
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 178dfcaf0bdf8296fd271cb7c4e5dd0bbd251d7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633930"
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>방법: MSBuild.exe를 사용하여 솔루션의 특정 대상 빌드

*MSBuild.exe*를 사용하여 솔루션에서 특정 프로젝트의 특정 대상을 빌드할 수 있습니다.

## <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>솔루션에서 특정 프로젝트의 특정 대상을 빌드하려면

1. 명령줄에서 `MSBuild.exe <SolutionName>.sln`을 입력합니다. 여기서 `<SolutionName>`은 실행할 대상이 포함된 솔루션의 파일 이름에 해당합니다.

2. `-target:` 스위치 뒤에 대상을 \<ProjectName>:\<TargetName> 형식으로 지정합니다. 프로젝트 이름에 `%`, `$`, `@`, `;`, `.`, `(`, `)` 또는 `'` 문자를 포함하는 경우 지정된 대상 이름에서 `_`로 변경합니다.

## <a name="example"></a>예제

 다음 예제에서는 `Rebuild` 프로젝트의 `NotInSlnFolder` 대상을 실행한 다음, `Clean`NewFolder`InSolutionFolder` 솔루션 폴더에 있는 *프로젝트의* 대상을 실행합니다.

```cmd
msbuild SlnFolders.sln -target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean
```

## <a name="troubleshooting"></a>문제 해결

사용할 수 있는 옵션을 검사하려는 경우 MSBuild에서 제공하는 디버깅 옵션을 사용할 수 있습니다. `MSBUILDEMITSOLUTION=1` 환경 변수를 설정하고 솔루션을 빌드합니다. 그러면 빌드 시 솔루션의 MSBuild의 내부 보기를 보여주는 *\<SolutionName>.sln.metaproj*라는 MSBuild 파일을 만듭니다. 이 보기를 검사하여 빌드할 수 있는 대상을 확인할 수 있습니다.

이 내부 보기가 필요하지 않으면 이 환경 변수 설정을 사용하여 빌드하지 않습니다. 이 설정은 솔루션에서 프로젝트를 빌드하는 문제가 발생할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [명령줄 참조](../msbuild/msbuild-command-line-reference.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
