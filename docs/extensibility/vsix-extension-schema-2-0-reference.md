---
title: VSIX 확장 스키마 2.0 참조 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78e260c62d67afc10fea25d52169c48b64c82f72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697923"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX 확장 스키마 2.0 참조
VSIX 배포 매니페스트 파일은 VSIX 패키지의 콘텐츠를 설명 합니다. 파일 형식은 스키마의 영향을 받습니다. 이 스키마의 버전 2.0에서는 사용자 지정 형식 및 특성을 추가할 수 있습니다.  매니페스트의 스키마를 확장할 수 있습니다. 매니페스트 로더는 인식할 수 없는 XML 요소와 특성을 무시 합니다.

> [!IMPORTANT]
> Visual Studio 2015는 Visual Studio 2010, Visual Studio 2012 또는 Visual Studio 2013 형식으로 VSIX 파일을 로드할 수 있습니다.

## <a name="package-manifest-schema"></a>패키지 매니페스트 스키마
 매니페스트 XML 파일의 루트 요소는 `<PackageManifest>` 입니다. 이 파일에는 `Version` 매니페스트 형식의 버전인 단일 특성이 있습니다. 형식에 대 한 주요 변경 내용이 있으면 버전 형식이 변경 됩니다. 이 문서에서는 `Version` 특성을 version = "2.0"의 값으로 설정 하 여 매니페스트에 지정 된 매니페스트 형식 버전 2.0을 설명 합니다.

### <a name="packagemanifest-element"></a>PackageManifest 요소
 `<PackageManifest>`Root 요소 내에서 다음 요소를 사용할 수 있습니다.

- `<Metadata>` -패키지 자체에 대 한 메타 데이터 및 광고 정보입니다. `Metadata`매니페스트에서는 하나의 요소만 허용 됩니다.

- `<Installation>` -이 섹션에는 설치할 수 있는 응용 프로그램 Sku를 비롯 하 여이 확장 패키지를 설치할 수 있는 방법이 정의 되어 있습니다. 매니페스트에서는 단일 `Installation` 요소만 사용할 수 있습니다. 매니페스트에는 요소가 있어야 합니다 `Installation` . 그렇지 않으면이 패키지가 SKU에 설치 되지 않습니다.

- `<Dependencies>` -이 패키지에 대 한 종속성의 선택적 목록이 여기에 정의 되어 있습니다.

- `<Assets>` -이 섹션은이 패키지에 포함 된 모든 자산을 포함 합니다. 이 섹션이 없으면이 패키지는 콘텐츠를 표시 하지 않습니다.

- `<AnyElement>*` -매니페스트 스키마는 다른 요소를 허용할 만큼 유연 합니다. 매니페스트 로더에서 인식 하지 않는 모든 자식 요소는 확장 관리자 API에서 추가 XmlElement 개체로 노출 됩니다. VSIX 확장은 이러한 자식 요소를 사용 하 여 Visual Studio에서 실행 되는 코드가 런타임에 액세스할 수 있는 매니페스트 파일에 추가 데이터를 정의할 수 있습니다. [VisualStudio. ExtensionManager 요소](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120))를 참조 하세요.

### <a name="metadata-element"></a>Metadata 요소
 이 섹션은 패키지, 해당 id 및 광고 정보에 대 한 메타 데이터입니다. `<Metadata>` 에는 다음 요소가 포함 되어 있습니다.

- `<Identity>` -이 패키지에 대 한 식별 정보를 정의 하 고 다음 특성을 포함 합니다.

  - `Id` -이 특성은 해당 작성자가 선택한 패키지의 고유 ID 여야 합니다. 이 이름은 CLR 형식을 namespaced 하는 것과 같은 방식으로 정규화 해야 합니다. Company.Product.Feature.Name. `Id`특성은 100 자로 제한 됩니다.

  - `Version` -이 패키지의 버전과 해당 콘텐츠를 정의 합니다. 이 특성은 CLR 어셈블리 버전 관리 형식 (1.2.40308.00)을 따릅니다. 버전 번호가 높은 패키지는 패키지에 대 한 업데이트로 간주 되며 설치 된 기존 버전에 설치할 수 있습니다.

  - `Language` -이 특성은 패키지의 기본 언어 이며이 매니페스트의 텍스트 데이터에 해당 합니다. 이 특성은 리소스 어셈블리에 대 한 CLR 로캘 코드 규칙 (예: en-us, en, fr-fr)을 따릅니다. `neutral`모든 버전의 Visual Studio에서 실행 되는 언어 중립적인 확장을 선언 하도록 지정할 수 있습니다. 기본값은 `neutral`입니다.

  - `Publisher` -이 특성은이 패키지의 게시자 (회사 또는 개별 이름)를 식별 합니다. `Publisher`특성은 100 자로 제한 됩니다.

