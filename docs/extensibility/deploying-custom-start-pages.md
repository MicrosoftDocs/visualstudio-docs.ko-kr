---
title: 사용자 지정 시작 페이지 배포 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712236"
---
# <a name="deploy-custom-start-pages"></a>사용자 지정 시작 페이지 배포

VSIX 배포를 사용 하거나 파일을 대상 컴퓨터의 올바른 위치로 복사 하 여 사용자 지정 시작 페이지를 배포할 수 있습니다.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>시작 페이지 프로젝트 템플릿을 사용 하 여 VSIX 배포

시작 페이지 프로젝트 템플릿을 사용 하 여 시작 페이지를 만든 다음 프로젝트를 빌드하면 Visual Studio에서 배포할 수 있는 *.vsix* 파일을 만듭니다. *.Vsix* 파일에서 시작 페이지를 패키징하 면 원하는 대상에 따라 배포에 대 한 다음 옵션을 제공 합니다.

- 네트워크 공유 또는 공용 웹 사이트에 *.vsix* 파일을 배치할 수 있습니다. 누군가가 파일을 열면 시작 페이지가 자동으로 설치 됩니다.

- 사용자가 **확장 관리자**를 사용 하 여 설치할 수 있도록 *.vsix* 파일을 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트에 업로드할 수 있습니다.

시작 페이지 프로젝트 템플릿은 기본 Visual Studio 시작 페이지의 복사본을 만들어 복사본을 수정 하 고 원래를 유지할 수 있습니다.

**확장 관리자** 를 사용 하거나 웹 사이트에서 다운로드 하 여 시작 페이지 프로젝트 템플릿을 가져올 수 있습니다.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>시작 페이지 프로젝트 템플릿을 사용 하지 않는 VSIX 배포
 VSIX를 성공적으로 배포 하려면 VSIX 등록 프로세스 및 **확장 관리자**에서 인식 하는 폴더에 확장을 설치 해야 합니다. 시작 페이지 프로젝트 템플릿은 올바른 폴더를 이미 지정 하기 때문에 VSIX 배포용 확장을 패키지할 때마다 사용 하는 것이 좋습니다. 그러나 템플릿을 사용할 수 없는 경우에는 VSIX 배포를 사용 하지 않고 만들 수 있습니다.

 시작 페이지 프로젝트 템플릿을 사용 하지 않고 VSIX 배포를 만들려면 먼저 다음 두 가지 방법 중 하나를 사용 하 여 시작 페이지에 대 한 *.vsix* 파일을 만듭니다.

- 빈 VSIX 프로젝트에 사용자 지정 시작 페이지 파일을 추가 합니다. 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)을 참조하세요.

- *Vsix* 파일을 수동으로 만듭니다. Vsix 파일을 수동으로 만들려면 다음을 수행 *합니다* .

   1. *Source.extension.vsixmanifest* 파일 및 *[Content_Types] .xml* 파일을 새 폴더에 만듭니다. 자세한 내용은 [VSIX 패키지의 분석](../extensibility/anatomy-of-a-vsix-package.md)을 참조 하세요.

   2. Windows 탐색기에서 두 XML 파일이 포함 된 폴더를 마우스 오른쪽 단추로 클릭 하 고 **보내기**를 클릭 한 다음 압축 (Zip) 폴더를 클릭 합니다. 결과로 만들어지는 *.zip* 파일의 이름을 *filename .vsix*로 바꿉니다. 여기서 filename은 패키지를 설치 하는 재배포 가능 파일의 이름입니다.

Visual Studio에서 시작 페이지를 인식 하려면 `Content Element` VSIX 매니페스트의는 `CustomExtension Element` `Type` 특성이로 설정 된를 포함 해야 합니다 `"StartPage"` . VSIX 배포를 사용 하 여 설치한 시작 페이지 확장은 **시작 옵션 페이지** 의 **시작 페이지 사용자 지정** 목록에 **[설치 된 확장]** *확장 이름*으로 표시 됩니다.

