---
title: SignFile 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 319afb810ba755d0201d3edaebcb06a493b59047
ms.sourcegitcommit: c2b3bf0de44cd379fd1ad5110385021d0ec950ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301449"
---
# <a name="signfile-task"></a>SignFile 작업

지정된 인증서를 사용하여 지정한 파일에 서명을 합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `SignFile` 작업의 매개 변수에 대해 설명합니다.

 SHA-256 인증서는 .NET 4.5 이상이 설치된 컴퓨터에서만 사용할 수 있습니다.

> [!WARNING]
> Visual Studio 2013 업데이트 3부터는 이 작업에 새 시그니처가 포함되어 파일의 대상 프레임워크 버전을 지정할 수 있습니다. MSBuild 프로세스에서는 대상 프레임워크가 .NET 4.5 이상일 때만 SHA-256 해시를 사용하므로 가능하면 항상 새 시그니처를 사용하는 것이 좋습니다. 대상 프레임워크가 .NET 4.0 이하이면 SHA-256 해시는 사용되지 않습니다.

|매개 변수|설명|
|---------------|-----------------|
|`CertificateThumbprint`|필수 `String` 매개 변수입니다.<br /><br /> 서명에 사용할 인증서를 지정합니다. 이 인증서는 현재 사용자의 개인 저장소에 있어야 합니다.|
|`SigningTarget`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> .exe 또는 .dll 형식의 인증서를 사용하여 서명할 파일을 지정합니다.|
|`TimestampUrl`|선택적 `String` 매개 변수입니다.<br /><br /> 타임스탬프 서버의 URL을 지정합니다.|
|`TargetFrameworkVersion`|대상에 대해 사용되는 .NET Framework 버전입니다.|

## <a name="remarks"></a>설명

 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [Task 기본 클래스](../msbuild/task-base-class.md)를 참조하세요.

## <a name="example"></a>예제

 다음 예제에서는 `SignFile` 작업을 통해 `FilesToSign` 속성으로 지정된 인증서를 사용하여 `CertificateThumbprint` 항목 컬렉션에 지정된 파일에 서명을 합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <FileToSign Include="File.exe" />
    </ItemGroup>
    <PropertyGroup>
        <Certificate>Cert.cer</Certificate>
    </PropertyGroup>
    <Target Name="Sign">
        <SignFile
            CertificateThumbprint="$(CertificateThumbprint)"
            SigningTarget="@(FileToSign)"
            TargetFrameworkVersion="v4.5" />
    </Target>
</Project>
```

> [!NOTE]
> 인증서 지문은 인증서의 SHA-1 해시입니다. 자세한 내용은 [신뢰할 수 있는 루트 CA 인증서의 SHA-1 해시 얻기](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\))를 참조하세요. 인증서 세부 정보에서 지문을 복사하여 붙여넣는 경우 추가(3F) 보이지 않는 문자를 포함하지 마세요. 이로 인해 `SignFile`이 인증서를 찾지 못할 수 있습니다.

## <a name="see-also"></a>참조

- [작업 참조](../msbuild/msbuild-task-reference.md)
- [작업](../msbuild/msbuild-tasks.md)