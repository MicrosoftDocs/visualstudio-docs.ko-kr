---
title: VSIX v3을 사용 하 여 extensions 폴더 외부에서 설치 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 913c3745-8aa9-4260-886e-a05aecfb2225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa2c7d97dda9bba139ec613b367eedbc6307848a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700178"
---
# <a name="install-outside-the-extensions-folder"></a>확장 폴더 외부에 설치

Visual Studio 2017 및 VSIX v3 (버전 3)부터 확장 자산을 extensions 폴더 외부에 설치할 수 있습니다. 현재는 다음 위치를 유효한 설치 위치로 사용할 수 있습니다. 여기서 [INSTALLDIR]는 Visual Studio 인스턴스의 설치 디렉터리에 매핑됩니다.

* [INSTALLDIR] \MSBuild
* [INSTALLDIR] \Xml\Schemas
* [INSTALLDIR] \Common7\IDE\PublicAssemblies
* [INSTALLDIR] \Licenses
* [INSTALLDIR] \Common7\IDE\ReferenceAssemblies
* [INSTALLDIR] \Common7\IDE\RemoteDebugger
* [INSTALLDIR] \Common7\IDE\VC\VCTargets (visual studio 2017에만 지원 되 고 Visual Studio 2019 이상에서 사용 되지 않음)

> [!NOTE]
> VSIX 형식을 사용 하면 Visual Studio 설치 폴더 구조 외부에 설치할 수 없습니다. 

이러한 디렉터리에 대 한 설치를 지원 하려면 VSIX를 "컴퓨터별 인스턴스당"으로 설치 해야 합니다. Source.extension.vsixmanifest 디자이너에서 "모든 사용자" 확인란을 선택 하 여 사용할 수 있습니다.

![모든 사용자 확인](media/check-all-users.png)

## <a name="how-to-set-the-installroot"></a>InstallRoot를 설정 하는 방법

Visual Studio의 **속성** 창을 사용 하 여 설치 디렉터리를 설정할 수 있습니다. 예를 들어, `InstallRoot` 프로젝트 참조의 속성을 위의 위치 중 하나로 설정할 수 있습니다.

![루트 속성 설치](media/install-root-properties.png)

그러면 `ProjectReference` VSIX 프로젝트의 .csproj 파일 내에 있는 해당 속성에 일부 메타 데이터가 추가 됩니다.

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
        <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
        <Name>ClassLibrary1</Name>
        <InstallRoot>PublicAssemblies</InstallRoot>
 </ProjectReference>
```

> [!NOTE]
> 원할 경우 .csproj 파일을 직접 편집할 수 있습니다.

## <a name="how-to-set-a-subpath-under-the-installroot"></a>InstallRoot 아래에 하위 경로를 설정 하는 방법

아래의 하위 경로에를 설치 하려는 경우 속성을 `InstallRoot` 속성 처럼 설정 하 여이 작업을 수행할 수 있습니다 `VsixSubPath` `InstallRoot` . 예를 들어 프로젝트 참조의 출력이 ' [INSTALLDIR] \MSBuild\MyCompany\MySDK\1.0 '에 설치 되도록 하려고 합니다. 속성 디자이너를 사용 하 여이 작업을 쉽게 수행할 수 있습니다.

![하위 경로 설정](media/set-subpath.png)

해당 .csproj 변경 내용은 다음과 같습니다.

```xml
<ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
       <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
       <Name>ClassLibrary1</Name>
       <InstallRoot>MSBuild</InstallRoot>
       <VSIXSubPath>MyCompany\MySDK\1.0</VSIXSubPath>
</ProjectReference>
```

## <a name="extra-information"></a>추가 정보

속성 디자이너 변경 내용은 프로젝트 참조 이상에 적용 됩니다. `InstallRoot` 위에서 설명한 것과 동일한 방법을 사용 하 여 프로젝트 내의 항목에 대 한 메타 데이터도 설정할 수 있습니다.
