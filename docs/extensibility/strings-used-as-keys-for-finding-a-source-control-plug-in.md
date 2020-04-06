---
title: 소스 제어 플러그인찾기를 위한 키로 사용되는 문자열 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9333ff1b6742ca14dc5541bd15e92b2eb39085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699710"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>소스 제어 플러그 인을 찾기 위한 키로 사용되는 문자열
다음 문자열은 소스 제어 플러그인에 대한 정보를 찾기 위해 레지스트리에 액세스하기 위한 키입니다.

 `STR_SCC_PROVIDER_REG_LOCATION``STR_PROVIDERREGKEY` `STR_SCCPROVIDERNAME` 및 레지스트리 키 또는 값은 Visual Studio의 소스 제어 플러그인으로 DLL을 등록하는 데 `STR_SCCPROVIDERPATH`사용됩니다.

 `SCC_PROJECTNAME_KEY``SCC_KEY, SCC_FILE_SIGNATURE`을 `SCC_PROJECTAUX_KEY`사용하며 `SCC_STATUS_FILE` MSSCCPRJ의 형식을 설명하는 데 사용됩니다. SCC 파일.

## <a name="string-keys-and-values"></a>문자열 키 및 값

|키|값|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|소프트웨어\소스코드제어제공자|
|`STR_PROVIDERREGKEY`|공급자레그키|
|`STR_SCCPROVIDERPATH`|SCC서버패스|
|`STR_SCCPROVIDERNAME`|SCC서버 이름|
|`STR_SCC_INI_SECTION`|원본 코드 제어|
|`STR_SCC_INI_KEY`|소스 코드 제어 제공 자|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. Scc|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|소스 코드 제어 파일|
|`SCC_NSE`|네임스페이스 확장|
|`SCC_NSE_PREFIX`|프로토컬 접두사|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFrom소스제어|
|`STR_SCCHELPCOLLECTION`|도움말 컬렉션|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|소프트웨어\마이크로소프트\소스 세이프|

## <a name="see-also"></a>참조
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
- [방법: 소스 제어 플러그 인 설치](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [MSSCCPRJ.SCC 파일](../extensibility/mssccprj-scc-file.md)
