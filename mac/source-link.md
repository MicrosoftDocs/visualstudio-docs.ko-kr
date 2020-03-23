---
title: 소스 링크를 사용하여 NuGet 패키지로 디버깅
description: 이 문서에서는 Mac용 Visual Studio의 소스 링크 기능에 대해 설명합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75439087"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>소스 링크를 사용하여 NuGet 패키지로 디버깅

소스 링크 기술을 사용하면 소스 파일에 대한 링크를 포함하여 .PDB를 제공하는 NuGet에서 .NET 어셈블리의 소스 코드를 디버깅할 수 있습니다. 소스 링크는 개발자가 NuGet 패키지를 만들 때 실행되며 어셈블리 및 패키지 내부에 소스 제어 메타데이터를 포함합니다. Mac용 Visual Studio에서 소스 링크를 사용하도록 설정하면 IDE는 설치된 패키지에 대해 소스 파일을 사용할 수 있는지 검색합니다. 그러면 Mac용 Visual Studio가 소스 파일 다운로드를 제공합니다. 개발자는 이를 사용하여 패키지 코드를 단계별로 실행할 수 있습니다. 또한 소스 링크는 Xamarin 프로젝트의 Mono 기본 클래스 라이브러리 코드에서도 작동하므로 .NET Framework 코드를 한 단계씩 실행할 수 있습니다. 소스 링크는 뛰어난 디버깅 환경을 만들기 위해 소스 제어 메타데이터를 제공합니다.

> [!NOTE]
> Mac용 Visual Studio는 현재 기호 서버를 지원하지 않습니다. 따라서 메타데이터가 기호 서버에서 호스트되는 소스 링크는 지원되지 않습니다.

## <a name="enable-source-link"></a>소스 링크 사용

Mac용 Visual Studio에서 소스 링크를 사용하도록 설정하려면 **Visual Studio > 기본 설정... > 프로젝트 > 디버거**로 이동하고 **한 단계씩 외부 코드 실행** 확인란이 선택되었는지 확인합니다.

![한 단계씩 외부 코드 실행 확인란을 보여 주는 기본 설정 대화 상자의 스크린샷](media/source-link1.png)

**외부 코드 다운로드**에서 원하는 대로 설정을 변경할 수 있습니다.
* 묻기: Mac용 Visual Studio에 외부 코드를 다운로드하라는 메시지가 표시됩니다.
* 항상: Mac용 Visual Studio에서 외부 코드를 자동으로 다운로드합니다.
* 안 함: Mac용 Visual Studio에서 관련 외부 코드를 다운로드하지 않습니다.

기본적으로 **묻기**가 선택되어 있습니다. NuGet 패키지에 대한 외부 코드가 검색되면 다음 프롬프트가 표시됩니다.

![NuGet 패키지에 대한 외부 코드가 검색되었을 때 표시되는 프롬프트의 스크린샷](media/source-link2.png)


## <a name="see-also"></a>참조

- [소스 링크 GitHub 리포지토리](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [.NET 설명서](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink) - 소스 링크 및 패키지에 소스 링크 지원을 추가하는 방법에 대한 자세한 내용
