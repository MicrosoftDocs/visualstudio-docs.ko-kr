---
title: VSIX v3 | 있는 확장 폴더 외부 설치 Microsoft Docs
description: extensions 폴더 외부에 Visual Studio SDK 확장 자산을 설치하는 방법 및 유효한 위치에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24b1e1a73ff588e5531eec2025c8a3c9e94760a4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898450"
---
# <a name="install-outside-the-extensions-folder"></a>확장 폴더 외부에 설치

Visual Studio 2017 및 VSIX v3(버전 3)부터 확장 자산은 extensions 폴더 외부에 설치할 수 있습니다. 현재 다음 위치는 유효한 설치 위치로 설정됩니다(여기서 [INSTALLDIR]은 Visual Studio 인스턴스의 설치 디렉터리에 매핑됨).

* [INSTALLDIR]\MSBuild
* [INSTALLDIR]\Xml\Schemas
* [INSTALLDIR]\Common7\IDE\PublicAssemblies
* [INSTALLDIR]\Licenses
* [INSTALLDIR]\Common7\IDE\ReferenceAssemblies
* [INSTALLDIR]\Common7\IDE\RemoteDebugger
* [INSTALLDIR]\Common7\IDE\VC\VCTargets(Visual Studio 2017에서만 지원되며 Visual Studio 2019 이상에서 사용되지 않음)

> [!NOTE]
> VSIX 형식을 사용하면 Visual Studio 설치 폴더 구조 외부에 설치할 수 없습니다. 

이러한 디렉터리에 대한 설치를 지원하려면 VSIX를 "컴퓨터당 인스턴스당"로 설치해야 합니다. extension.vsixmanifest 디자이너에서 "모든 사용자" 확인란을 확인하여 사용하도록 설정할 수 있습니다.

![모든 사용자 확인](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>InstallRoot를 설정하는 방법

설치 디렉터리를 설정하려면 Visual Studio **속성** 창을 사용할 수 있습니다. 예를 들어 프로젝트 참조의 속성을 위의 위치 중 하나로 설정할 수 `InstallRoot` 있습니다.

![루트 속성 설치](media/install-root-properties.png)

그러면 `ProjectReference` VSIX 프로젝트의 .csproj 파일 내의 해당 속성에 일부 메타데이터가 추가됩니다.

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> 원하는 경우 .csproj 파일을 직접 편집할 수 있습니다.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>InstallRoot에서 하위 경로를 설정하는 방법

아래의 하위 경로에 설치하려는 경우 `InstallRoot` 속성과 마찬가지로 속성을 설정하여 설치할 수 `VsixSubPath` `InstallRoot` 있습니다. 예를 들어 프로젝트 참조의 출력을 '[INSTALLDIR]\MSBuild\MyCompany\MySDK\1.0'에 설치하려고 합니다. 속성 디자이너를 사용하면 이 작업을 쉽게 수행할 수 있습니다.

![set 하위 경로](media/set-subpath.png)

해당하는 .csproj 변경 내용은 다음과 같습니다.

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>추가 정보

속성 디자이너 변경은 프로젝트 참조 이상에 적용됩니다. `InstallRoot` 위에서 설명한 것과 동일한 메서드를 사용하여 프로젝트 내의 항목에 대한 메타데이터도 설정할 수 있습니다.
