---
title: VSIX v3로 확장 폴더 외부에 설치 | 마이크로 소프트 문서
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700178"
---
# <a name="install-outside-the-extensions-folder"></a>확장 폴더 외부에 설치

Visual Studio 2017 및 VSIX v3(버전 3)을 시작으로 확장 자산은 확장 폴더 외부에 설치할 수 있습니다. 현재 다음 위치는 유효한 설치 위치로 활성화되어 있습니다(여기서 [INSTALLDIR]이 Visual Studio 인스턴스의 설치 디렉터리에 매핑됨).

* [설치DIR]\MSBuild
* [INSTALLDIR]\Xml\스키마스
* [INSTALLDIR]\공통7\IDE\공개 어셈블리
* [설치DIR]\라이센스
* [INSTALLDIR]\공통7\IDE\참조 어셈블리
* [INSTALLDIR]\공통7\IDE\원격 디버거
* [INSTALLDIR]\Common7\IDE\VC\VCTargets (Visual Studio 2017에서만 지원, 비주얼 스튜디오 2019 및 이후 버전에서 더 이상 사용되지 않음)

> [!NOTE]
> VSIX 형식은 Visual Studio 설치 폴더 구조 외부에 설치할 수 없습니다. 

이러한 디렉터리에 대한 설치를 지원하려면 VSIX를 "시스템당 인스턴스별"으로 설치해야 합니다. 이 옵션을 사용하면 extension.vsixmanifest 디자이너의 "모든 사용자" 확인란을 선택할 수 있습니다.

![모든 사용자 확인](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>설치 루트를 설정하는 방법

설치 디렉터리를 설정하려면 Visual Studio에서 **속성** 창을 사용할 수 있습니다. 예를 들어 프로젝트 참조의 `InstallRoot` 속성을 위의 위치 중 하나로 설정할 수 있습니다.

![루트 속성 설치](media/install-root-properties.png)

이렇게 하면 VSIX 프로젝트의 `ProjectReference` .csproj 파일 내부의 해당 속성에 일부 메타데이터가 추가됩니다.

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> 원하는 경우 .csproj 파일을 직접 편집할 수 있습니다.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>설치 루트에서 하위 경로를 설정하는 방법

`InstallRoot`의 하위 경로 아래에 설치하려는 경우 `VsixSubPath` `InstallRoot` 속성과 마찬가지로 속성을 설정하여 설치할 수 있습니다. 예를 들어 프로젝트 참조의 출력을 '[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'에 설치하기를 원한다고 가정해 보겠습니다. 우리는 속성 디자이너와 함께 쉽게이 작업을 수행 할 수 있습니다 :

![하위 경로 설정](media/set-subpath.png)

해당 .csproj 변경 사항은 다음과 같습니다.

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>추가 정보

속성 디자이너 변경 사항은 프로젝트 참조 그 이상에 적용됩니다. 위에서 설명한 `InstallRoot` 것과 동일한 방법을 사용하여 프로젝트 내의 항목에 대한 메타데이터를 설정할 수 있습니다.
