---
title: 레지스트리 설정을 사용 하 여 전용 갤러리 관리
description: Visual Studio 갤러리, 샘플 갤러리 또는 개인 갤러리에서 컨트롤, 템플릿 및 도구에 대 한 액세스를 제어 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9fef1e6447ac07e9c3d4ccfb76a9ee1e06f91e42
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898837"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>방법: 레지스트리 설정을 사용 하 여 전용 갤러리 관리
격리 된 셸 확장의 관리자 또는 개발자 인 경우 Visual Studio 갤러리, 샘플 갤러리 또는 개인 갤러리의 컨트롤, 템플릿 및 도구에 대 한 액세스를 제어할 수 있습니다. 갤러리를 사용할 수 있거나 사용할 수 없게 하려면 수정 된 레지스트리 키와 해당 값을 설명 하는 *.pkgdef* 파일을 만듭니다.

## <a name="manage-private-galleries"></a>개인 갤러리 관리
 여러 컴퓨터의 갤러리에 대 한 액세스를 제어 하는 *.pkgdef* 파일을 만들 수 있습니다. 이 파일의 형식은 다음과 같아야 합니다.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 `Repositories`키는 사용 하거나 사용 하지 않도록 설정할 갤러리를 참조 합니다. Visual Studio 갤러리와 샘플 갤러리는 다음과 같은 리포지토리 Guid를 사용 합니다.

- Visual Studio 갤러리: 0F45E408-7995-4375-9485-86B8DB553DC9

- 샘플 갤러리: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  `Disabled`이 값은 선택 사항입니다. 기본적으로 갤러리는 사용 하도록 설정 되어 있습니다.

  값은 [ `Priority` **옵션** ] 대화 상자에 표시 되는 갤러리의 순서를 결정 합니다. Visual Studio 갤러리의 우선 순위는 10이 고 샘플 갤러리의 우선 순위는 20입니다. 개인 갤러리는 우선 순위 100에서 시작 합니다. 여러 갤러리에 동일한 우선 순위 값이 있는 경우 해당 값이 표시 되는 순서는 지역화 된 특성의 값에 따라 결정 됩니다 `DisplayName` .

  `Protocol`Atom 기반 또는 SharePoint 기반 갤러리의 경우이 값이 필요 합니다.

  `DisplayName`또는 둘 다 `DisplayNameResourceID` `DisplayNamePackageGuid` 지정 해야 합니다. All을 지정 하면 `DisplayNameResourceID` 및 `DisplayNamePackageGuid` 쌍이 사용 됩니다.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>.Pkgdef 파일을 사용 하 여 Visual Studio 갤러리를 사용 하지 않도록 설정
 *.Pkgdef* 파일에서 갤러리를 사용 하지 않도록 설정할 수 있습니다. 다음 항목은 Visual Studio 갤러리를 사용 하지 않도록 설정 합니다.

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 다음 항목은 샘플 갤러리를 사용 하지 않도록 설정 합니다.

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>참조
- [프라이빗 갤러리](../extensibility/private-galleries.md)
