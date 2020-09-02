---
title: Visual Studio 2017에 대 한 사용자 지정 프로젝트 및 항목 템플릿 업그레이드
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698853"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>사용자 지정 Visual Studio용 프로젝트 및 항목 템플릿 2017 업그레이드

Visual studio 2017부터 Visual Studio는 이전 버전의 Visual Studio와 다른 방식으로 .vsix 또는 .msi에 의해 설치 된 프로젝트 및 항목 템플릿을 검색 합니다. 사용자 지정 프로젝트 또는 항목 템플릿을 사용 하는 확장을 소유한 경우 확장을 업데이트 해야 합니다. 이 문서에서는 수행 해야 하는 작업을 설명 합니다.

이 변경 내용은 Visual Studio 2017에만 적용 됩니다. 이전 버전의 Visual Studio에는 영향을 주지 않습니다.

VSIX 확장의 일부로 프로젝트 또는 항목 템플릿을 만들려면 [사용자 지정 프로젝트 및 항목 템플릿 만들기](../extensibility/creating-custom-project-and-item-templates.md)를 참조 하세요.

## <a name="template-scanning"></a>템플릿 검색

이전 버전의 Visual Studio에서 **devenv/setup** 또는 **devenv/installvstemplates** 는 로컬 디스크를 검색 하 여 프로젝트 및 항목 템플릿을 검색 했습니다. Visual Studio 2017부터 검색은 사용자 수준 위치에 대해서만 수행 됩니다. 기본 사용자 수준 위치는 **%USERPROFILE%\Documents \\<Visual Studio 버전 \> \templates \\ **입니다. 이 위치는 **Project**  >  마법사에서 **템플릿을 자동으로 Visual Studio로 가져오기** 옵션을 선택한 경우 프로젝트**내보내기 템플릿 ...** 명령에 의해 생성 된 템플릿에 사용 됩니다.

사용자가 아닌 다른 위치의 경우 템플릿의 위치 및 기타 특성을 지정 하는 매니페스트 (. vstman) 파일을 포함 해야 합니다. Vstman 파일은 템플릿에 사용 되는 .vstemplate 파일과 함께 생성 됩니다. .Vsix를 사용 하 여 확장을 설치 하는 경우 Visual Studio 2017에서 확장을 다시 컴파일하여이를 수행할 수 있습니다. 그러나 .msi를 사용 하는 경우 수동으로 변경 해야 합니다. 이러한 변경을 수행 하기 위해 수행 해야 하는 작업 목록은을  **사용 하 여 설치 된 확장에 대 한 업그레이드를 참조 하세요. MSI** 는이 페이지의 뒷부분에 있습니다.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>프로젝트 또는 항목 템플릿을 사용 하 여 VSIX 확장을 업데이트 하는 방법

1. Visual Studio 2017에서 솔루션을 엽니다. 코드를 업그레이드 하 라는 메시지가 표시 됩니다. **확인**을 클릭합니다.

2. 업그레이드가 완료 되 면 설치 대상의 버전을 변경 해야 할 수 있습니다. VSIX 프로젝트에서 source.extension.vsixmanifest 파일을 열고 **설치 대상** 탭을 선택 합니다. **버전 범위** 필드가 **[14.0]** 인 경우 **편집** 을 클릭 하 고 Visual Studio 2017를 포함 하도록 변경 합니다. 예를 들어 **[14.0, 15.0]** 로 설정 하 여 visual studio 2015 또는 visual studio 2017에 확장을 설치 하거나 **[15.0]** 로 설정 하 여 visual studio 2017에 설치할 수 있습니다.

3. 코드를 다시 컴파일합니다.

4. Visual Studio를 닫습니다.

5. VSIX를 설치 합니다.

6. 다음을 수행 하 여 업데이트를 테스트할 수 있습니다.

    1. 다음 레지스트리 키를 통해 파일 검색 변경이 활성화 됩니다.

         **reg add hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1/reg: 32**

    2. 키를 추가한 후에는 **devenv/installvstemplates**를 실행 합니다.

    3. Visual Studio를 다시 엽니다. 예상 위치에서 템플릿을 찾아야 합니다.

    > [!NOTE]
    > 레지스트리 키가 있는 경우 Visual Studio 확장성 프로젝트 템플릿을 사용할 수 없습니다. 레지스트리 키를 삭제 하 고 사용 하려면 **devenv/installvstemplates**를 다시 실행 해야 합니다.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>프로젝트 및 항목 템플릿 배포에 대 한 기타 권장 사항