- `<DisplayName>` -이 요소는 확장 관리자 UI에 표시 되는 사용자에 게 친숙 한 패키지 이름을 지정 합니다. `DisplayName`콘텐츠는 50 자로 제한 됩니다.

- `<Description>` -이 선택적 요소는 확장 관리자 UI에 표시 되는 패키지 및 해당 내용에 대 한 간단한 설명입니다. `Description`콘텐츠는 원하는 모든 텍스트를 포함할 수 있지만 1000 자로 제한 됩니다.

- `<MoreInfo>` -이 선택적 요소는이 패키지에 대 한 전체 설명을 포함 하는 온라인 페이지의 URL입니다. 프로토콜을 http로 지정 해야 합니다.

- `<License>` -이 선택적 요소는 패키지에 포함 된 라이선스 파일 (.txt, .rtf)의 상대 경로입니다.

- `<ReleaseNotes>` -이 선택적 요소는 패키지 (.txt, .rtf)에 포함 된 릴리스 정보 파일에 대 한 상대 경로 이거나 릴리스 정보를 표시 하는 웹 사이트의 URL입니다.

- `<Icon>` -이 선택적 요소는 패키지에 포함 된 이미지 파일 (png, bmp, jpeg, ico)의 상대 경로입니다. 아이콘 이미지는 32x32 픽셀 이어야 하며 (또는 해당 크기로 축소 됨) listview UI에 나타납니다. 요소가 지정 되지 않은 경우 `Icon` UI는 기본값을 사용 합니다.

- `<PreviewImage>` -이 선택적 요소는 패키지에 포함 된 이미지 파일 (png, bmp, jpeg)의 상대 경로입니다. 미리 보기 이미지는 픽셀을 200 x 200 하 고 세부 정보 UI에 표시 되어야 합니다. 요소가 지정 되지 않은 경우 `PreviewImage` UI는 기본값을 사용 합니다.

- `<Tags>` -이 선택적 요소는 검색 힌트에 사용 되는 세미콜론으로 구분 된 추가 텍스트 태그를 나열 합니다. `Tags`요소는 100 자로 제한 됩니다.

- `<GettingStartedGuide>` -이 선택적 요소는 HTML 파일의 상대 경로 이거나이 패키지 내에서 확장 또는 콘텐츠를 사용 하는 방법에 대 한 정보가 포함 된 웹 사이트의 URL입니다. 이 가이드는 설치의 일부로 시작 됩니다.

- `<AnyElement>*` -매니페스트 스키마는 다른 요소를 허용할 만큼 유연 합니다. 매니페스트 로더에서 인식 되지 않는 모든 자식 요소는 XmlElement 개체의 목록으로 노출 됩니다. VSIX 확장은 이러한 자식 요소를 사용 하 여 매니페스트 파일에 추가 데이터를 정의 하 고 런타임에 열거할 수 있습니다.

### <a name="installation-element"></a>설치 요소
 이 섹션에서는이 패키지를 설치할 수 있는 방법 및 설치할 수 있는 응용 프로그램 Sku를 정의 합니다. 이 섹션에는 다음과 같은 특성이 포함 되어 있습니다.

- `Experimental` -현재 모든 사용자에 대해 설치 된 확장 프로그램이 있지만 동일한 컴퓨터에서 업데이트 된 버전을 개발 하는 경우이 특성을 true로 설정 합니다. 예를 들어 모든 사용자에 대해 MyExtension 1.0을 설치 했지만 동일한 컴퓨터에서 MyExtension 2.0을 디버깅 하려는 경우 실험적 = "true"를 설정 합니다. 이 특성은 Visual Studio 2015 업데이트 1 이상에서 사용할 수 있습니다.

- `Scope` -이 특성은 "Global" 또는 "제품 확장" 값을 사용할 수 있습니다.

  - "Global"은 설치가 특정 SKU로 한정 되지 않도록 지정 합니다. 예를 들어 확장 SDK를 설치할 때이 값이 사용 됩니다.

  - "제품 확장"은 개별 Visual Studio Sku로 범위가 지정 된 기존 VSIX 확장 (버전 1.0)을 설치 하도록 지정 합니다. 이것은 기본값입니다.

