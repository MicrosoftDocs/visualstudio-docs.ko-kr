---
title: 사용자 지정 시작 페이지 배포 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 210b4589c0e2165af537c3fa9129affb06197e9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712236"
---
# <a name="deploy-custom-start-pages"></a>사용자 지정 시작 페이지 배포

VSIX 배포를 사용하거나 대상 컴퓨터의 올바른 위치에 파일을 복사하여 사용자 지정 시작 페이지를 배포할 수 있습니다.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>시작 페이지 프로젝트 템플릿을 사용하여 VSIX 배포

시작 페이지 프로젝트 템플릿을 사용하여 시작 페이지를 만든 다음 프로젝트를 빌드할 때 Visual Studio는 배포할 수 있는 *.vsix* 파일을 만듭니다. *.vsix* 파일에서 시작 페이지를 패키징하면 의도한 대상에 따라 배포할 수 있는 다음과 같은 옵션이 제공됩니다.

- *.vsix* 파일을 네트워크 공유 또는 공용 웹 사이트에 배치할 수 있습니다. 다른 사용자가 파일을 열면 시작 페이지가 자동으로 설치됩니다.

- 사용자가 **확장 관리자를**사용하여 설치할 수 있도록 [Visual Studio 마켓플레이스](https://marketplace.visualstudio.com/) 웹 사이트에 *.vsix* 파일을 업로드할 수 있습니다.

시작 페이지 프로젝트 템플릿은 복사본을 수정하고 원본을 보존할 수 있도록 기본 Visual Studio 시작 페이지의 복사본을 만듭니다.

**확장 관리자를** 사용하거나 웹 사이트에서 다운로드하여 시작 페이지 프로젝트 템플릿을 가져올 수 있습니다.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>시작 페이지 프로젝트 템플릿을 사용하지 않고 VSIX 배포
 VSIX 배포를 성공적으로 진행하려면 VSIX 등록 프로세스 및 **확장 관리자에서**인식하는 폴더에 확장을 설치해야 합니다. 시작 페이지 프로젝트 템플릿은 이미 올바른 폴더를 지정하므로 VSIX 배포에 대한 확장을 패키징할 때마다 폴더를 사용하는 것이 좋습니다. 그러나 템플릿을 사용할 수 없는 경우 사용하지 않고 VSIX 배포를 만들 수 있습니다.

 시작 페이지 프로젝트 템플릿을 사용하지 않고 VSIX 배포를 만들려면 먼저 다음 두 가지 방법 중 하나에서 시작 페이지에 대한 *.vsix* 파일을 만듭니다.

- 빈 VSIX 프로젝트에 사용자 정의 시작 페이지 파일을 추가하여. 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)을 참조하십시오.

- *수동으로 .vsix* 파일을 만듭니다. *.vsix* 파일을 수동으로 만들려면 다음을 수행하십시오.

   1. 새 폴더에 *extension.vsixmanifest* 파일과 *[Content_Types].xml* 파일을 만듭니다. 자세한 내용은 [VSIX 패키지의 해부학을](../extensibility/anatomy-of-a-vsix-package.md)참조하십시오.

   2. Windows 탐색기에서 두 개의 XML 파일이 포함된 폴더를 마우스 오른쪽 단추로 클릭하고 에서 **보내기를**클릭한 다음 압축(압축) 폴더를 클릭합니다. 파일 이름은 패키지를 설치하는 재배포 가능한 파일의 이름인 *Filename.vsix로*결과 *.zip* 파일의 이름을 바꿉니다.

Visual Studio에서 시작 페이지를 인식하려면 `Content Element` VSIX 매니페스트에 `CustomExtension Element` 에 `Type` 설정된 특성이 있는 a가 `"StartPage"`포함되어야 합니다. VSIX 배포를 사용하여 설치한 시작 페이지 확장은 **시작** 옵션 페이지의 **시작 시작 페이지** 목록에 **[설치된 확장]** *확장 이름으로*나타납니다.

