---
title: 셸 명령
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf13c7624d6c9d8e64b79f653eb83a0c5f3b3f0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565879"
---
# <a name="shell-command"></a>셸 명령
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 내에서 실행 프로그램을 시작합니다.

## <a name="syntax"></a>구문

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>인수
`path`

필수 사항입니다. 실행할 파일의 경로와 파일 이름 또는 열 문서. 지정된 파일이 PATH 환경 변수에 있는 디렉터리 중 하나에 없으면 전체 경로가 필요합니다.

`args`

(선택 사항) 호출된 프로그램에 전달할 인수입니다.

## <a name="switches"></a>스위치
/commandwindow [또는] /command [또는] /c [또는] /cmd

(선택 사항) 실행 파일에 대한 출력이 **명령** 창에 표시되는지 지정합니다.

/dir:`folder` [또는] /d: `folder`

(선택 사항) 프로그램이 실행될 때 설정할 작업 디렉터리를 지정합니다.

/outputwindow [또는] /output [또는] /out [또는] /o

(선택 사항) 실행 파일에 대한 출력이 **출력** 창에 표시되도록 지정합니다.

## <a name="remarks"></a>설명
`Tools.Shell` 바로 뒤에 /dir /o /c 스위치를 지정해야 합니다. 실행 파일 이름 뒤에 지정된 모든 내용은 명령줄 인수로 전달됩니다.

미리 정의된 별칭 `Shell`을 `Tools.Shell` 대신 사용할 수 있습니다.

> [!CAUTION]
> `path` 인수가 디렉터리 경로와 파일 이름을 제공하면 다음과 같이 전체 경로 이름을 리터럴 따옴표(""")로 묶어야 합니다.

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

세 개의 큰따옴표(""") 각 집합이 `Shell` 프로세서에 의해 단일 큰따옴표 문자로 해석됩니다. 따라서 앞의 예제는 실제로 다음과 같은 경로 문자열을 `Shell` 명령에 전달합니다.

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> 리터럴 따옴표(""")로 경로 문자열을 묶지 않으면 Windows는 첫 번째 공백까지의 문자열 부분만 사용합니다. 예를 들어 위의 경로 문자열이 제대로 인용되지 않으면 Windows는 C:\ 루트 디렉터리에 있는 "Program"이라는 파일을 찾습니다. C:\Program.exe 실행 파일을 실제로 사용할 수 있는 경우 Windows는 불법적 인 변조로 설치한 경우 조차도 원하는 "c:\Program Files\SomeFile.exe" 프로그램 대신 해당 프로그램을 실행하려고 시도합니다.

## <a name="example"></a>예제
다음 명령은 xcopy.exe를 사용하여 `MyText.txt` 파일을 `Text` 폴더에 복사합니다. xcopy.exe 출력은 **명령 창** 및 **출력** 창 모두에 표시됩니다.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>참고 항목

- [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)
- [명령 창](../../ide/reference/command-window.md)
- [출력 창](../../ide/reference/output-window.md)
- [찾기/명령 상자](../../ide/find-command-box.md)
- [Visual Studio 명령 별칭](../../ide/reference/visual-studio-command-aliases.md)
