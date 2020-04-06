---
title: '방법: 레지스트리 설정을 사용하여 개인 갤러리 관리 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2630fc71bea40a4d05e616ae336759ba62431a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710928"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>방법: 레지스트리 설정을 사용하여 개인 갤러리 관리
격리된 셸 확장의 관리자 또는 개발자인 경우 Visual Studio 갤러리, 샘플 갤러리 또는 개인 갤러리의 컨트롤, 템플릿 및 도구에 대한 액세스를 제어할 수 있습니다. 갤러리를 사용 가능하거나 사용할 수 없게 만들려면 수정된 레지스트리 키와 해당 값을 설명하는 *.pkgdef* 파일을 만듭니다.

## <a name="manage-private-galleries"></a>개인 갤러리 관리
 *.pkgdef* 파일을 만들어 여러 컴퓨터의 갤러리에 대한 액세스를 제어할 수 있습니다. 이 파일에는 다음 형식이 있어야 합니다.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 `Repositories` 키는 활성화또는 비활성화할 갤러리를 가리킵니다. 비주얼 스튜디오 갤러리와 샘플 갤러리는 다음 리포지토리 GUID를 사용합니다.

- 비주얼 스튜디오 갤러리 : 0F45E408-7995-4375-9485-86B8DB553DC9

- 샘플 갤러리 : AEB9CB40-D8E6-4615-B52C-27E307F8506C

  값은 `Disabled` 선택 사항입니다. 기본적으로 갤러리가 활성화됩니다.

  이 `Priority` 값은 **옵션** 대화 상자에 갤러리가 나열되는 순서를 결정합니다. 비주얼 스튜디오 갤러리는 우선 순위 10이고 샘플 갤러리에는 우선 순위 20이 있습니다. 개인 갤러리는 우선 순위 100부터 시작합니다. 여러 갤러리의 우선 순위 값이 동일한 경우 해당 갤러리가 표시되는 순서는 `DisplayName` 지역화된 특성의 값에 따라 결정됩니다.

  이 `Protocol` 값은 Atom 기반 또는 SharePoint 기반 갤러리에 필요합니다.

  `DisplayName`또는 둘 `DisplayNameResourceID` 다 `DisplayNamePackageGuid`와 를 지정해야 합니다. 모두 지정하면 `DisplayNameResourceID` 및 `DisplayNamePackageGuid` 쌍이 사용됩니다.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>.pkgdef 파일을 사용하여 비주얼 스튜디오 갤러리 비활성화
 *.pkgdef* 파일에서 갤러리를 비활성화할 수 있습니다. 다음 항목은 Visual Studio 갤러리를 사용하지 않도록 설정합니다.

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 다음 항목은 샘플 갤러리를 사용하지 않도록 설정합니다.

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>참조
- [프라이빗 갤러리](../extensibility/private-galleries.md)