시작 페이지 패키지에 어셈블리가 포함된 경우 Visual Studio가 시작될 때 사용할 수 있도록 바인딩 경로 등록을 추가해야 합니다. 이렇게 하려면 패키지에 다음 정보가 포함된 *.pkgdef* 파일이 포함되어 있는지 확인합니다.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>모든 사용자를 위한 VSIX 배포
 기본적으로 VSIX 패키지에 배포된 확장은 현재 사용자에 대해서만 설치됩니다. 모든 사용자 배포를 만들어 대상 컴퓨터의 모든 사용자에 대해 시작 페이지 설치를 만들 수 있습니다.

### <a name="to-create-an-all-users-deployment"></a>모든 사용자 배포를 만들려면

1. 코드 보기에서 *extension.vsixmanifest 파일을 엽니다.*

2. vsix `Identifier` 매니페스트의 요소에서 값이 `AllUsers` 있는 요소를 추가합니다. `true`

    ```
    <AllUsers>true</AllUsers>
    ```

     이렇게 하면 vsix 설치 관리자가 관리자 권한을 묻는 메시지를 표시한 다음 *\Common7\IDE\Extensions에 파일을 설치합니다.*

3. *.pkgdef 파일을 엽니다.*

4. *MyStartPage.xaml이* 시작 페이지가 포함된 *.xaml* 파일의 이름인 다음을 추가하여 HKLM 아래의 기본 시작 페이지를 설정하려면 *.pkgdef를* 수정합니다.

     [$RootKey$\시작 페이지\기본값]

     "우리"="$PackageFolder$\\*MyStartPage.xaml*"

     이렇게 하면 Visual Studio에서 새 시작 페이지 위치를 볼 수 있습니다.

## <a name="file-copy-deployment"></a>파일 복사 배포
 사용자 지정 시작 페이지를 배포하기 위해 *.vsix* 파일을 만들 필요가 없습니다. 대신 태그 및 지원 파일을 사용자의 <em>\StartPages\* 폴더에 직접 복사할 수 있습니다. *Customize Start Page</em> ** **시작** 옵션 페이지의 시작 페이지 목록은 경로와 함께 해당 폴더의 모든 *.xaml* 파일을 나열합니다(예: *%USERPROFILE%\내 문서\비주얼 스튜디오 {버전}\StartPages\\{파일 이름}.xaml)* 시작 페이지에 개인 어셈블리에 대한 참조가 포함된 경우 해당 어셈블리를\* 복사하여 *\Private Assemblies 폴더에 붙여넣아야 합니다.

 *.vsix* 파일에 패키징하지 않고 만든 시작 페이지를 배포하려면 기본 파일 복사 전략(예: 일괄 처리 스크립트 또는 필요한 디렉터리에 파일을 넣을 수 있는 기타 배포 기술)을 사용하는 것이 좋습니다.

### <a name="to-manually-install-a-custom-start-page"></a>사용자 지정 시작 페이지를 수동으로 설치하려면

1. 어셈블리 이외의 지원 파일과 함께 시작 페이지 태그가 포함된 *.xaml* 파일을 복사하여 사용자의 *\StartPages\* 폴더에 붙여넣습니다.

2. 시작 페이지에 어셈블리가 필요한 경우 어셈블리를 복사하여 *.에 붙여넣습니다. {비주얼 스튜디오 설치 폴더}\Common7\IDE\개인 어셈블리\\. \\*

3. **시작** 옵션 페이지의 **시작 페이지 사용자 지정** 목록에서 새 시작 페이지를 선택합니다. 자세한 내용은 [시작 페이지 사용자 지정을](../ide/customizing-the-start-page-for-visual-studio.md)참조하십시오.

## <a name="see-also"></a>참조

- [시작 페이지 사용자 지정](../ide/customizing-the-start-page-for-visual-studio.md)
- [시작 페이지에 사용자 컨트롤 추가](../extensibility/adding-user-control-to-the-start-page.md)
