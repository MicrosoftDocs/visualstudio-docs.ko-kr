---
title: 명령줄을 사용하여 확장 게시
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40be0252218f39b4ff98b58caedd7f9f20ce6d5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697123"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>연습: 명령줄을 통해 Visual Studio 확장 게시

이 연습에서는 명령줄을 사용하여 Visual Studio 마켓플레이스에 Visual Studio 확장을 게시하는 방법을 보여 주십니다. 마켓플레이스에 확장을 추가하면 개발자는 확장 [**및 업데이트**](../ide/finding-and-using-visual-studio-extensions.md) 대화 상자를 사용하여 새 확장 및 업데이트된 확장을 찾아볼 수 있습니다.

VsixPublisher.exe는 마켓플레이스에 Visual Studio 확장을 게시하기 위한 명령줄 도구입니다. ${VSInstallDir}\VSSDK\VisualStudio통합\도구\Bin\VsixPublisher.exe에서 액세스할 수 있습니다. 이 도구에서 사용할 수 있는 명령은 다음과 같습니다: **게시**, **createPublisher**, **deletePublisher**, **deleteExtension**, **로그인**, **로그아웃**.

## <a name="commands"></a>명령

### <a name="publish"></a>게시

마켓플레이스에 확장을 게시합니다. 확장은 vsix, exe/msi 파일 또는 링크일 수 있습니다. 확장이 이미 동일한 버전으로 있는 경우 확장을 덮어씁니다. 확장이 아직 존재하지 않는 경우 새 확장을 만듭니다.

|명령 옵션 |설명 |
|---------|---------|
|페이로드(필수) | 게시할 페이로드 경로 또는 "추가 정보 URL"로 사용할 링크입니다. |
|게시 매니페스트(필수) | 사용할 게시 매니페스트 파일에 대한 경로입니다. |
|무시 경고 | 확장을 게시할 때 무시할 경고 목록입니다. 이러한 경고는 확장을 게시할 때 명령줄 메시지로 표시됩니다. (예: "VSIXValidatorWarning01, VSIXValidatorWarning02")
|개인 액세스 토큰 | 게시자를 인증하는 데 사용되는 PAT(개인 액세스 토큰)입니다. 제공되지 않으면 PAT는 로그인한 사용자로부터 획득됩니다. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>만들기게시자

마켓플레이스에서 게시자를 만듭니다. 또한 게시자를 컴퓨터에 기록하여 향후 작업을 수행합니다(예: 확장 삭제/게시).

|명령 옵션 |설명 |
|---------|---------|
|표시이름(필수) | 게시자의 이름을 표시합니다. |
|게시자 이름(필수) | 게시자 이름(예: 식별자)입니다. |
|개인 액세스 토큰(필수) | 게시자를 인증하는 데 사용되는 개인 액세스 토큰입니다. |
|간략한 설명 | 게시자(파일이 아님)에 대한 간략한 설명입니다. |
|긴 설명 | 게시자(파일이 아님)에 대한 긴 설명입니다. |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>삭제게시자

마켓플레이스에서 게시자를 삭제합니다.

|명령 옵션 |설명 |
|---------|---------|
|게시자 이름(필수) | 게시자 이름(예: 식별자)입니다. |
|개인 액세스 토큰(필수) | 게시자를 인증하는 데 사용되는 개인 액세스 토큰입니다. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>삭제확장

마켓플레이스에서 확장을 삭제합니다.

|명령 옵션 |설명 |
|---------|---------|
|확장 이름(필수) | 삭제할 확장의 이름입니다. |
|게시자 이름(필수) | 게시자 이름(예: 식별자)입니다. |
|개인 액세스 토큰 | 게시자를 인증하는 데 사용되는 개인 액세스 토큰입니다. 제공되지 않으면 패팅은 로그인한 사용자로부터 획득됩니다. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>로그인

게시자를 컴퓨터에 기록합니다.

