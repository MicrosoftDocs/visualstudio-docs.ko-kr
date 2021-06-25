---
title: 소스 제어 플러그 인을 찾기 위해 키로 사용 되는 문자열
description: 원본 제어 플러그 인에 대 한 정보를 찾기 위해 레지스트리에 액세스 하기 위한 키인 문자열에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f25a105c442fa4a1ff8ed0f95b9c49272d751932
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899386"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>소스 제어 플러그 인을 찾기 위한 키로 사용되는 문자열
다음 문자열은 원본 제어 플러그 인에 대 한 정보를 찾기 위해 레지스트리에 액세스 하는 데 사용할 수 있는 키입니다.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` , `STR_SCCPROVIDERPATH` 및 `STR_SCCPROVIDERNAME` 는 DLL을 Visual Studio의 소스 제어 플러그 인으로 등록 하는 데 사용 되는 레지스트리 키 또는 값입니다.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` , `SCC_KEY, SCC_FILE_SIGNATURE` 및는 `SCC_STATUS_FILE` mssccprj.scc의 형식을 설명 하는 데 사용 됩니다. SCC 파일.

## <a name="string-keys-and-values"></a>문자열 키 및 값

|Key|값|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|원본 코드 제어|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ.SCC. SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|소스 코드 제어 파일|
|`SCC_NSE`|네임 스페이스 확장|
|`SCC_NSE_PREFIX`|프로토콜 접두사|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
- [방법: 소스 제어 플러그 인 설치](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [MSSCCPRJ.SCC 파일](../extensibility/mssccprj-scc-file.md)
