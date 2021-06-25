---
title: VSIX 매니페스트 디자이너 | Microsoft Docs
description: VSIX 매니페스트 디자이너에서 Visual Studio 확장에 대한 설치 동작을 설정하는 VSIX 패키지 매니페스트 파일을 수정하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: baea7be60c67f186da2372c4644366b4a1a7a202
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905191"
---
# <a name="vsix-manifest-designer"></a>VSIX 매니페스트 디자이너
Visual Studio 확장에 대한 설치 동작을 설정하는 VSIX 패키지 매니페스트 파일을 수정합니다.

 **VSIX 매니페스트 디자이너는** 기본 VSIX 스키마에 매핑합니다. 스키마의 모든 요소는 디자이너에서 해당 컨트롤을 사용하여 설정할 수 있습니다. 스키마에 대한 자세한 내용은 [VSIX 확장 스키마 2.0 참조 를 참조하세요.](../extensibility/vsix-extension-schema-2-0-reference.md)

 **VSIX 매니페스트 디자이너를** 열려면 **솔루션 탐색기** *source.extension.vsixmanifest* 파일을 찾아 파일을 엽니다. 파일에 유효한 XML이 없으면 매니페스트 디자이너가 열리지 않습니다.

> [!NOTE]
> *source.extension.vsixmanifest* 파일은 패키지를 빌드할 때 *extension.vsixmanifest에* 출력됩니다.

## <a name="uielement-list"></a>UI 요소 목록
 **VSIX 매니페스트 디자이너에는** 스키마의 이러한 최상위 요소에 해당하는 네 개의 섹션이 포함되어 있습니다.

- 메타데이터

- 대상 설치

- 자산

- 종속성

  제목 영역에는 다음 컨트롤이 포함됩니다.

  **제품 이름** 확장 이름을 설명합니다.

  **제품 ID** 이 패키지에 대한 고유 ID 정보를 지정합니다.

  **작성자** 확장 작성자의 이름을 지정합니다.

  **버전** 확장의 버전 번호를 지정합니다.

  **메타데이터** 탭에는 다음 컨트롤이 포함되어 있습니다.

  **설명** 확장 **관리자** 에 표시할 확장에 대한 텍스트 설명을 제공합니다.

  **언어** 매니페스트의 텍스트 데이터에 해당하는 패키지의 기본 언어를 지정합니다. `Language`특성은 리소스 어셈블리(예: en-us, en, fr-fr)에 대한 CLR(공용 언어 런타임) 로케일 코드 규칙을 따릅니다. 기본적으로 값은 중립적입니다. 즉, 패키지는 모든 언어 버전의 Visual Studio 실행됩니다.

  **라이선스** 사용자 라이선스가 포함된 텍스트 파일(있는 경우)을 지정합니다.

  **아이콘** **아이콘이***있는* 경우 확장 관리자 에 표시할 아이콘이 포함된 그래픽 파일( *.png*,.bmp, *.jpeg*, *.ico)을* 지정합니다. 아이콘 이미지는 32x32픽셀이어야 합니다. 그렇지 않은 경우 해당 크기로 크기가 크기가 크기가 됩니다. 아이콘을 지정하지 않으면 **확장 관리자에서** 기본 아이콘을 사용합니다.

  **미리 보기 이미지** 미리 보기 이미지가 *있는* 경우 **확장 관리자에** 표시할 미리 보기 이미지를 포함하는 그래픽 파일(.png, *.bmp*, *.jpeg*, *.ico)을* 지정합니다. 미리 보기 이미지는 200x200픽셀이어야 합니다. 미리 보기 이미지를 지정하지 않으면 **확장 관리자에서** 기본 이미지를 사용합니다.

  **태그** 검색 힌트에 사용할 텍스트 태그를 추가합니다.

  **릴리스 정보** 릴리스 정보가 포함된 파일(*.txt*, *.rtf*)을 지정합니다. 또한 릴리스 메모를 표시하는 웹 사이트의 URL을 사용합니다.

  **시작 가이드** VSIX 패키지의 확장명 또는 콘텐츠를 사용하는 방법에 대한 정보가 포함된 파일(*.txt*, *.rtf*)을 지정합니다. 이 가이드는 확장 설치가 완료되면 표시됩니다. 또한 가이드를 표시하는 웹 사이트의 URL을 사용합니다.

  **추가 정보 URL** 제품에 대한 추가 정보가 포함된 웹 사이트의 URL을 지정합니다.

  **대상 설치 탭에는** 다음 컨트롤이 포함되어 있습니다.

  **설치 유형** **Visual Studio 확장** 및 **확장 SDK를** 대상 설치 유형으로 나열합니다. 옵션은 선택한 형식에 따라 다릅니다.

  **Visual Studio 확장** 패키지를 설치하는 방법과 이 확장을 설치할 수 있는 Visual Studio 제품을 설명하는 **InstallationTarget** 요소를 나열합니다. 각 제품은 이름 및 버전 또는 버전 범위별로 개별적으로 식별됩니다. 제품을 목록에 추가하고 수정하고 삭제할 수 있습니다. 제품의 이름과 버전은 연결된 **InstallationTarget** 요소의 **ID** 및 **버전** 특성에 해당합니다.

  **버전 범위는** [12.0, 14.0]이며 다음 표기사를 사용합니다.

