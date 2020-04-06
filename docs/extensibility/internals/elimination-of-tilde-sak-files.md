---
title: ~ SAK 파일 제거 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0294198bb1560f8df6f17170013f88d4fe11e5cf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708495"
---
# <a name="elimination-of-sak-files"></a>~ SAK 파일 제거
소스 제어 플러그인 API 1.2에서 *~ SAK* 파일은 소스 제어 플러그인이 *MSSCCPRJ* 파일 및 공유 체크 아웃을 지원하는지 여부를 감지하는 기능 플래그 및 새로운 기능으로 대체되었습니다.

## <a name="sak-files"></a>~ SAK 파일
Visual Studio .NET 2003은 *~SAK로*접두사된 임시 파일을 만들었습니다. 이러한 파일은 소스 제어 플러그인이 다음을 지원하는지 확인하는 데 사용됩니다.

- *MSSCCPRJ.SCC* 파일.

- 여러(공유) 체크 아웃.

소스 제어 플러그인 API 1.2에 제공된 고급 기능을 지원하는 플러그인의 경우 IDE는 다음 섹션에서 자세히 설명한 새로운 기능, 플래그 및 기능을 사용하여 임시 파일을 만들지 않고도 이러한 기능을 검색할 수 있습니다.

## <a name="new-capability-flags"></a>새 기능 플래그
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>새로운 함수
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 소스 제어 플러그인이 여러(공유) 체크 아웃을 지원하는 경우 `SCC_CAP_MULTICHECKOUT` 기능을 선언하고 `SccIsMultiCheckOutEnabled` 함수를 구현합니다. 이 함수는 소스 제어 프로젝트에서 체크 아웃 작업이 발생할 때마다 호출됩니다.

 소스 제어 플러그인이 *MSSCCPRJ.SCC* 파일의 생성 및 사용을 지원하는 경우 `SCC_CAP_SCCFILE` 기능을 선언하고 [SccWillCreateSccFile을](../../extensibility/sccwillcreatesccfile-function.md)구현합니다. 이 함수는 파일 목록과 함께 호출됩니다. 이 함수는 각 파일에 `TRUE' or 'FALSE` 대해 Visual Studio에서 *MSSCCPRJ.SCC* 파일을 사용해야 하는지 여부를 나타냅니다. 소스 제어 플러그인이 이러한 새로운 기능 및 기능을 지원하지 않도록 선택하면 다음 레지스트리 키를 사용하여 이러한 파일 의 생성을 비활성화할 수 있습니다.

 **[HKEY_CURRENT_USER\소프트웨어\마이크로소프트\비주얼 스튜디오\8.0\소스 컨트롤] ** = *DoNotCreate임시파일인소스제어검:00000001*

> [!NOTE]
> 이 레지스트리 키가 *dword:0000000으로*설정된 경우 존재하지 않는 키와 동일하며 Visual Studio는 여전히 임시 파일을 만들려고 시도합니다. 그러나 레지스트리 키가 *dword:00000001로*설정된 경우 Visual Studio는 임시 파일을 만들려고 시도하지 않습니다. 대신 소스 제어 플러그인이 *MSSCCPRJ.SCC* 파일을 지원하지 않으며 공유 체크 아웃을 지원하지 않는다고 가정합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 버전 1.2의 새로운 소식](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
