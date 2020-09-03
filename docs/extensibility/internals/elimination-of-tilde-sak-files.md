---
title: ~ SAK 파일 제거 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708495"
---
# <a name="elimination-of-sak-files"></a>~ SAK 파일 제거
소스 제어 플러그 인 API 1.2에서는 소스 제어 플러그 인에서 *mssccprj.scc* 파일 및 공유 체크 아웃을 지원 하는지 여부를 검색 하는 새 함수 및 기능 플래그로 *~ SAK* 파일이 대체 되었습니다.

## <a name="sak-files"></a>~ SAK 파일
Visual Studio .NET 2003에는 *~ SAK*접두사가 붙은 임시 파일이 생성 되었습니다. 이러한 파일은 소스 제어 플러그 인에서 지원 되는지 여부를 확인 하는 데 사용 됩니다.

- *Mssccprj.scc* 파일입니다.

- 여러 (공유) 체크 아웃

소스 제어 플러그 인 API 1.2에 제공 된 고급 기능을 지 원하는 플러그 인의 경우 IDE는 다음 섹션에 자세히 설명 된 새로운 기능, 플래그 및 함수를 사용 하 여 임시 파일을 만들지 않고도 이러한 기능을 감지할 수 있습니다.

## <a name="new-capability-flags"></a>새 기능 플래그
 `SCC_CAP_SCCFILE`

 `SCC_CAP_MULTICHECKOUT`

## <a name="new-functions"></a>새로운 함수
- [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)

- [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)

 소스 제어 플러그 인에서 여러 (공유) 체크 아웃을 지 원하는 경우 기능을 선언 `SCC_CAP_MULTICHECKOUT` 하 고 함수를 구현 `SccIsMultiCheckOutEnabled` 합니다. 이 함수는 원본 제어 프로젝트에서 체크 아웃 작업이 발생할 때마다 호출 됩니다.

 소스 제어 플러그 인에서 *mssccprj.scc* 파일의 생성 및 사용을 지 원하는 경우 기능을 선언 `SCC_CAP_SCCFILE` 하 고 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)를 구현 합니다. 이 함수는 파일의 목록을 사용 하 여 호출 됩니다. 함수는 `TRUE' or 'FALSE` 각 파일에 대해를 반환 하 여 Visual Studio에서 *mssccprj.scc* 파일을 사용 해야 하는지 여부를 나타냅니다. 소스 제어 플러그 인에서 이러한 새 기능 및 기능을 지원 하지 않도록 선택 하는 경우 다음 레지스트리 키를 사용 하 여 이러한 파일을 만들지 않도록 설정할 수 있습니다.

 **[HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0\sourcecontrol] DoNotCreateTemporaryFilesInSourceControl**  =  *dword: 00000001*

> [!NOTE]
> 이 레지스트리 키가 *dword: 00000000*으로 설정 된 경우에는 해당 키가 존재 하지 않는 것과 같으며 Visual Studio에서 임시 파일을 계속 만들려고 시도 합니다. 그러나 레지스트리 키가 *dword: 00000001*로 설정 된 경우에는 Visual Studio에서 임시 파일을 만들려고 시도 하지 않습니다. 대신, 소스 제어 플러그 인이 *mssccprj.scc* 파일을 지원 하지 않으며 공유 체크 아웃을 지원 하지 않는 것으로 가정 합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
