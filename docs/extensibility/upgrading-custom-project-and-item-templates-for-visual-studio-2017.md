---
title: Visual Studio 2017을 위한 사용자 지정 프로젝트 및 항목 템플릿 업그레이드
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5f807e142b376d05e5a44600e8f6b24ddb3593be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698853"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Visual Studio 2017을 위한 사용자 지정 프로젝트 및 항목 템플릿 업그레이드

Visual Studio 2017에서 시작하여 Visual Studio는 .vsix 또는 .msi가 이전 버전의 Visual Studio와 다른 방식으로 설치한 프로젝트 및 항목 템플릿을 검색합니다. 사용자 지정 프로젝트 또는 항목 템플릿을 사용하는 확장을 소유한 경우 확장을 업데이트해야 합니다. 이 문서에서는 수행해야 하는 작업을 설명합니다.

이 변경 사항은 Visual Studio 2017에만 영향을 줍니다. 이전 버전의 Visual Studio에는 영향을 주지 않습니다.

VSIX 확장의 일부로 프로젝트 또는 항목 템플릿을 만들려면 [사용자 지정 프로젝트 및 항목 템플릿 만들기를](../extensibility/creating-custom-project-and-item-templates.md)참조하십시오.

## <a name="template-scanning"></a>템플릿 스캔

이전 버전의 Visual Studio에서는 **devenv /setup** 또는 **devenv /installvstemplates가** 로컬 디스크를 스캔하여 프로젝트 및 항목 템플릿을 찾았습니다. Visual Studio 2017에서 시작하여 사용자 수준 위치에 대해서만 검색이 수행됩니다. 기본 사용자 수준 위치는 **%USERPROFILE%\문서\\<\>비주얼 스튜디오\\버전 \템플릿입니다.** 이 위치는 **마법사에서** >  **템플릿을 Visual Studio로 자동으로 가져오는** 경우 프로젝트**내보내기 템플릿에서** 생성된 템플릿에 사용됩니다.

다른(사용자가 아닌) 위치의 경우 템플릿의 위치 및 기타 특성을 지정하는 매니페스트(.vstman) 파일을 포함해야 합니다. .vstman 파일은 템플릿에 사용되는 .vstemplate 파일과 함께 생성됩니다. .vsix를 사용하여 확장을 설치하는 경우 Visual Studio 2017에서 확장을 다시 컴파일하여 이 작업을 수행할 수 있습니다. 그러나 .msi를 사용하는 경우 수동으로 변경해야 합니다. 이러한 변경을 수행하려면 **을 사용하여 설치된 확장에 대한 업그레이드를 참조하십시오. MSI는** 이 페이지의 나중에 볼 수 있습니다.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>프로젝트 또는 항목 템플릿으로 VSIX 확장을 업데이트하는 방법

1. Visual Studio 2017에서 솔루션을 엽니다. 코드를 업그레이드하라는 메시지가 표시됩니다. **확인**을 클릭합니다.

2. 업그레이드가 완료되면 설치 대상의 버전을 변경해야 할 수 있습니다. VSIX 프로젝트에서 source.extension.vsixmanifest 파일을 열고 대상 **설치** 탭을 선택합니다. 버전 **범위** 필드가 **[14.0]인**경우 **편집을** 클릭하고 Visual Studio 2017을 포함하도록 변경합니다. 예를 들어 Visual Studio 2015 또는 Visual Studio 2017에 확장을 설치하려면 **[14.0,15.0]으로** 설정하거나 **[15.0]으로** 설정하여 Visual Studio 2017에만 설치할 수 있습니다.

3. 코드를 다시 컴파일합니다.

4. Visual Studio를 닫습니다.

5. VSIX를 설치합니다.

6. 다음을 수행하여 업데이트를 테스트할 수 있습니다.

    1. 파일 검색 변경 사항은 다음 레지스트리 키에 의해 활성화됩니다.

         **reg 추가 hklm\software\microsoft\visualstudio\15.0\VSTemplate /v 비활성화 템플릿 검색 /t REG_DWORD /d 1 /reg:32**

    2. 키를 추가 한 후 **devenv /installvstemplates를 실행합니다.**

    3. 비주얼 스튜디오를 다시 엽니다. 예상 위치에 템플릿을 찾아야 합니다.

    > [!NOTE]
    > 레지스트리 키가 있는 경우 Visual Studio 확장성 프로젝트 템플릿을 사용할 수 없습니다. 레지스트리 키를 삭제해야 하며 **devenv /installvstemplates를**다시 실행해야 합니다.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>프로젝트 및 항목 템플릿 배포를 위한 기타 권장 사항

