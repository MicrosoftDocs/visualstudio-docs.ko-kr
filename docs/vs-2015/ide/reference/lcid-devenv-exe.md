---
title: -LCID(devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: badb88abdf4b3ffd6140cb587b2b0add20630925
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672694"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IDE(통합 개발 환경) 내의 텍스트, 통화 및 다른 값에 사용된 기본 언어를 설정합니다.

## <a name="syntax"></a>구문

```
devenv {/LCID|/l} LocaleID
```

## <a name="arguments"></a>인수
 `LocaleID` 필수입니다. 지정한 언어의 LCID(로캘 ID)입니다.

## <a name="remarks"></a>설명
 IDE를 로드하고 환경에 대한 기본 자연 언어를 설정합니다. 이 변경은 세션 간에 유지되고 IDE의 **옵션** 대화 상자에 있는 **환경** 옵션의 **국가별 설정** 창에 반영됩니다.

 지정된 언어를 사용자의 시스템에서 사용할 수 없는 경우 /LCID 스위치는 무시됩니다.

 다음 표에서는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]에서 지원하는 언어의 LCID 목록을 보여 줍니다.

|언어|LCID|
|--------------|----------|
|중국어(간체)|2052|
|중국어(번체)|1028|
|영어|1033|
|프랑스어|1036|
|독일어|1031|
|이탈리아어|1040|
|일본어|1041|
|한국어|1042|
|스페인어|3082|

## <a name="example"></a>예
 이 예에서는 영어 리소스 문자열을 사용하는 IDE를 로드합니다.

```
devenv /LCID 1033
```

## <a name="see-also"></a>관련 항목
 [Devenv 명령줄 스위치](../../ide/reference/devenv-command-line-switches.md) [국가별 설정, 환경, 옵션 대화 상자](../../ide/reference/international-settings-environment-options-dialog-box.md) [창 레이아웃 사용자 지정](../../ide/customizing-window-layouts-in-visual-studio.md)
