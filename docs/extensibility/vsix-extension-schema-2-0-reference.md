---
title: VSIX 확장 스키마 2.0 참조 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697923"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX 확장 스키마 2.0 참조
VSIX 배포 매니페스트 파일은 VSIX 패키지의 내용을 설명합니다. 파일 형식은 스키마에 의해 제어됩니다. 이 스키마의 버전 2.0은 사용자 지정 형식 및 특성추가를 지원합니다.  매니페스트의 스키마는 확장 할 수 있습니다. 매니페스트 로더는 이해하지 못하는 XML 요소와 특성을 무시합니다.

> [!IMPORTANT]
> Visual Studio 2015는 Visual Studio 2010, Visual Studio 2012 또는 Visual Studio 2013 형식으로 VSIX 파일을 로드할 수 있습니다.

## <a name="package-manifest-schema"></a>패키지 매니페스트 스키마
 매니페스트 XML 파일의 루트 `<PackageManifest>`요소는 . 매니페스트 형식의 `Version`버전인 단일 특성이 있습니다. 형식이 크게 변경되면 버전 형식이 변경됩니다. 이 문서에서는 매니페스트 형식 버전 2.0에 대해 설명하며, 이 형식은 버전="2.0"의 값으로 `Version` 특성을 설정하여 매니페스트에 지정됩니다.

### <a name="packagemanifest-element"></a>패키지 매니페스트 요소
 `<PackageManifest>` 루트 요소 내에서 다음 요소를 사용할 수 있습니다.

- `<Metadata>`- 패키지 자체에 대한 메타데이터 및 광고 정보. 매니페스트에는 하나의 `Metadata` 요소만 허용됩니다.

- `<Installation>`- 이 섹션에서는 설치할 수 있는 응용 프로그램 SKU를 포함하여 이 확장 패키지를 설치할 수 있는 방법을 정의합니다. 매니페스트에는 `Installation` 단일 요소만 허용됩니다. 매니페스트에는 `Installation` 요소가 있어야 하거나 이 패키지는 SKU에 설치되지 않습니다.

- `<Dependencies>`- 이 패키지에 대한 선택적 종속성 목록이 여기에 정의되어 있습니다.

- `<Assets>`- 이 섹션에는 이 패키지에 포함된 모든 에셋이 포함되어 있습니다. 이 섹션이 없으면 이 패키지에 콘텐츠가 표시되지 않습니다.

