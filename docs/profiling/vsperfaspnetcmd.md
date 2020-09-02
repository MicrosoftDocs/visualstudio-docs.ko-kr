---
title: VSPerfASPNetCmd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b6ddadc15a5e0d53535b82d87aadd31fec65adaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330484"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
**VSPerfASPNetCmd.exe** 명령줄 도구를 사용하면 환경 변수를 설정하거나 컴퓨터를 다시 시작하지 않아도 ASP.Net 웹 사이트를 프로파일링할 수 있습니다. ASP.NET 웹 사이트를 프로파일링하며 **VSPerfCmd**에서 제공하는 추가 기능이 필요하지 않으면 [VSPerfCmd](../profiling/vsperfcmd.md) 대신 **VSPerfASPNetCmd.exe**를 사용합니다. **VSPerfASPNetCmd**에 대한 자세한 내용은 [VSPerfASPNETCmd를 사용한 빠른 웹 사이트 프로파일링](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)을 참조하세요. **VSPerfASPNetCmd**는 ASP.NET 웹 사이트를 프로파일링하기 위해 독립 실행형 프로파일러를 사용할 때 사용할 수 있는 기본 명령줄 도구입니다.

## <a name="syntax"></a>구문
 **vsperfaspnetcmd** [/*Options*] *Website*

## <a name="options"></a>옵션

|옵션|설명|
|------------|-----------------|
|**/Sample** 또는 **/s**|샘플링 방법을 사용하여 웹 사이트를 프로파일링합니다. **/Sample**이 기본 방법입니다. /Sample은 **/Trace**와 함께 사용할 수 없습니다.|
|**/Trace** 또는 **/t**|계측 방법을 사용하여 웹 사이트를 프로파일링합니다. /Trace는 **/Sample**과 함께 사용할 수 없습니다.|
|**/Memory**[ **:** `Type`]or   **/m**[ **:** {**a**&#124;**l**}]|메모리 할당을 프로파일링하고 선택적으로 개체 수명(가비지 수집)을 프로파일링합니다. **/Memory**는 샘플링 또는 계측 방법을 함께 사용할 수 있습니다.<br /><br /> *Type*은 다음 중 하나일 수 있습니다.<br /><br /> -   **allocation**(또는 **a**)은 메모리 할당 데이터만 수집합니다.<br />-   **lifetime**(또는 **l**)은 메모리 할당 및 개체 수명 데이터를 수집합니다.<br /><br /> 기본 `Type`은 **allocation**입니다.|
|**/Tip** 또는 **/i**|자세한 ASP.NET 요청 및 ADO.NET 호출 정보를 프로파일링 데이터에 추가합니다. **/Tip**은 샘플링 또는 계측 방법과 함꼐 사용할 수 있으며 **/Memory** 옵션과 함께 사용할 수 있습니다.|
|**/Output:** `File` 또는   **/o:** `File`|프로파일링 데이터(.*vsp*) 파일의 경로와 파일 이름을 지정합니다.|
|**/NoWait** 또는 **/n**|명령 프롬프트를 즉시 반환하여 명령 프롬프트 창에서 추가 명령을 사용할 수 있도록 합니다. 프로파일링을 해제하려면 별도 명령줄에 **VSPerfASPNETCmd /Shutdown**을 입력해야 합니다.|
|**/PackSymbols**[:{**on**&#124;**off**} 또는 **/p**[:{**on**&#124;**off**}|프로파일링 데이터(.*vsp*) 파일에 기호(함수, 매개 변수 이름 등)를 포함합니다.|
|**/Shutdown:** `Website`또는   **/d:** `Website`|프로파일링을 해제합니다. **/NoWait** 옵션을 사용하여 프로파일링을 시작한 후에 또는 프로파일러가 예기치 않게 종료된 경우에 명령줄에서 유일한 옵션으로 사용합니다. 원래의 **VSPerfASPNETCmd** 명령에 사용한 것과 동일한 URL을 지정합니다.|
|`Website`|프로파일링할 웹 사이트의 URL입니다.|

## <a name="see-also"></a>참조
- [VSPerfASPNETCmd를 사용한 빠른 웹 사이트 프로파일링](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