- [ - 최소 버전 포함

- ] - 최대 버전 포함

- ( - 최소 버전 전용

- ) - 최대 버전 전용

- 단일 버전 # - 지정된 버전만

  **확장 SDK** 특정 제품 및 버전으로 범위가 지정되지 않은 전역 설치를 지정합니다. **대상 플랫폼 식별자는** 대상으로 하는 "Windows"와 같은 플랫폼입니다. **대상 플랫폼 버전은** 대상 플랫폼의 버전(예: 8.0)입니다. **SDK 이름** 및 **SDK 버전은** 각각 SDK의 이름 및 버전 번호입니다.

  **이 VSIX는 모든 사용자용으로 설치됩니다(설치 시 권한 상승 필요).** 이 확인란을 선택하면 모든 사용자에 대해 확장이 설치됩니다. 그렇지 않으면 현재 사용자에 대해서만 설치됩니다.

  **이 VSIX는 Windows Installer 설치됩니다.** 이 확인란을 선택하면 *Windows Installer(*.msi파일)에 의해 확장이 설치됩니다. 그렇지 않으면 일반적인 VSIX 패키지(*.vsix* 파일)로 설치됩니다.

  **자산 탭에는** 다음 컨트롤이 포함되어 있습니다.

  **자산 목록** 이 패키지가 표시 하는 확장 또는 콘텐츠 요소를 설명 하는 자산 요소를 나열 합니다. 각 확장명 또는 콘텐츠 요소는 원본, 형식 및 경로별로 별도로 나열됩니다. 확장 및 콘텐츠 요소를 목록에 추가하고 수정하고 삭제할 수 있습니다. 확장 또는 콘텐츠 요소의 형식 및 경로는 `Type` 연결된 요소의 및 `Path` 특성에 해당합니다. `Asset` 다음과 같은 형식이 알려져 있습니다.

- Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  자산을 추가하거나 편집하려면 자산 형식, 자산이 현재 솔루션의 프로젝트인지 파일 시스템의 파일인지 여부 및 프로젝트 이름을 지정해야 합니다. 포함할 폴더의 이름을 지정할 수도 있습니다.

  사용자 고유의 형식을 만들고 고유한 이름을 지정할 수도 있습니다.

  **Dependencies** 탭에는 다음 컨트롤이 포함되어 있습니다.

  **이름, 원본 및 버전 범위** 이 패키지가 종속된 다른 패키지인 이 패키지의 종속성 요소를 나열합니다. 종속성 패키지가 지정된 경우 이 패키지를 설치하기 전에 설치해야 합니다. 그렇지 않으면 이 패키지에서 설치해야 합니다.

  종속성 패키지는 식별자, 이름, 버전 범위, 원본 및 종속성을 확인하는 방법에 의해 지정됩니다. 각 종속성 패키지는 이름, 버전 및 원본별로 별도로 나열됩니다. 종속성 패키지를 목록에 추가, 수정 및 삭제할 수 있습니다.

  식별자는 `ID` 종속성 패키지 메타데이터의 특성과 일치해야 합니다. 원본은 현재 솔루션의 프로젝트, 현재 설치된 확장명 또는 파일일 수 있습니다. **종속성 확인 방법** 설정은 중첩된 패키지의 상대 경로 또는 종속성에 대한 다운로드 위치의 URL일 수 있습니다. ID, 버전 및 종속성 패키지의 확인은 `Id` 연결된 `Version` 요소의 , 및 특성에 `Location` `Dependency` 해당합니다.

## <a name="see-also"></a>참조
- [VSIX 확장 스키마 2.0 참조](../extensibility/vsix-extension-schema-2-0-reference.md)
- [VSIX 패키지의 구조](../extensibility/anatomy-of-a-vsix-package.md)
