---
title: VSIX v3의 Ngen 지원 | 마이크로 소프트 문서
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb75b9256ca937106235fa7a7d66d9cec71c9c60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702408"
---
# <a name="ngen-support-in-vsix-v3"></a>VSIX v3의 Ngen 지원

Visual Studio 2017과 새로운 VSIX v3(버전 3) 확장 매니페스트 형식을 사용하면 확장 개발자가 설치 시 어셈블리를 "ngen"할 수 있습니다.

다음은 "ngen"이 하는 일을 설명하는 MSDN의 발췌문입니다.

>네이티브 이미지*생성기(Ngen.exe)는*관리되는 응용 프로그램의 성능을 향상시키는 도구입니다. *Ngen.exe는* 컴파일된 프로세서별 컴퓨터 코드를 포함하는 파일인 네이티브 이미지를 만들고 로컬 컴퓨터의 기본 이미지 캐시에 설치합니다. 런타임은 JIT(Just-In-Time) 컴파일러를 사용하지 않고 캐시의 네이티브 이미지를 사용하여 원본 어셈블리를 컴파일할 수 있습니다.
>
>[에서 Ngen.exe (네이티브 이미지 생성기)](/dotnet/framework/tools/ngen-exe-native-image-generator)

어셈블리를 "ngen"하려면 VSIX를 "시스템당 인스턴스당"설치해야 합니다. 디자이너의 "모든 사용자" 확인란을 `extension.vsixmanifest` 선택하여 이 옵션을 사용할 수 있습니다.

![모든 사용자 확인](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Ngen을 활성화하는 방법

어셈블리에 ngen을 사용하려면 Visual Studio에서 **속성** 창을 사용할 수 있습니다.

설정할 수 있는 속성은 4가지가 있습니다.

1. **Ngen** (부울) - true이면 Visual Studio 설치 프로그램이 어셈블리를 "ngen"합니다.
2. **Ngen 응용** 프로그램(문자열) - Ngen은 어셈블리 종속성을 해결하기 위해 응용 프로그램의 *app.config* 파일을 사용할 수 있는 기회를 제공합니다. 이 값은 *사용할 app.config(Visual* Studio 설치 디렉터리에 상대)를 사용하는 응용 프로그램으로 설정되어야 합니다.
3. **Ngen** 아키텍처(열거형) - 기본적으로 어셈블리를 컴파일하는 아키텍처입니다. 옵션은 다음과 같습니다. 지정되지 않음 b. X86 c. X64 d. 모두
4. **Ngen 우선** 순위(1에서 3 사이의 정수) - Ngen 우선 순위 수준은 [Ngen.exe 우선 순위 수준으로](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)문서화되어 있습니다.

다음은 실행 중 **속성** 창입니다.

![속성에 ngen](media/ngen-in-properties.png)

이렇게 하면 VSIX 프로젝트의 *.csproj* 파일 내부의 프로젝트 참조에 메타데이터가 추가됩니다.

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
> 원하는 경우 .csproj 파일을 직접 편집할 수 있습니다.

## <a name="extra-information"></a>추가 정보

속성 디자이너 변경 사항은 프로젝트 참조 그 이상에 적용됩니다. 항목이 .NET 어셈블리인 한 프로젝트 내 항목에 대한 Ngen 메타데이터를 설정할 수 있습니다(위에서 설명한 것과 동일한 방법을 사용).
