---
title: VerifyFileHash 작업 | Microsoft Docs
ms.date: 01/28/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- VerifyFileHash task [MSBuild]
- MSBuild, VerifyFileHash task
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9340657704900feb5ebdc188103109872ee39f5d
ms.sourcegitcommit: e3b9cbeea282f1b531c6a3f60515ebfe1688aa0e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/18/2020
ms.locfileid: "77439127"
---
# <a name="verifyfilehash-task"></a>VerifyFileHash 작업

파일이 예상 파일 해시와 일치하는지 확인합니다. 해시가 일치하지 않으면 작업이 실패합니다.

이 작업은 15.8에 추가되었지만 16.0 미만의 MSBuild 버전에 사용하려면 [해결 방법](https://github.com/Microsoft/msbuild/pull/3999#issuecomment-458193272)이 필요합니다.

## <a name="task-parameters"></a>작업 매개 변수

 다음 표에서는 `VerifyFileHash` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|`File`|필수 `String` 매개 변수입니다.<br /><br />해시되고 유효성이 검사된 파일입니다.|
|`Hash`|필수 `String` 매개 변수입니다.<br /><br />파일의 예상 해시입니다.|
|`Algorithm`|선택적 `String` 매개 변수입니다.<br /><br />알고리즘입니다. 허용되는 값: `SHA256`, `SHA384`, `SHA512`. 기본값은 `SHA256`입니다.|
|`HashEncoding`|선택적 `String` 매개 변수입니다.<br /><br />생성된 해시에 사용할 인코딩입니다. 기본값은 `hex`입니다. 허용되는 값은 `hex`, `base64`입니다.|

## <a name="example"></a>예제

다음 예제에서는 `VerifyFileHash` 작업을 사용하여 자체 체크섬을 확인합니다.

```xml
<Project>
  <Target Name="VerifyHash">
    <GetFileHash Files="$(MSBuildProjectFullPath)">
      <Output
          TaskParameter="Items"
          ItemName="FilesWithHashes" />
    </GetFileHash>

    <Message Importance="High"
             Text="@(FilesWithHashes->'%(Identity): %(FileHash)')" />

    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="$(ExpectedHash)" />
  </Target>
</Project>
```

MSBuild 16.5 이상에서 제어 흐름의 조건으로 해시 비교를 사용하는 경우와 같이 해시가 일치하지 않을 때 빌드가 실패하지 않도록 하려면 다음 코드를 사용하여 경고를 메시지로 다운그레이드할 수 있습니다.

```xml
  <PropertyGroup>
    <MSBuildWarningsAsMessages>$(MSBuildWarningsAsMessages);MSB3952</MSBuildWarningsAsMessages>
  </PropertyGroup>

  <Target Name="DemoVerifyCheck">
    <VerifyFileHash File="$(MSBuildThisFileFullPath)"
                    Hash="1"
                    ContinueOnError="WarnAndContinue" />

    <PropertyGroup>
      <HashMatched>$(MSBuildLastTaskResult)</HashMatched>
    </PropertyGroup>

    <Message Condition=" '$(HashMatched)' != 'true'"
             Text="The hash didn't match" />

    <Message Condition=" '$(HashMatched)' == 'true'"
             Text="The hash did match" />
  </Target>
```

## <a name="see-also"></a>참조

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
