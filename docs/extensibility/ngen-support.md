---
title: VSIX v3의 Ngen 지원 | Microsoft Docs
description: 확장 개발자가 관리 되는 응용 프로그램의 성능을 향상 시키는 데 사용할 수 있는 도구인 네이티브 이미지 생성기를 사용 하도록 설정 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 064176a0a28e3621e796bf60ede552f9cda155b0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864031"
---
# <a name="ngen-support-in-vsix-v3"></a>VSIX v3의 Ngen 지원

Visual Studio 2017 및 새 VSIX v3 (버전 3) 확장 매니페스트 형식을 사용 하면 확장 개발자가 설치 시 어셈블리를 "ngen" 할 수 있습니다.

다음은 "ngen"의 기능을 설명 하는 MSDN에서 발췌 한 것입니다.

>네이티브 이미지 생성기 (*Ngen.exe*)는 관리 되는 응용 프로그램의 성능을 향상 시키는 도구입니다. *Ngen.exe* 는 컴파일된 프로세서별 컴퓨터 코드가 포함 된 파일인 네이티브 이미지를 만들어 로컬 컴퓨터의 네이티브 이미지 캐시에 설치 합니다. 런타임은 JIT(Just-In-Time) 컴파일러를 사용하지 않고 캐시의 네이티브 이미지를 사용하여 원본 어셈블리를 컴파일할 수 있습니다.
>
>from [Ngen.exe (네이티브 이미지 생성기)](/dotnet/framework/tools/ngen-exe-native-image-generator)

어셈블리를 "ngen" 하려면 VSIX를 "컴퓨터별 인스턴스당"으로 설치 해야 합니다. 디자이너에서 "모든 사용자" 확인란을 선택 하 여 사용할 수 있습니다 `extension.vsixmanifest` .

![모든 사용자 확인](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Ngen을 사용 하도록 설정 하는 방법

어셈블리에 대해 ngen을 사용 하려면 Visual Studio의 **속성** 창을 사용할 수 있습니다.

설정할 수 있는 속성에는 다음 4 가지가 있습니다.

1. **Ngen** (부울)-True 이면 Visual Studio 설치 관리자가 어셈블리를 "Ngen" 합니다.
2. **Ngen 응용 프로그램** (문자열)-ngen은 어셈블리 종속성을 해결 하기 위해 응용 프로그램의 *app.config* 파일을 사용할 수 있는 기회를 제공 합니다. 이 값은 *app.config* 를 사용 하려는 응용 프로그램 (Visual Studio 설치 디렉터리 기준)으로 설정 해야 합니다.
3. **Ngen 아키텍처** (enum)-어셈블리를 고유 하 게 컴파일하는 아키텍처입니다. 옵션은입니다. NotSpecified b. X86 c. X64 d. 모두
4. **Ngen 우선 순위** (1에서 3 사이의 정수)-Ngen 우선 순위 수준은 [Ngen.exe 우선 순위](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)수준에서 설명 됩니다.

다음은 동작의 **속성** 창을 확인 하는 것입니다.

![속성의 ngen](media/ngen-in-properties.png)

그러면 VSIX 프로젝트의 *.csproj* 파일 내에 있는 프로젝트 참조에 메타 데이터가 추가 됩니다.

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> 원할 경우 .csproj 파일을 직접 편집할 수 있습니다.

## <a name="extra-information"></a>추가 정보

속성 디자이너 변경 내용은 프로젝트 참조 이상에 적용 됩니다. 항목이 .NET 어셈블리인 경우에도 프로젝트 내에 있는 항목에 대 한 Ngen 메타 데이터 (위에서 설명한 것과 동일한 메서드 사용)를 설정할 수 있습니다.