- `AllUsers` -이 선택적 특성은 모든 사용자에 대해이 패키지를 설치할지 여부를 지정 합니다. 기본적으로이 특성은 패키지를 사용자 단위로 지정 하는 false입니다. 이 값을 true로 설정 하면 설치 사용자가 관리 권한 수준으로 승격 하 여 결과 VSIX를 설치 해야 합니다.

- `InstalledByMsi` -이 선택적 특성은이 패키지가 MSI에 의해 설치 되는지 여부를 지정 합니다. MSI에 의해 설치 된 패키지는 Visual Studio 확장 관리자가 아닌 MSI (프로그램 및 기능)에 의해 설치 되 고 관리 됩니다.  기본적으로이 특성은 패키지가 MSI에 의해 설치 되지 않도록 지정 하는 false입니다.

- `SystemComponent` -이 선택적 특성은이 패키지를 시스템 구성 요소로 간주할지 여부를 지정 합니다. 시스템 구성 요소는 확장 관리자 UI에 표시 되지 않으므로 업데이트할 수 없습니다. 기본적으로이 특성은 패키지가 시스템 구성 요소가 아님을 지정 하는 false입니다.

- `AnyAttribute*` - `Installation` 요소는 런타임에 이름-값 쌍 사전으로 노출 되는 개방형 특성 집합을 허용 합니다.

- `<InstallationTarget>` -이 요소는 VSIX 설치 관리자가 패키지를 설치 하는 위치를 제어 합니다. `Scope`특성 값이 "제품 확장" 이면 패키지는 확장에 대 한 가용성을 알리기 위해 해당 콘텐츠의 일부로 매니페스트 파일을 설치 하는 SKU를 대상으로 해야 합니다. `<InstallationTarget>` `Scope` 특성에 명시적 또는 기본값 "제품 확장"이 있는 경우 요소의 특성은 다음과 같습니다.

  - `Id` -이 특성은 패키지를 식별 합니다.  특성은 네임 스페이스 규칙을 따릅니다. Company.Product.Feature.Name. `Id`특성은 영숫자 문자만 포함할 수 있으며 100 자로 제한 됩니다. 예상 값:

    - VisualStudio Atedshell

    - Microsoft.VisualStudio.Pro

    - VisualStudio

    - VisualStudio

    - VisualStudio. VWDExpress

    - VisualStudio. Vpdexpress.exe

    - VisualStudio.

    - VisualStudio

    - 내 셸. 앱

  - `Version` -이 특성은이 SKU의 최소 및 최대 지원 버전을 포함 하는 버전 범위를 지정 합니다. 패키지에서 지 원하는 Sku 버전을 자세히 확인할 수 있습니다. 버전 범위 표기법은 [10.0-11.0]입니다. 여기서

    - [-최소 버전 포함.

    - ]-최대 버전 포함.

    - (-최소 버전 제외.

    - )-최대 버전 전용입니다.

    - 단일 버전 #-지정 된 버전에만 해당 합니다.

    > [!IMPORTANT]
    > VSIX 스키마 버전 2.0는 Visual Studio 2012에서 도입 되었습니다. 이 스키마를 사용 하려면 컴퓨터에 Visual Studio 2012 이상이 설치 되어 있어야 하 고 해당 제품의 일부인 VSIXInstaller.exe를 사용 해야 합니다. Visual Studio 2012 이상 VSIXInstaller를 사용 하 여 이전 버전의 Visual Studio를 대상으로 지정할 수 있지만 이후 버전의 설치 관리자를 사용 하는 경우에만 사용할 수 있습니다.

    Visual Studio 2017 버전 번호는 [Visual studio 빌드 번호 및 릴리스 날짜](../install/visual-studio-build-numbers-and-release-dates.md)에서 찾을 수 있습니다.

    Visual Studio 2017 릴리스에 대 한 버전을 표현 하는 경우 부 버전은 항상 **0**이어야 합니다. 예를 들어 Visual Studio 2017 버전 15.3.26730.0는 [15.0.26730.0, 16.0)로 표현 되어야 합니다. Visual Studio 2017 이상 버전 번호에만 필요 합니다.

  - `AnyAttribute*` - `<InstallationTarget>` 요소는 런타임에 노출 되는 개방형 특성 집합을 이름-값 쌍 사전으로 허용 합니다.

### <a name="dependencies-element"></a>종속성 요소
 이 요소는이 패키지가 선언 하는 종속성 목록을 포함 합니다. 종속성을 지정 하는 경우 해당 패키지 (로 식별 됨 `Id` )가 이전에 설치 되어 있어야 합니다.

