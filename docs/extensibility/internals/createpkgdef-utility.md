---
title: CreatePkgDef 유틸리티 | Microsoft Docs
description: Visual Studio 확장에 대한 .dll 파일을 매개 변수로 사용하며 .dll 파일과 함께 사용할 .pkgdef 파일을 만드는 CreatePkgDef 유틸리티에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bfbd4b42d9ceddd40e08c28926a59aecba719fe9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898125"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef 유틸리티
Visual Studio 확장에 대한 .dll 파일을 매개 변수로 사용하여 *.dll* 파일과 함께 *사용할 .pkgdef* 파일을 만듭니다. *.pkgdef* 파일에는 확장이 설치될 때 시스템 레지스트리에 기록되는 모든 정보가 포함되어 있습니다.

> [!NOTE]
> Visual Studio SDK에 포함된 대부분의 프로젝트 템플릿은 빌드 프로세스의 일부로 *.pkgdef* 파일을 자동으로 만듭니다. 이 문서는 패키지를 수동으로 만들거나 기존 패키지를 변환하여 *.pkgdef*  배포를 사용하려는 사람들을 위한 것입니다.

## <a name="syntax"></a>구문

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>인수
**/out= &lt; FileName&gt;**\
필수 요소. *.pkgdef* 출력 파일의 이름을 &lt; FileName 로 &gt; 설정합니다.

**/codebase**\
선택 사항입니다. **CodeBase** 유틸리티를 강제로 등록합니다.

**/assembly**\
**어셈블리** 유틸리티를 강제로 등록합니다.

**&lt;AssemblyPath&gt;**\
*.pkgdef* 를 생성하려는 *.dll* 파일의 경로입니다.

## <a name="remarks"></a>설명
*.pkgdef* 파일을 사용한 확장 배포는 이전 버전의 Visual Studio 레지스트리 요구 사항을 대체합니다.

::: moniker range=">=vs-2019"

*.pkgdef* 파일은 다음 위치 중 하나에 설치해야 합니다.

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

설치 폴더가 *%localappdata%\Microsoft\Visual Studio\16.0\Extensions인 \\* 경우 확장은 Visual Studio 인식되지만 기본적으로 사용하지 않도록 설정됩니다. 사용자는 확장 관리 를 사용하여 확장을 사용하도록 설정할 수 **있습니다.**

설치 폴더가 *%vsinstalldir%\Common7\IDE\Extensions인 \\* 경우 확장은 기본적으로 사용하도록 설정됩니다.

> [!NOTE]
> **확장 관리 도구는** VSIX 패키지의 일부로 설치되지 않은 한 확장에 액세스하는 데 사용할 수 없습니다.

::: moniker-end

::: moniker range="vs-2017"

*.pkgdef* 파일은 다음 위치 중 하나에 설치해야 합니다.

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

설치 폴더가 *%localappdata%\Microsoft\Visual Studio\15.0\Extensions인 \\* 경우 확장은 Visual Studio 인식되지만 기본적으로 사용하지 않도록 설정됩니다. 사용자는 확장 및 업데이트를 사용하여 확장을 사용하도록 설정할 수 **있습니다.**

설치 폴더가 *%vsinstalldir%\Common7\IDE\Extensions인 \\* 경우 확장은 기본적으로 사용하도록 설정됩니다.

> [!NOTE]
> **확장 및 업데이트** 도구는 VSIX 패키지의 일부로 설치되지 않은 한 확장에 액세스하는 데 사용할 수 없습니다.

::: moniker-end

## <a name="see-also"></a>참조
- [CreateExpInstance 유틸리티](../../extensibility/internals/createexpinstance-utility.md)