시작 페이지 패키지에 어셈블리를 포함 하는 경우 Visual Studio가 시작 될 때 사용할 수 있도록 바인딩 경로 등록을 추가 해야 합니다. 이렇게 하려면 패키지에 다음 정보가 포함 된 *.pkgdef* 파일이 포함 되어 있는지 확인 합니다.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>모든 사용자에 대 한 VSIX 배포
 기본적으로 VSIX 패키지에 배포 된 확장은 현재 사용자에 대해서만 설치 합니다. 모든 사용자 배포를 만들어 대상 컴퓨터의 모든 사용자에 대해 시작 페이지를 설치 하도록 만들 수 있습니다.

### <a name="to-create-an-all-users-deployment"></a>모든 사용자 배포를 만들려면

1. 코드 뷰에서 *source.extension.vsixmanifest* 파일을 엽니다.

2. `Identifier`Vsix 매니페스트의 요소에서 값이 인 요소를 추가 `AllUsers` `true` 합니다.

    ```
    <AllUsers>true</AllUsers>
    ```

     이렇게 하면 vsix 설치 관리자에서 관리자 권한을 묻는 메시지가 표시 된 다음 *\Common7\IDE\Extensions*에 파일을 설치 합니다.

3. *.Pkgdef* 파일을 엽니다.

4. 다음을 추가 하 여 HKLM에서 기본 시작 페이지를 설정 하도록 *. .pkgdef* 를 수정 합니다. 여기서 *mystartpage. Xaml* 은 시작 페이지를 포함 하는 *.xaml* 파일의 이름입니다.

     [$RootKey $ \StartPage\Default]

     "Uri" = "$PackageFolder $ \\ *mystartpage .xaml*"

     그러면 Visual Studio에서 새 시작 페이지 위치를 확인 합니다.

## <a name="file-copy-deployment"></a>파일 복사 배포
 사용자 지정 시작 페이지를 배포 하는 *.vsix* 파일을 만들 필요는 없습니다. 대신 사용자의 <em>\Startpages 폴더에 태그 및 지원 파일을 직접 복사할 수 있습니다 \* . 시작 옵션 페이지의 **시작 페이지 사용자 지정</em> * 목록에는 해당 폴더에 있는 모든 *.xaml* 파일 및 경로 (예: *%USERPROFILE%\My documents\visual Studio {version} \startpages \\ {file Name} .xaml*)가 나열 됩니다. **Startup** 시작 페이지에 전용 어셈블리에 대 한 참조가 포함 된 경우 해당 파일을 복사 하 여 * \PrivateAssemblies 폴더에 붙여넣어야 합니다 \* .

 *.Vsix* 파일에 패키지 하지 않고 만든 시작 페이지를 배포 하려면 기본 파일 복사 전략을 사용 하는 것이 좋습니다. 예를 들어 일괄 처리 스크립트나 파일을 필요한 디렉터리에 저장할 수 있는 다른 배포 기술을 사용 하는 것이 좋습니다.

### <a name="to-manually-install-a-custom-start-page"></a>사용자 지정 시작 페이지를 수동으로 설치 하려면

1. 시작 페이지 태그를 포함 하는 *.xaml* 파일을 어셈블리 외의 지원 파일과 함께 복사 하 고 사용자의 * \Startstpages 폴더에 붙여넣습니다. \*

2. 시작 페이지에 어셈블리가 필요 하면 해당 페이지를 복사 하 *여에 \\ 붙여넣습니다. {Visual Studio 설치 폴더} \Common7\IDE\PrivateAssemblies \\ *.

3. **시작 옵션 페이지** 의 **시작 페이지 사용자 지정** 목록에서 새 시작 페이지를 선택 합니다. 자세한 내용은 [시작 페이지 사용자 지정](../ide/customizing-the-start-page-for-visual-studio.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보

- [시작 페이지 사용자 지정](../ide/customizing-the-start-page-for-visual-studio.md)
- [시작 페이지에 사용자 정의 컨트롤 추가](../extensibility/adding-user-control-to-the-start-page.md)
