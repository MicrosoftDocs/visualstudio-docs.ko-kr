---
title: 일반적으로 프로젝트를 확장하는 데 사용되는 개체에 대한 CATID | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, CATIDs
- GUIDs, VSPackages
- CATIDs for VSPackages
ms.assetid: 0c7fdb66-ed96-4b36-89f6-021bca573572
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5754e53f24731eb44dba128ccfcf4b474e833d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709860"
---
# <a name="catids-for-objects-that-are-typically-used-to-extend-projects"></a>일반적으로 프로젝트를 확장하는 데 사용되는 개체에 대한 CATID
다음 표에는 `Project` 에 `ProjectItem` [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]대한 및 프로젝트에 대한 개체를 확장하고 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 자동화하는 데 사용되는 CATID가 나열됩니다. 이러한 CATID는 *VSLangProj.olb에*정의되어 있습니다.

## <a name="listing-of-catids"></a>CATIDs 목록

|이름|GUID|
|----------|----------|
|<xref:VSLangProj.PrjCATID.prjCATIDProject>|{610D4614-D0D5-11D2-8599-006097C68E81}|
|<xref:VSLangProj.PrjCATID.prjCATIDProjectItem>|{610D4615-D0D5-11D2-8599-006097C68E81}|

## <a name="visual-basic-catids"></a>비주얼 베이직 CATID
 다음 표에는 찾아보기 개체를 확장하는 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 데 사용되는 CATID가 나열됩니다. 그들은 모두 *VSLangProj.olb에*정의되어 있습니다.

|이름|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectBrowseObject>|{E0FDC879-C32A-4751-A3D3-0B3824BD575F}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBProjectConfigBrowseObject>|{67F8DD11-14EB-489b-87F0-F01C52AF3870}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFileBrowseObject>|{EA5BD05D-3C72-40A5-95A0-28A2773311CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBFolderBrowseObject>|{932DC619-2EAA-4192-B7E6-3D15AD31DF49}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDVBReferenceBrowseObject>|{2289B812-8191-4e81-B7B3-174045AB0CB5}|

## <a name="visual-c-catids"></a>비주얼 C # CATIDs
 다음 CATID를 사용하여 찾아보기 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 개체를 확장할 수 있습니다. 그들은 모두 *VSLangProj.olb에*정의되어 있습니다.

|이름|GUID|
|----------|----------|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectBrowseObject>|{4EF9F003-DE95-4d60-96B0-212979F2A857}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpProjectConfigBrowseObject>|{A12CE10A-227F-4963-ADB6-3A43388513CA}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFileBrowseObject>|{8D58E6AF-ED4E-48B0-8C7B-C74EF0735451}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpFolderBrowseObject>|{914FE278-054A-45DB-BF9E-5F22484CC84C}|
|<xref:VSLangProj.PrjBrowseObjectCATID.prjCATIDCSharpReferenceBrowseObject>|{2F0FA3B8-C855-4a4e-95A5-CB45C67D6C27}|

## <a name="c-catids"></a>C++ CATIDs
 다음 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트 시스템 CATID는 .NET 2003의 형식 라이브러리에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 노출되지 않으며 이러한 프로젝트 개체를 확장할 때마다 코드에 포함해야 합니다. 이러한 CATID는 의 이후 릴리스의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]형식 라이브러리에 포함됩니다.

|이름|GUID|
|----------|----------|
|`CVCProjectNode`|{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFolderNode`|{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCFileNode`|{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|

 다음 코드 예제에서는 코드에서 이러한 CATID를 프로그래밍하는 방법을 보여 줍니다.

```
const LPOLESTR CVCProjectNode::s_wszCATID = L"{EE8299CB-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFolderNode::s_wszCATID = L"{EE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCFileNode::s_wszCATID = L"{EE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
```

 다음 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트 시스템 CATID는 .NET 2003의 형식 라이브러리에도 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 노출되지 않으며 이러한 프로젝트 개체를 확장할 때마다 코드에 포함해야 합니다. 이러한 CATID는 .NET [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 2003에서만 사용할 수 있으며 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]의 이후 릴리스에서는 사용할 수 없습니다.

|이름|GUID|
|----------|----------|
|`CVCAssemblyReferenceNode`|{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}|
|`CVCProjectReferenceNode`|{593DCFCE-20A7-48e4-ACA1-49ADE9049887}|
|`CVCActiveXReferenceNode`|{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}|
|`CVCReferences`|{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}|

 다음 코드 예제에서는 코드에서 이러한 CATID를 프로그래밍하는 방법을 보여 줍니다.

```
const LPOLESTR CVCAssemblyReferenceNode::s_wszCATID = L"{FE8299C9-19B6-4f20-ABEA-E1FD9A33B683}";
const LPOLESTR CVCProjectReferenceNode::s_wszCATID = L"{593DCFCE-20A7-48e4-ACA1-49ADE9049887}";
const LPOLESTR CVCActiveXReferenceNode::s_wszCATID = L"{9E8182D3-C60A-44f4-A74B-14C90EF9CACE}";
const LPOLESTR CVCReferences::s_wszCATID = L"{FE8299CA-19B6-4f20-ABEA-E1FD9A33B683}";
```

 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 및 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 프로젝트 유형에 대한 GUID는 다음 표에 나와 있습니다.

| 프로젝트 형식 | GUID |
| - | - |
| [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] | {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} |
| [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] | {F184B08F-C81C-45F6-A57F-5ABD9991F28F} |

## <a name="see-also"></a>참조
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [프로젝트 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)
