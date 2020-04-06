---
title: 생성PkgDef 유틸리티 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709162"
---
# <a name="createpkgdef-utility"></a>만들기PkgDef 유틸리티
Visual Studio 확장에 대한 .dll 파일을 매개 변수로 가져와 *.dll* 파일과 함께 *.pkgdef* 파일을 만듭니다. *.pkgdef* 파일에는 확장프로그램을 설치할 때 시스템 레지스트리에 기록되는 모든 정보가 포함되어 있습니다.

> [!NOTE]
> Visual Studio SDK에 포함된 대부분의 프로젝트 템플릿은 빌드 프로세스의 일부로 *.pkgdef* 파일을 자동으로 만듭니다. 이 문서는 수동으로 패키지를 만들거나 기존 패키지를 *.pkgdef* 배포를 사용하도록 변환하려는 사용자를 위한 것입니다.

## <a name="syntax"></a>구문

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>인수
**/out=&lt;파일 이름&gt;**\
필수 사항입니다. *.pkgdef* 출력 파일의 이름을 &lt;FileName으로&gt;설정합니다.

**/코드베이스**\
(선택 사항) CodeBase 유틸리티로 강제로 **등록합니다.**

**/어셈블리**\
어셈블리 유틸리티로 강제로 **등록합니다.**

**&lt;어셈블리 경로&gt;**\
*.pkgdef를*생성하려는 *.dll* 파일의 경로입니다.

## <a name="remarks"></a>설명
*.pkgdef* 파일을 사용하여 확장 확장 배포는 이전 버전의 Visual Studio의 레지스트리 요구 사항을 대체합니다.

::: moniker range=">=vs-2019"

*.pkgdef* 파일은 다음 위치 중 하나에 설치해야 합니다.

- *%로컬 앱 데이터%\마이크로소프트\비주얼 스튜디오\16.0\확장\\*

- *%vsinstalldir%\공통7\IDE\확장\\*

설치 폴더가 *%localappdata%=Microsoft\Visual Studio\16.0\확장인\\*경우 확장은 Visual Studio에서 인식되지만 기본적으로 비활성화됩니다. 사용자는 확장 관리를 사용하여 **확장을 활성화할**수 있습니다.

설치 폴더가 *%vsinstalldir%\Common7\IDE\확장인\\*경우 확장은 기본적으로 활성화됩니다.

> [!NOTE]
> 확장 **관리** 도구는 VSIX 패키지의 일부로 설치되어 있는 경우 확장에 액세스하는 데 사용할 수 없습니다.

::: moniker-end

::: moniker range="vs-2017"

*.pkgdef* 파일은 다음 위치 중 하나에 설치해야 합니다.

- *%로컬 앱 데이터%\마이크로소프트\비주얼 스튜디오\15.0\확장\\*

- *%vsinstalldir%\공통7\IDE\확장\\*

설치 폴더가 *%localappdata%=Microsoft\Visual Studio\15.0\확장인\\*경우 확장은 Visual Studio에서 인식되지만 기본적으로 비활성화됩니다. 사용자는 확장 및 업데이트를 사용하여 확장을 활성화할 수 **있습니다.**

설치 폴더가 *%vsinstalldir%\Common7\IDE\확장인\\*경우 확장은 기본적으로 활성화됩니다.

> [!NOTE]
> **확장 및 업데이트** 도구는 VSIX 패키지의 일부로 설치되어 있는 경우 확장에 액세스하는 데 사용할 수 없습니다.

::: moniker-end

## <a name="see-also"></a>참조
- [만들기ExpInstance 유틸리티](../../extensibility/internals/createexpinstance-utility.md)