|명령 옵션 |설명 |
|---------|---------|
|개인 액세스 토큰(필수 | 게시자를 인증하는 데 사용되는 개인 액세스 토큰입니다. |
|게시자 이름(필수) | 게시자 이름(예: 식별자)입니다. |
|overwrite | 기존 게시자가 새 개인 액세스 토큰으로 덮어써야 한다고 지정합니다. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

컴퓨터에서 게시자를 기록합니다.

|명령 옵션 |설명 |
|---------|---------|
|게시자 이름(필수) | 게시자 이름(예: 식별자)입니다. |
|무시누락게시자 | 지정된 게시자가 아직 로그인하지 않은 경우 도구에 오류가 발생하지 않도록 지정합니다. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>게시매니페스트 파일

publishManifest 파일은 **게시** 명령에서 사용됩니다. 마켓플레이스에서 알아야 할 확장에 대한 모든 메타데이터를 나타냅니다. 업로드중인 확장이 VSIX 확장에서 온 경우 "ID" 속성에는 "internalName" 집합만 있어야 합니다. 이는 나머지 "ID" 속성이 vsixmanifest 파일에서 생성될 수 있기 때문입니다. 확장이 msi/exe 또는 링크 확장인 경우 사용자는 "ID" 속성에 필요한 필드를 제공해야 합니다. 매니페스트의 나머지 부분에는 마켓플레이스와 관련된 정보(예: 카테고리, Q&A가 활성화되어 있는지 여부 등)가 포함되어 있습니다.

VSIX 확장자 게시매니페스트 파일 샘플:

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

MSI/EXE 또는 LINK 게시매니페스트 파일 샘플:

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

자산 파일은 readme 파일에 이미지와 같은 것들을 포함하기 위해 제공 될 수있다. 예를 들어 확장에 다음과 같은 "개요" 마크다운 문서가 있는 경우:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

이전 예제에서 "이미지/testlogo.png"를 해결하기 위해 사용자는 다음과 같이 게시 매니페스트에 "assetFiles"를 제공할 수 있습니다.

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

## <a name="publishing-walkthrough"></a>게시 연습

### <a name="prerequisites"></a>사전 요구 사항

이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

### <a name="create-a-visual-studio-extension"></a>비주얼 스튜디오 확장 만들기

이 경우 기본 VSPackage 확장을 사용 하지만 동일한 단계는 모든 종류의 확장에 대 한 유효 합니다.

1. 메뉴 명령이 있는 "TestPublish"라는 이름의 C#에서 VSPackage를 만듭니다. 자세한 내용은 [첫 번째 확장 만들기: Hello World](../extensibility/extensibility-hello-world.md)를 참조하십시오.

### <a name="package-your-extension"></a>확장 패키지

1. 제품 이름, 작성자 및 버전에 대한 올바른 정보로 확장 vsixmanifest를 업데이트합니다.

   ![업데이트 확장 vsixmanifest](media/update-extension-vsixmanifest.png)

2. **릴리스** 모드에서 확장을 빌드합니다. 이제 확장이 \bin\Release 폴더에 VSIX로 패키징됩니다.

3. VSIX를 두 번 클릭하여 설치를 확인할 수 있습니다.

### <a name="test-the-extension"></a>확장 테스트

 확장을 배포하기 전에 Visual Studio의 실험 인스턴스에 제대로 설치되었는지 확인합니다.

1. Visual Studio에서 디버깅을 시작합니다. 을 사용하여 Visual Studio의 실험 인스턴스를 엽니다.

2. 실험적인 인스턴스에서 **도구** 메뉴로 이동하여 **확장 및 업데이트를 클릭합니다...**. TestPublish 확장은 가운데 창에 나타나고 활성화되어야 합니다.

3. **도구** 메뉴에서 테스트 명령이 표시되는지 확인합니다.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>명령줄을 통해 마켓플레이스에 확장 게시

1. 확장의 릴리스 버전을 빌드하 고 최신 인지 확인 합니다.

2. 게시 매니페스트.json 및 overview.md 파일을 만들었는지 확인합니다.

3. 명령줄을 열고 ${VSInstallDir}\VSSDK\VisualStudioIntegration\도구\Bin\ 디렉토리로 이동합니다.

4. 새 게시자를 만들려면 다음 명령을 사용합니다.

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. 게시자를 성공적으로 만들면 다음 명령줄 메시지가 표시됩니다.

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. [Visual Studio 마켓플레이스로](https://marketplace.visualstudio.com/manage/publishers) 이동하여 만든 새 게시자를 확인할 수 있습니다.

7. 새 확장을 게시하려면 다음 명령을 사용합니다.

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. 게시자를 성공적으로 만들면 다음 명령줄 메시지가 표시됩니다.

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. [Visual Studio 마켓플레이스로](https://marketplace.visualstudio.com/) 이동하여 게시한 새 확장을 확인할 수 있습니다.

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>비주얼 스튜디오 마켓플레이스에서 확장 설치

이제 확장이 게시되었으므로 Visual Studio에 설치하고 테스트합니다.

1. 비주얼 스튜디오에서 **도구** 메뉴에서 **확장 및 업데이트를 클릭합니다...**.

2. **온라인을** 클릭한 다음 테스트 게시를 검색합니다.

3. **다운로드**를 클릭합니다. 그러면 확장이 설치될 예정입니다.

4. 설치를 완료하려면 Visual Studio의 모든 인스턴스를 닫습니다.

## <a name="remove-the-extension"></a>확장 제거

Visual Studio 마켓플레이스와 컴퓨터에서 확장을 제거할 수 있습니다.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>명령줄을 통해 마켓플레이스에서 확장을 제거하려면

1. 확장을 제거하려면 다음 명령을 사용합니다.

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. 확장을 성공적으로 삭제하면 다음 명령줄 메시지가 표시됩니다.

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>컴퓨터에서 확장을 제거하려면

1. 비주얼 스튜디오에서 **도구** 메뉴에서 **확장 및 업데이트를 클릭합니다.**

2. "MyVsixExtension"를 선택한 다음 **제거를**클릭합니다. 그러면 확장이 제거될 예정입니다.

3. 제거를 완료하려면 Visual Studio의 모든 인스턴스를 닫습니다.
