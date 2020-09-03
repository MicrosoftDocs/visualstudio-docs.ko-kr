---
title: CreatePkgDef 유틸리티 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709162"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef 유틸리티
Visual Studio 확장에 대 한 .dll 파일을 매개 변수로 사용 하 고 *.dll* 파일과 함께 사용 되는 *.pkgdef* 파일을 만듭니다. *.Pkgdef* 파일은 확장이 설치 될 때 시스템 레지스트리에 기록 될 모든 정보를 포함 합니다.

> [!NOTE]
> Visual Studio SDK에 포함 된 대부분의 프로젝트 템플릿은 빌드 프로세스의 일부로 *.pkgdef* 파일을 자동으로 만듭니다. 이 문서는 수동으로 패키지를 만들거나 기존 패키지를 .pkgdef 배포를 사용 하도록 변환 하려는 사용자를 위한 것입니다 *.*

## <a name="syntax"></a>구문

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>인수
**/out = &lt; FileName&gt;**\
필수 요소. *.Pkgdef* 출력 파일의 이름을 FileName으로 설정 합니다. &lt; &gt;

**/codebase**\
선택 사항입니다. **코드 베이스** 유틸리티를 사용 하 여 등록을 강제 합니다.

**/assembly**\
**어셈블리** 유틸리티를 사용 하 여 등록을 강제 합니다.

**&lt;AssemblyPath&gt;**\
*.Pkgdef*를 생성 하려는 *.dll* 파일의 경로입니다.

## <a name="remarks"></a>설명
*.Pkgdef* 파일을 사용 하 여 확장 배포는 이전 버전의 Visual Studio에 대 한 레지스트리 요구 사항을 대체 합니다.

::: moniker range=">=vs-2019"

*.Pkgdef* 파일은 다음 위치 중 하나에 설치 해야 합니다.

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

설치 폴더가 *%Localappdata%\Microsoft\Visual Studio\16.0\Extensions \\ *인 경우 Visual Studio에서 확장을 인식 하지만 기본적으로 사용 하지 않도록 설정 됩니다. 사용자는 확장 **관리**를 사용 하 여 확장을 사용 하도록 설정할 수 있습니다.

설치 폴더가 *%vsinstalldir%\Common7\IDE\Extensions \\ *인 경우 확장은 기본적으로 사용 하도록 설정 됩니다.

> [!NOTE]
> 확장 **관리** 도구는 VSIX 패키지의 일부로 설치 되지 않은 경우 확장에 액세스할 때 사용할 수 없습니다.

::: moniker-end

::: moniker range="vs-2017"

*.Pkgdef* 파일은 다음 위치 중 하나에 설치 해야 합니다.

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

설치 폴더가 *%Localappdata%\Microsoft\Visual Studio\15.0\Extensions \\ *인 경우 Visual Studio에서 확장을 인식 하지만 기본적으로 사용 하지 않도록 설정 됩니다. 사용자는 확장 **및 업데이트**를 사용 하 여 확장을 사용 하도록 설정할 수 있습니다.

설치 폴더가 *%vsinstalldir%\Common7\IDE\Extensions \\ *인 경우 확장은 기본적으로 사용 하도록 설정 됩니다.

> [!NOTE]
> 확장 **및 업데이트** 도구는 VSIX 패키지의 일부로 설치 되지 않은 경우 확장에 액세스 하는 데 사용할 수 없습니다.

::: moniker-end

## <a name="see-also"></a>추가 정보
- [CreateExpInstance 유틸리티](../../extensibility/internals/createexpinstance-utility.md)
