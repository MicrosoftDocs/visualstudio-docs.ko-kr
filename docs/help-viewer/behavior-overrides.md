---
title: 도움말 콘텐츠 관리자 재정의
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c03d631be1bc4a38e514e1019fa230775427a53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825103"
---
# <a name="help-content-manager-overrides"></a>도움말 콘텐츠 관리자 재정의

Visual Studio IDE에서 도움말 뷰어와 도움말 관련 기능의 기본 동작을 변경할 수 있습니다. 일부 옵션은 [.pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/) 파일을 만들어 다양한 레지스트리 키 값을 설정하여 지정됩니다. 다른 옵션은 레지스트리에서 직접 설정됩니다.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>.pkgdef 파일을 사용하여 도움말 뷰어 동작을 제어하는 방법

1. 첫 번째 줄이 `[$RootKey$\Help]`으로 포함된 *.pkgdef* 파일을 만듭니다.

2. 별도의 줄에서 아래 표에 설명된 레지스트리 키 값의 일부 또는 전체를 추가합니다(예: `"UseOnlineHelp"=dword:00000001`).

3. 파일을 *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\\<edition\>\Common7\IDE\CommonExtensions*에 복사합니다.

4. 개발자 명령 프롬프트에서 `devenv /updateconfiguration`를 실행합니다.

### <a name="registry-key-values"></a>레지스트리 키 값

|레지스트리 키 값|형식|데이터|Description|
|------------------|----|----|-----------|
|NewContentAndUpdateService|문자열|\<http URL for service endpoint\>|고유한 서비스 엔드포인트 정의|
|UseOnlineHelp|dword|로컬 도움말을 지정하려면 `0`, 온라인 도움말을 지정하려면 `1`|온라인 또는 오프라인 도움말 기본값 정의|
|OnlineBaseUrl|문자열|\<http URL for service endpoint\>|고유한 F1 엔드포인트 정의|
|OnlineHelpPreferenceDisabled|dword|온라인 도움말 기본 설정 옵션을 사용하려고 설정하려면 `0` 또는 사용하지 않도록 설정하려면 `1`|온라인 도움말 기본 설정 옵션을 사용하지 않도록 설정|
|DisableManageContent|dword|도움말 뷰어에서 **콘텐츠 관리** 탭을 사용하도록 설정하려면 `0` 또는 사용하도록 설정하지 않으려면 `1`|**콘텐츠 관리** 탭 사용 안 함|
|DisableFirstRunHelpSelection|dword|처음으로 시작될 때 구성된 도움말 기능을 사용하도록 설정하려면 `0` 또는 사용하지 않도록 설정하려면 `1`|Visual Studio 처음 시작 시 콘텐츠 설치 사용 안 함|

### <a name="example-pkgdef-file-contents"></a>예제:.pkgdef 파일 콘텐츠

```pkgdef
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>레지스트리 편집기를 사용하여 도움말 뷰어 동작 변경

다음 두 동작은 레지스트리 편집기에서 레지스트리 키 값을 설정하여 제어할 수 있습니다.

|Task|레지스트리 키|값|데이터|
|----------|-----|------|----|
|BITS 작업 우선 순위 재정의|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (on a 64-bit machine)\Microsoft\Help\v2.3|BITSPriority|**전경**, **높음**, **보통** 또는 **낮음**|
|네트워크 공유의 로컬 콘텐츠 저장소 가리키기|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>추가 정보

- [도움말 뷰어 관리자 가이드](../help-viewer/administrator-guide.md)
- [도움말 콘텐츠 관리자에 대 한 명령줄 인수](../help-viewer/command-line-arguments.md)
- [Microsoft 도움말 뷰어](../help-viewer/overview.md)