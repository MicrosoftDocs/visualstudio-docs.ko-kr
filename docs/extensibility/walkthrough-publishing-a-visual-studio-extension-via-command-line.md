---
title: 명령줄을 사용 하 여 확장 게시
ms.date: 07/12/2018
ms.topic: how-to
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5108f4afa382c00376424432d2086f0494e34a03
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904673"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>연습: 명령줄을 통해 Visual Studio 확장 게시

이 연습에서는 명령줄을 사용 하 여 Visual Studio Marketplace에 Visual Studio 확장을 게시 하는 방법을 보여 줍니다. Marketplace에 확장을 추가 하면 개발자가 [**확장 및 업데이트**](../ide/finding-and-using-visual-studio-extensions.md) 대화 상자를 사용 하 여 새 확장과 업데이트 된 확장을 찾을 수 있습니다.

VsixPublisher.exe는 Visual Studio 확장을 Marketplace에 게시 하기 위한 명령줄 도구입니다. $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe에서 액세스할 수 있습니다. 이 도구에서 사용할 수 있는 명령은 **게시**, **createpublisher**, **deletepublisher**, **deletepublisher**, **login**및 **logout**입니다.

## <a name="commands"></a>명령

### <a name="publish"></a>게시

Marketplace에 확장을 게시 합니다. 확장은 vsix, exe/msi 파일 또는 링크 일 수 있습니다. 동일한 버전의 확장이 이미 있으면 확장을 덮어씁니다. 확장 프로그램이 아직 없는 경우 새 확장을 만듭니다.