- `<AnyElement>*`- 매니페스트 스키마는 다른 요소를 허용할 만큼 유연합니다. 매니페스트 로더에서 인식하지 못하는 모든 자식 요소는 확장 관리자 API에 추가 XmlElement 개체로 노출됩니다. 이러한 자식 요소를 사용하여 VSIX 확장은 Visual Studio에서 실행되는 코드가 런타임에 액세스할 수 있는 매니페스트 파일의 추가 데이터를 정의할 수 있습니다. [참조 마이크로소프트.비주얼 스튜디오.확장관리자.IExtension.Additional요소](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>메타데이터 요소
 이 섹션은 패키지, ID 및 광고 정보에 대한 메타데이터입니다. `<Metadata>`다음 요소가 포함되어 있습니다.

- `<Identity>`- 이 패키지의 식별 정보를 정의하고 다음 특성을 포함합니다.

  - `Id`- 이 특성은 작성자가 선택한 패키지의 고유 ID여야 합니다. 이름은 CLR 형식이 네임스페이스(Company.Product.Feature.Name)와 동일한 방식으로 정규화되어야 합니다. 특성은 `Id` 100자로 제한됩니다.

  - `Version`- 이 패키지의 버전과 그 내용을 정의합니다. 이 특성은 CLR 어셈블리 버전 지정 형식인 Major.Minor.Build.Revision(1.2.40308.00)을 따릅니다. 버전 번호가 높은 패키지는 패키지에 대한 업데이트로 간주되며 기존 설치된 버전 위에 설치할 수 있습니다.

  - `Language`- 이 특성은 패키지의 기본 언어이며 이 매니페스트의 텍스트 데이터에 해당합니다. 이 특성은 리소스 어셈블리에 대한 CLR 로캘 코드 규칙을 따릅니다. 모든 버전의 Visual Studio에서 실행되는 언어 중립 확장을 선언하도록 지정할 `neutral` 수 있습니다. 기본값은 `neutral`입니다.

  - `Publisher`- 이 특성은 회사 또는 개별 이름 중 하나이 패키지의 게시자를 식별합니다. 특성은 `Publisher` 100자로 제한됩니다.

- `<DisplayName>`- 이 요소는 확장 관리자 UI에 표시되는 사용자 친화적인 패키지 이름을 지정합니다. 콘텐츠는 `DisplayName` 50자로 제한됩니다.

- `<Description>`- 이 선택적 요소는 확장 관리자 UI에 표시되는 패키지 및 해당 내용에 대한 간략한 설명입니다. 콘텐츠에 `Description` 원하는 텍스트가 포함될 수 있지만 1000자로 제한됩니다.

- `<MoreInfo>`- 이 선택적 요소는 이 패키지에 대한 전체 설명이 포함된 온라인 페이지의 URL입니다. 프로토콜은 http로 지정해야 합니다.

- `<License>`- 이 선택적 요소는 패키지에 포함된 라이센스 파일(.txt, .rtf)에 대한 상대 경로입니다.

- `<ReleaseNotes>`- 이 선택적 요소는 패키지에 포함된 릴리즈 노트 파일(.txt, .rtf)에 대한 상대 경로이거나 릴리스 메모를 표시하는 웹 사이트의 URL입니다.

- `<Icon>`-이 선택적 요소는 패키지에 포함된 이미지 파일(png, bmp, jpeg, ico)에 대한 상대 경로입니다. 아이콘 이미지는 32x32 픽셀이어야 하며(또는 해당 크기로 축소됨) listview UI에 나타납니다. 요소를 `Icon` 지정하지 않으면 UI에서 기본값을 사용합니다.

- `<PreviewImage>`-이 선택적 요소는 패키지에 포함된 이미지 파일(png, bmp, jpeg)에 대한 상대 경로입니다. 미리 보기 이미지는 200x200 픽셀이어야 하며 세부 정보 UI에 표시됩니다. 요소를 `PreviewImage` 지정하지 않으면 UI에서 기본값을 사용합니다.

- `<Tags>`- 이 선택적 요소에는 검색 힌트에 사용되는 추가 세미콜론 구분 텍스트 태그가 나열됩니다. `Tags` 요소는 100자로 제한됩니다.

- `<GettingStartedGuide>`- 이 선택적 요소는 HTML 파일에 대한 상대 경로 또는 이 패키지 내의 확장자 또는 콘텐츠를 사용하는 방법에 대한 정보가 포함된 웹 사이트의 URL입니다. 이 가이드는 설치의 일부로 시작됩니다.

- `<AnyElement>*`- 매니페스트 스키마는 다른 요소를 허용할 만큼 유연합니다. 매니페스트 로더에서 인식되지 않는 모든 자식 요소는 XmlElement 개체 목록으로 노출됩니다. 이러한 자식 요소를 사용하여 VSIX 확장은 매니페스트 파일의 추가 데이터를 정의하고 런타임에 열거할 수 있습니다.

### <a name="installation-element"></a>설치 요소
 이 섹션에서는 이 패키지를 설치할 수 있는 방법과 설치할 수 있는 응용 프로그램 SKU를 정의합니다. 이 섹션에는 다음 특성이 포함되어 있습니다.

- `Experimental`- 현재 모든 사용자에 대해 설치되어 있지만 동일한 컴퓨터에서 업데이트된 버전을 개발하는 확장이 있는 경우 이 특성을 true로 설정합니다. 예를 들어 모든 사용자에 대해 MyExtension 1.0을 설치했지만 동일한 컴퓨터에서 MyExtension 2.0을 디버깅하려는 경우 Experimental="true"를 설정합니다. 이 특성은 Visual Studio 2015 업데이트 1 이상에서 사용할 수 있습니다.

- `Scope`- 이 특성은 값 "글로벌"또는 "제품 확장"을 취할 수 있습니다 :

  - "전역"은 설치가 특정 SKU로 범위가 지정되지 않도록 지정합니다. 예를 들어 이 값은 확장 SDK를 설치할 때 사용됩니다.

  - "ProductExtension"은 개별 Visual Studio SKU로 범위가 지정된 기존 VSIX 확장(버전 1.0)이 설치되도록 지정합니다. 기본값입니다.

- `AllUsers`- 이 선택적 특성은 이 패키지가 모든 사용자에게 설치될지 여부를 지정합니다. 기본적으로 이 특성은 false이며 패키지가 사용자별로 지정됩니다. 이 값을 true로 설정하면 설치 사용자는 관리 권한 수준으로 상승하여 결과 VSIX를 설치해야 합니다.

- `InstalledByMsi`- 이 선택적 특성은 이 패키지가 MSI에 의해 설치되는지 여부를 지정합니다. MSI에 의해 설치된 패키지는 설치 및 MSI에 의해 관리 (프로그램 및 기능) 및 비주얼 스튜디오 확장 관리자에 의해.  기본적으로 이 특성은 false이며 MSI에서 패키지가 설치되지 않도록 지정합니다.

- `SystemComponent`- 이 선택적 특성은 이 패키지를 시스템 구성 요소로 간주해야 하는지 여부를 지정합니다. 시스템 구성 요소는 확장 관리자 UI에 표시되지 않으며 업데이트할 수 없습니다. 기본적으로 이 특성은 false이며 패키지가 시스템 구성 요소가 아님을 지정합니다.

- `AnyAttribute*`- `Installation` 요소는 런타임에 이름 값 쌍 사전으로 노출되는 개방형 특성 집합을 허용합니다.

- `<InstallationTarget>`-이 요소는 VSIX 설치 프로그램이 패키지를 설치하는 위치를 제어합니다. `Scope` 특성값이 "ProductExtension"인 경우 패키지는 확장에 대한 가용성을 알리기 위해 매니페스트 파일을 내용의 일부로 설치한 SKU를 대상으로 해야 합니다. 특성에 `<InstallationTarget>` 명시적 또는 기본값 "ProductExtension"이 있는 경우 `Scope` 요소에는 다음 특성이 있습니다.

  - `Id`- 이 특성은 패키지를 식별합니다.  특성은 네임스페이스 규칙인 Company.Product.Feature.Name 따릅니다. 속성은 `Id` 숫자 문자만 포함할 수 있으며 100자로 제한됩니다. 예상 값:

    - 마이크로소프트.비주얼스튜디오.통합쉘

    - Microsoft.VisualStudio.Pro

    - 마이크로소프트.비주얼 스튜디오.프리미엄

    - 마이크로소프트.비주얼 스튜디오.얼티밋

    - 마이크로소프트.비주얼스튜디오.폭스바겐드익스프레스

    - 마이크로소프트.비주얼스튜디오.VPD익스프레스

    - 마이크로소프트.비주얼스튜디오.VS윈익스프레스

    - 마이크로소프트.비주얼 스튜디오.VSLS

    - 내.쉘.앱

  - `Version`- 이 특성은 이 SKU의 최소 및 최대 지원 버전이 있는 버전 범위를 지정합니다. 패키지는 지원하는 SCO의 버전을 자세히 설명할 수 있습니다. 버전 범위 표기는 [10.0 - 11.0]이며, 여기서

    - [ - 최소 버전 포함.

    - ] - 최대 버전 포함.

    - ( - 최소 버전 독점.

    - ) - 최대 버전 독점.

    - 단일 버전 번호 - 지정된 버전만.

    > [!IMPORTANT]
    > VSIX 스키마의 버전 2.0은 비주얼 스튜디오 2012에서 소개되었습니다. 이 스키마를 사용하려면 Visual Studio 2012 이상이 컴퓨터에 설치되어 있어야 하며 해당 제품의 일부인 VSIXInstaller.exe를 사용해야 합니다. 이전 버전의 Visual Studio를 Visual Studio 2012 이상 VSIXInstaller를 사용하여 대상으로 지정할 수 있지만 이후 버전의 설치 관리자를 통해서만 대상을 지정할 수 있습니다.

    Visual Studio 2017 버전 번호는 [Visual Studio 빌드 번호 및 릴리스 날짜에서](../install/visual-studio-build-numbers-and-release-dates.md)찾을 수 있습니다.

    Visual Studio 2017 릴리스의 버전을 표현할 때 부 버전은 항상 **0이어야**합니다. 예를 들어 Visual Studio 2017 버전 15.3.26730.0은 [15.0.26730.0,16.0)로 표현되어야 합니다. 이는 Visual Studio 2017 및 이후 버전 번호에만 필요합니다.

  - `AnyAttribute*`- `<InstallationTarget>` 요소는 이름 값 쌍 사전으로 런타임에 노출되는 개방형 특성 집합을 허용합니다.

### <a name="dependencies-element"></a>종속성 요소
 이 요소에는 이 패키지가 선언하는 종속성 목록이 포함되어 있습니다. 종속성을 지정하면 해당 패키지(종속 `Id`패키지로 식별)가 이전에 설치되어 있어야 합니다.

- `<Dependency>`요소 - 이 자식 요소에는 다음과 같은 속성이 있습니다.

  - `Id`- 이 특성은 종속 패키지의 고유 ID여야 합니다. 이 ID 값은 `<Metadata><Identity>Id` 이 패키지가 종속된 패키지의 특성과 일치해야 합니다. 특성은 `Id` 네임스페이스 규칙인 Company.Product.Feature.Name 따릅니다. 속성은 숫자 문자만 포함할 수 있으며 100자로 제한됩니다.

  - `Version`- 이 특성은 이 SKU의 최소 및 최대 지원 버전이 있는 버전 범위를 지정합니다. 패키지는 지원하는 SCO의 버전을 자세히 설명할 수 있습니다. 버전 범위 표기는 [12.0, 13.0]이며 다음과 같은 위치입니다.

    - [ - 최소 버전 포함.

    - ] - 최대 버전 포함.

    - ( - 최소 버전 독점.

    - ) - 최대 버전 독점.

    - 단일 버전 번호 - 지정된 버전만.

  - `DisplayName`- 이 특성은 대화 상자 및 오류 메시지와 같은 UI 요소에 사용되는 종속 패키지의 표시 이름입니다. MSI에서 종속 패키지를 설치하지 않는 한 이 특성은 선택 사항입니다.

  - `Location`- 이 선택적 특성은 이 VSIX 내의 상대 경로를 중첩된 VSIX 패키지로 지정하거나 종속성에 대한 다운로드 위치에 대한 URL을 지정합니다. 이 특성은 사용자가 필수 구성 조건 패키지를 찾는 데 사용됩니다.

  - `AnyAttribute*`- `Dependency` 요소는 런타임에 이름 값 쌍 사전으로 노출되는 개방형 특성 집합을 허용합니다.

### <a name="assets-element"></a>자산 요소
 이 요소에는 이 `<Asset>` 패키지에 의해 표시되는 각 확장 또는 콘텐츠 요소에 대한 태그 목록이 포함되어 있습니다.

- `<Asset>`-이 요소에는 다음과 같은 속성과 요소가 포함되어 있습니다.

  - `Type`- 이 요소로 표시되는 확장 또는 콘텐츠의 유형입니다. 각 `<Asset>` 요소에는 단일 `Type`요소가 `<Asset>` 있어야 하지만 여러 `Type`요소에는 동일할 수 있습니다. 이 특성은 네임스페이스 규칙에 따라 정규화된 이름으로 표시되어야 합니다. 알려진 유형은 다음과 같습니다.

    1. 마이크로소프트.비주얼 스튜디오.vs패키지

    2. Microsoft.VisualStudio.MefComponent

    3. 마이크로소프트.비주얼 스튜디오.툴박스컨트롤

    4. 마이크로소프트.비주얼 스튜디오.샘플

    5. 마이크로소프트.비주얼 스튜디오.프로젝트 템플릿

    6. 마이크로소프트.비주얼 스튜디오.항목 템플릿

    7. 마이크로소프트.비주얼 스튜디오.어셈블리

       고유한 형식을 만들고 고유한 이름을 지정할 수 있습니다. Visual Studio 내에서 런타임시 코드는 확장 관리자 API를 통해 이러한 사용자 지정 형식을 열거하고 액세스할 수 있습니다.

  - `Path`- 에셋을 포함하는 패키지 내의 파일 또는 폴더에 대한 상대 경로입니다.

  - `TargetVersion`- 지정된 자산이 적용되는 버전 범위입니다. 여러 버전의 에셋을 다른 버전의 Visual Studio로 배송하는 데 사용됩니다. 효과를 얻으려면 Visual Studio 2017.3 이상이 필요합니다.

  - `AnyAttribute*`- 이름-값 쌍 사전으로 런타임에 노출되는 개방형 특성 집합입니다.

    `<AnyElement>*`- 모든 구조화 된 `<Asset>` 콘텐츠는 시작과 끝 태그 사이에 허용됩니다. 모든 요소는 XmlElement 개체 목록으로 노출됩니다. VSIX 확장은 매니페스트 파일에서 구조화 된 형식 별 메타데이터를 정의하고 런타임에 열거 할 수 있습니다.

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

## <a name="see-also"></a>참조

- [선박 비주얼 스튜디오 확장](../extensibility/shipping-visual-studio-extensions.md)
