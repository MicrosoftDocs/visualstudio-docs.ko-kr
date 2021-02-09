---
title: '&lt;Strings &gt; 요소 (부트스트래퍼) | Microsoft Docs'
description: Strings 요소는 제품 이름, 패키지 이름 및 설치 오류 메시지에 대 한 지역화 된 문자열을 정의 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.NoStringsForCulture
- MSBuild.GenerateBootstrapper.ProductCultureNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Strings> element [bootstrapper]
ms.assetid: d5ea3613-5fc9-4a11-bef3-46a01178bf60
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a2c8cac705f4e6ae8d72f3a2e9bd5ec4c8ed68bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877475"
---
# <a name="ltstringsgt-element-bootstrapper"></a>&lt;Strings &gt; 요소 (부트스트래퍼)
제품 이름, 패키지 이름 및 설치 오류 메시지에 대 한 지역화 된 문자열을 정의 합니다.

## <a name="syntax"></a>구문

```xml
<Strings>
    <String
        Name
    >
    </String>
</Strings>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 요소는 `Strings` 요소의 자식입니다 `Package` . 특성이 없습니다.

## <a name="string"></a>String
 요소는 `String` 요소의 자식입니다 `Strings` . 요소에는 `Strings` 하나 이상의 요소가 있을 수 있습니다 `String` .

 `String` 에는 다음과 같은 특성이 있습니다.

|attribute|Description|
|---------------|-----------------|
|`Name`|필수 사항입니다. 문자열의 이름입니다.|

## <a name="example"></a>예제
 다음 코드 예제에서는 .NET Framework 설치 관리자에 대 한 모든 영어 문자열을 지정 합니다.

```xml
<Strings>
    <String Name="DisplayName">.NET Framework 2.0</String>
    <String Name="Culture">en</String>
    <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>
    <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>
    <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>
    <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>
    <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>
    <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>
    <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>
    <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>
    <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>
    <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>
    <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>
    <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>
</Strings>
```

## <a name="see-also"></a>참고 항목
- [\<Package> 요소](../deployment/package-element-bootstrapper.md)