---
title: XmlPoke 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f44ce4736900fde35716ca3ec9dabb2d55c6df51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588384"
---
# <a name="xmlpoke-task"></a>XmlPoke 작업

XML 파일로의 XPath 쿼리에 의해 지정된 대로 값을 반환합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `XmlPoke` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|Description|
|---------------|-----------------|
|`Namespaces`|선택적 `String` 매개 변수입니다.<br /><br /> XPath 쿼리 접두사에 대한 네임스페이스를 지정합니다. `Namespaces`는 `Namespace` 및 `Prefix` 특성을 포함한 `Uri` 요소로 이루어진 XML 코드 조각입니다. `Prefix` 특성은 `Uri` 특성에 지정된 네임스페이스와 연결할 접두사를 지정합니다. 빈 `Prefix`를 사용하지 않습니다.|
|`Query`|선택적 `String` 매개 변수입니다.<br /><br /> XPath 쿼리를 지정합니다.|
|`Value`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> 지정된 경로에 삽입할 값을 지정합니다.|
|`XmlInputPath`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> XML 입력을 파일 경로로 지정합니다.|

## <a name="remarks"></a>설명

 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Tasks.TaskExtension> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Utilities.Task> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.

## <a name="example"></a>예제

수정할 sample.xml은 다음과 같습니다.

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

이 예제에서 `/Package/mp:PhoneIdentity/PhonePublisherId`를 수정하려는 경우 다음을 사용합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

여기에서 `dn`은 기본 네임스페이스의 인위적인 네임스페이스 접두사로 사용됩니다.

## <a name="see-also"></a>참고 항목

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