- 압축 템플릿 파일을 사용 하지 마십시오. 압축 된 템플릿 파일은 리소스와 콘텐츠를 검색 하기 위해 압축을 해제 해야 하므로 사용할 문서가 클수록 됩니다. 대신, 템플릿 초기화 속도를 높이기 위해 프로젝트 템플릿과 항목 템플릿을 자체 디렉터리에 개별 파일로 배포 해야 합니다. VSIX 확장의 경우에는 VSIX 파일을 만드는 동안 SDK 빌드 작업에서 압축 된 템플릿의 압축을 자동으로 풉니다.

- 템플릿 검색 중 불필요 한 리소스 어셈블리 로드를 방지 하기 위해 템플릿 이름, 설명, 아이콘 또는 미리 보기에 대해 패키지/리소스 ID 항목을 사용 하지 마십시오. 대신 지역화 된 매니페스트를 사용 하 여 지역화 된 이름 또는 속성을 사용 하는 각 로캘에 대 한 템플릿 항목을 만들 수 있습니다.

- 템플릿을 파일 항목으로 포함 하는 경우 매니페스트 생성에서 예상 된 결과를 제공 하지 않을 수 있습니다. 이 경우 수동으로 생성 된 매니페스트를 VSIX 프로젝트에 추가 해야 합니다.

## <a name="file-changes-in-project-and-item-templates"></a>프로젝트 및 항목 템플릿의 파일 변경 내용
새 파일을 올바르게 만들 수 있도록 Visual Studio 2015 및 Visual Studio 2017 버전 템플릿 파일 간의 차이점을 보여 줍니다.

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

 다음은 VSIX 프로젝트를 다시 작성 한 결과로 생성 된 vstman 파일 (VSIX 프로젝트의 매니페스트 디렉터리에서 찾을 수 있음)입니다.

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

 [서식 데이터](../extensibility/templatedata-element-visual-studio-templates.md) 요소에서 제공 하는 정보는 동일 하 게 유지 됩니다. **\<VSTemplateContainer>** 요소는 연결 된 템플릿의 .vstemplate 파일을 가리킵니다.

 다음은 Visual Studio 2015에서 만든 기본 .vstemplate 파일입니다.

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

 다음은 VSIX 프로젝트를 다시 작성 한 결과로 생성 된 vstman 파일 (VSIX 프로젝트의 매니페스트 디렉터리에서 찾을 수 있음)입니다.

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

 요소가 제공 하는 정보는 **\<TemplateData>** 동일 하 게 유지 됩니다. **\<VSTemplateContainer>** 요소는 연결 된 템플릿의 .vstemplate 파일을 가리킵니다.

 Vstman 파일의 다양 한 요소에 대 한 자세한 내용은 [Visual Studio 템플릿 매니페스트 스키마 참조](../extensibility/visual-studio-template-manifest-schema-reference.md)를 참조 하세요.

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>를 사용 하 여 설치 된 확장을 업그레이드 합니다. I

일부 MSI 기반 확장 프로그램은 다음 디렉터리와 같은 공통 템플릿 위치에 템플릿을 배포 합니다.

- **\<Visual Studio installation directory>\Common7\IDE \\<projecttemplates/ItemTemplates\>**

- **\<Visual Studio installation directory>\Common7\IDE\Extensions \\<ExtensionName \> \\<프로젝트/itemtemplates\>**

확장에서 MSI 기반 배포를 수행 하는 경우 템플릿 매니페스트를 수동으로 생성 하 고 확장 프로그램에 포함 되어 있는지 확인 해야 합니다. 위에 나열 된 vstman 예제와 [Visual Studio 템플릿 매니페스트 스키마 참조](../extensibility/visual-studio-template-manifest-schema-reference.md)를 비교 합니다.

프로젝트 및 항목 템플릿에 대 한 별도의 매니페스트를 만들고 위에 지정 된 대로 루트 템플릿 디렉터리를 가리켜야 합니다. 확장 및 로캘 당 매니페스트 하나를 만듭니다.

## <a name="see-also"></a>추가 정보

- [템플릿 검색 문제 해결](troubleshooting-template-discovery.md)
- [사용자 지정 프로젝트 및 항목 템플릿 만들기](creating-custom-project-and-item-templates.md)