- `<Dependency>` 요소-이 자식 요소에는 다음과 같은 특성이 있습니다.

  - `Id` -이 특성은 종속 패키지의 고유 ID 여야 합니다. 이 id 값은 `<Metadata><Identity>Id` 이 패키지가 종속 된 패키지의 특성과 일치 해야 합니다. `Id`특성은 네임 스페이스 규칙을 따릅니다. Company.Product.Feature.Name. 특성은 영숫자 문자만 포함할 수 있으며 100 자로 제한 됩니다.

  - `Version` -이 특성은이 SKU의 최소 및 최대 지원 버전을 포함 하는 버전 범위를 지정 합니다. 패키지에서 지 원하는 Sku 버전을 자세히 확인할 수 있습니다. 버전 범위 표기법은 [12.0, 13.0]입니다. 여기서는 다음과 같습니다.

    - [-최소 버전 포함.

    - ]-최대 버전 포함.

    - (-최소 버전 제외.

    - )-최대 버전 전용입니다.

    - 단일 버전 #-지정 된 버전에만 해당 합니다.

  - `DisplayName` -이 특성은 대화 상자 및 오류 메시지와 같은 UI 요소에 사용 되는 종속 패키지의 표시 이름입니다. 종속 패키지를 MSI로 설치 하지 않는 한이 특성은 선택 사항입니다.

  - `Location` -이 선택적 특성은이 VSIX 내에서 중첩 된 VSIX 패키지에 대 한 상대 경로를 지정 하거나 종속성의 다운로드 위치에 대 한 URL을 지정 합니다. 이 특성은 사용자가 필수 구성 요소 패키지를 찾는 데 사용 됩니다.

  - `AnyAttribute*` - `Dependency` 요소는 런타임에 이름-값 쌍 사전으로 노출 되는 개방형 특성 집합을 허용 합니다.

### <a name="assets-element"></a>자산 요소
 이 요소에는 `<Asset>` 이 패키지에 표시 되는 각 확장 프로그램 또는 콘텐츠 요소에 대 한 태그 목록이 포함 되어 있습니다.

- `<Asset>` -이 요소에는 다음과 같은 특성 및 요소가 포함 됩니다.

  - `Type` -이 요소가 나타내는 확장 또는 콘텐츠의 형식입니다. 각 `<Asset>` 요소에는 단일가 있어야 `Type` 하지만 여러 `<Asset>` 요소가 같을 수도 있습니다 `Type` . 이 특성은 네임 스페이스 규칙에 따라 정규화 된 이름으로 표시 되어야 합니다. 알려진 형식은 다음과 같습니다.

    1. VisualStudio. VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. VisualStudio. ToolboxControl

    4. VisualStudio

    5. VisualStudio

    6. VisualStudio

    7. VisualStudio

       사용자 고유의 형식을 만들고 고유한 이름을 지정할 수 있습니다. Visual Studio 내에서 런타임에 코드는 확장 관리자 API를 통해 이러한 사용자 지정 형식을 열거 하 고 액세스할 수 있습니다.

  - `Path` -자산을 포함 하는 패키지 내의 파일 또는 폴더에 대 한 상대 경로입니다.

  - `TargetVersion` -지정 된 자산이 적용 되는 버전 범위입니다. 여러 버전의 자산을 다른 버전의 Visual Studio에 전달 하는 데 사용 됩니다. 적용 하려면 Visual Studio 2017.3 이상이 필요 합니다.

  - `AnyAttribute*` -런타임에 이름-값 쌍 사전으로 노출 되는 개방형 특성 집합입니다.

    `<AnyElement>*` -시작 태그와 끝 태그 사이에 구조화 된 콘텐츠를 사용할 수 `<Asset>` 있습니다. 모든 요소는 XmlElement 개체의 목록으로 노출 됩니다. VSIX 확장은 매니페스트 파일에서 구조화 된 유형별 메타 데이터를 정의 하 고 런타임에 열거할 수 있습니다.

### <a name="sample-manifest"></a>샘플 매니페스트

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
  <Metadata>
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />
    <DisplayName>Test Package</DisplayName>
    <Description>Information about my package</Description>
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>
    <License>eula.rtf</License>
    <ReleaseNotes>notes.txt</ReleaseNotes>
    <Icon>Images\icon.png</Icon>
    <PreviewImage>Images\preview.png</PreviewImage>
  </Metadata>
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>추가 정보

- [Visual Studio 확장 제공](../extensibility/shipping-visual-studio-extensions.md)