- 압축된 템플릿 파일을 사용하지 마십시오. 압축된 템플릿 파일은 리소스와 콘텐츠를 검색하기 위해 압축해제해야 하므로 사용하는 데 비용이 많이 듭니다. 대신 템플릿 초기화 속도를 높이기 위해 프로젝트 및 항목 템플릿을 자체 디렉터리 아래에 개별 파일로 배포해야 합니다. VSIX 확장의 경우 SDK 빌드 작업은 VSIX 파일을 만드는 동안 압축이 있는 템플릿의 압축을 자동으로 해제합니다.

- 템플릿 검색 중에 불필요한 리소스 어셈블리 로드를 방지하려면 템플릿 이름, 설명, 아이콘 또는 미리 보기에 패키지/리소스 ID 항목을 사용하지 마십시오. 대신 지역화된 매니페스트를 사용하여 지역화된 이름 또는 속성을 사용하는 각 로캘에 대한 템플릿 항목을 만들 수 있습니다.

- 템플릿을 파일 항목으로 포함하는 경우 매니페스트 생성이 예상된 결과를 제공하지 못할 수 있습니다. 이 경우 VSIX 프로젝트에 수동으로 생성된 매니페스트를 추가해야 합니다.

## <a name="file-changes-in-project-and-item-templates"></a>프로젝트 및 항목 템플릿의 파일 변경 사항
새 파일을 올바르게 만들 수 있도록 Visual Studio 2015와 Visual Studio 2017 버전의 템플릿 파일 간의 차이점을 보여 주실 수 있습니다.

 다음은 Visual Studio 2015에서 만든 기본 프로젝트 .vstemplate 파일입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 다음은 VSIX 프로젝트의 재구성으로 인해 발생한 .vstman 파일(VSIX 프로젝트의 매니페스트 디렉토리에서 찾을 수 있음)입니다.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) 요소에서 제공하는 정보는 동일하게 유지됩니다. VSTemplateContainer>요소는 연결된 템플릿에 대한 .vstemplate 파일을 가리킵니다. ** \<**

 다음은 Visual Studio 2015에서 만든 기본 항목 .vstemplate 파일입니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 다음은 VSIX 프로젝트의 재구성으로 인해 발생한 .vstman 파일(VSIX 프로젝트의 매니페스트 디렉토리에서 찾을 수 있음)입니다.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>
```

 TemplateData>요소에서 제공하는 정보는 동일하게 유지됩니다. ** \<** VSTemplateContainer>요소는 연결된 템플릿에 대한 .vstemplate 파일을 가리킵니다. ** \<**

 .vstman 파일의 다양한 요소에 대한 자세한 내용은 [Visual Studio 템플릿 매니페스트 스키마 참조](../extensibility/visual-studio-template-manifest-schema-reference.md)를 참조하십시오.

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>확장에 대한 업그레이드가 함께 설치되었습니다. Msi

일부 MSI 기반 확장은 다음 디렉터리와 같은 일반적인 템플릿 위치에 템플릿을 배포합니다.

- **\<비주얼 스튜디오 설치 디렉토리>\Common7\IDE\\<프로젝트 템플릿/항목 템플릿\>**

- **\<비주얼 스튜디오 설치 디렉토리>\Common7\IDE\확장\\<확장 이름\> \\<프로젝트/항목 템플릿\>**

확장이 MSI 기반 배포를 수행하는 경우 템플릿 매니페스트를 수동으로 생성하고 확장 설정에 포함되어 있는지 확인해야 합니다. 위에 나열된 .vstman 예제와 [Visual Studio 템플릿 매니페스트 스키마 참조를](../extensibility/visual-studio-template-manifest-schema-reference.md)비교합니다.

프로젝트 및 항목 템플릿에 대해 별도의 매니페스트를 만들고 위에 지정된 루트 템플릿 디렉토리를 가리키야 합니다. 확장 및 로캘당 하나의 매니페스트를 만듭니다.

## <a name="see-also"></a>참조

- [템플릿 검색 문제 해결](troubleshooting-template-discovery.md)
- [사용자 지정 프로젝트 및 항목 템플릿 만들기](creating-custom-project-and-item-templates.md)