|명령 옵션 |설명 |
|---------|---------|
|페이로드 (필수) | 게시할 페이로드의 경로 이거나 "추가 정보 URL"로 사용할 링크입니다. |
|항목 매니페스트 (필수) | 사용할 게시 매니페스트 파일의 경로입니다. |
|ignoreWarnings | 확장을 게시할 때 무시할 경고 목록입니다. 이러한 경고는 확장을 게시할 때 명령줄 메시지로 표시 됩니다. (예: "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | 게시자를 인증 하는 데 사용 되는 PAT (개인용 액세스 토큰)입니다. 제공 되지 않은 경우에는 로그인 한 사용자가 PAT를 획득 합니다. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Marketplace에서 게시자를 만듭니다. 또한 향후 작업을 위해 게시자를 컴퓨터에 기록 합니다 (예: 확장 삭제/게시).

|명령 옵션 |설명 |
|---------|---------|
|displayName (필수) | 게시자의 표시 이름입니다. |
|가 나 Ername (필수) | 게시자 이름 (예: 식별자)입니다. |
|personalAccessToken (필수) | 게시자를 인증 하는 데 사용 되는 개인 액세스 토큰입니다. |
|shortDescription | 게시자에 대 한 간단한 설명입니다 (파일이 아님). |
|이상 설명 | 게시자에 대 한 자세한 설명입니다 (파일이 아님). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Marketplace에서 게시자를 삭제 합니다.

|명령 옵션 |설명 |
|---------|---------|
|가 나 Ername (필수) | 게시자 이름 (예: 식별자)입니다. |
|personalAccessToken (필수) | 게시자를 인증 하는 데 사용 되는 개인 액세스 토큰입니다. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Marketplace에서 확장을 삭제 합니다.

|명령 옵션 |설명 |
|---------|---------|
|extensionName (필수) | 삭제할 확장의 이름입니다. |
|가 나 Ername (필수) | 게시자 이름 (예: 식별자)입니다. |
|personalAccessToken | 게시자를 인증 하는 데 사용 되는 개인 액세스 토큰입니다. 제공 되지 않은 경우에는 로그인 한 사용자가 pat를 획득 합니다. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>로그인

컴퓨터에 게시자를 로깅합니다.

|명령 옵션 |설명 |
|---------|---------|
|personalAccessToken (필수) | 게시자를 인증 하는 데 사용 되는 개인 액세스 토큰입니다. |
|가 나 Ername (필수) | 게시자 이름 (예: 식별자)입니다. |
|overwrite | 새 개인용 액세스 토큰을 사용 하 여 기존 게시자를 덮어쓰도록 지정 합니다. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

컴퓨터에서 게시자를 로깅합니다.

|명령 옵션 |설명 |
|---------|---------|
|가 나 Ername (필수) | 게시자 이름 (예: 식별자)입니다. |
|ignoreMissingPublisher | 지정 된 게시자가 아직 로그인 하지 않은 경우 도구에 오류가 발생 하지 않도록 지정 합니다. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>파일 매니페스트 파일

**게시** 명령에서 사용할 수 있는 매니페스트 파일을 사용 합니다. Marketplace에서 알고 있어야 하는 확장에 대 한 모든 메타 데이터를 나타냅니다. 업로드할 확장이 VSIX 확장의 경우 "identity" 속성은 "internalName"만 설정 해야 합니다. 이는 source.extension.vsixmanifest 파일에서 "id"의 나머지 속성을 생성할 수 있기 때문입니다. 확장이 msi/exe 또는 링크 확장인 경우 "identity" 속성에 필수 필드를 제공 해야 합니다. 매니페스트의 나머지 부분에는 Marketplace에 대 한 정보 (예: 범주, Q&A가 사용 하도록 설정 되었는지 여부)가 포함 되어 있습니다.

VSIX 확장: 매니페스트 파일 샘플:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

MSI/EXE 또는 링크 파일 매니페스트 파일 샘플:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>자산 파일

추가 정보 파일에 이미지와 같은 항목을 포함 하기 위해 자산 파일을 제공할 수 있습니다. 예를 들어 확장에 다음 "개요" Markdown 문서가 있는 경우:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

이전 예제에서 "images/testlogo.png"을 해결 하기 위해 사용자는 아래와 같이 해당 게시 매니페스트에 "assetFiles"를 제공할 수 있습니다.

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>연습 게시

### <a name="prerequisites"></a>사전 요구 사항

이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

### <a name="create-a-visual-studio-extension"></a>Visual Studio 확장 만들기

이 경우에는 기본 VSPackage 확장을 사용 하지만 동일한 단계는 모든 종류의 확장에 대해 유효 합니다.

1. 메뉴 명령을 포함 하는 "TestPublish" 라는 c #에서 VSPackage를 만듭니다. 자세한 내용은 [첫 번째 확장 만들기: Hello World](../extensibility/extensibility-hello-world.md)를 참조 하세요.

### <a name="package-your-extension"></a>확장 패키지

1. 제품 이름, 저자 및 버전에 대 한 올바른 정보를 사용 하 여 source.extension.vsixmanifest 확장을 업데이트 합니다.

   ![확장 source.extension.vsixmanifest 업데이트](media/update-extension-vsixmanifest.png)

2. **릴리스** 모드에서 확장을 빌드합니다. 이제 확장이 \bin\Release 폴더에 VSIX로 패키지 됩니다.

3. VSIX를 두 번 클릭 하 여 설치를 확인할 수 있습니다.

### <a name="test-the-extension"></a>확장 테스트

 확장을 배포 하기 전에 빌드 및 테스트를 수행 하 여 Visual Studio의 실험적 인스턴스에 제대로 설치 되었는지 확인 합니다.

1. Visual Studio에서 디버깅을 시작 합니다. Visual Studio의 실험적 인스턴스를 엽니다.

2. 실험적 인스턴스에서 **도구** 메뉴로 이동 하 여 **확장 및 업데이트 ...** 를 클릭 합니다. TestPublish 확장은 가운데 창에 표시 되 고 사용 하도록 설정 되어야 합니다.

3. **도구** 메뉴에서 테스트 명령이 표시 되는지 확인 합니다.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>명령줄을 통해 Marketplace에 확장을 게시 합니다.

1. 확장의 릴리스 버전을 빌드하고 최신 버전 인지 확인 해야 합니다.

2. publishmanifest.js및 overview.md 파일을 만들었는지 확인 합니다.

3. 명령줄을 열고 $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\ directory로 이동 합니다.

4. 새 게시자를 만들려면 다음 명령을 사용 합니다.

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. 게시자를 성공적으로 만들면 다음과 같은 명령줄 메시지가 표시 됩니다.

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. 으로 이동 하 여 만든 새 게시자를 확인할 수 있습니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. 새 확장을 게시 하려면 다음 명령을 사용 합니다.

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. 게시자를 성공적으로 만들면 다음과 같은 명령줄 메시지가 표시 됩니다.

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. 로 이동 하 여 게시 한 새 확장을 확인할 수 있습니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Visual Studio Marketplace에서 확장을 설치 합니다.

이제 확장이 게시 되었으므로 Visual Studio에 설치 하 고 테스트 합니다.

1. Visual Studio의 **도구** 메뉴에서 **확장 및 업데이트 ...** 를 클릭 합니다.

2. **온라인** 을 클릭 한 다음 testpublish를 검색 합니다.

3. **다운로드**를 클릭합니다. 그러면 확장이 설치 되도록 예약 됩니다.

4. 설치를 완료 하려면 Visual Studio의 모든 인스턴스를 닫습니다.

## <a name="remove-the-extension"></a>확장 제거

Visual Studio Marketplace 및 컴퓨터에서 확장을 제거할 수 있습니다.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>명령줄을 통해 Marketplace에서 확장을 제거 하려면

1. 확장을 제거 하려면 다음 명령을 사용 합니다.

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. 확장이 성공적으로 삭제 되 면 다음과 같은 명령줄 메시지가 표시 됩니다.

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>컴퓨터에서 확장을 제거 하려면

1. Visual Studio의 **도구** 메뉴에서 **확장 및 업데이트**를 클릭 합니다.

2. "MyVsixExtension"을 선택 하 고 **제거**를 클릭 합니다. 그러면 확장이 제거 되도록 예약 됩니다.

3. 제거를 완료 하려면 Visual Studio의 모든 인스턴스를 닫습니다.
