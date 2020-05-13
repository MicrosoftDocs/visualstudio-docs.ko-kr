---
title: MSBuild 프로젝트 파일의 데이터 유지 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e83526007f676ae94ddce57936b627bcb4308c2a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706692"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild 프로젝트 파일의 데이터 유지
프로젝트 하위 형식은 나중에 사용하기 위해 하위 유형별 데이터를 프로젝트 파일에 유지해야 할 수 있습니다. 프로젝트 하위 유형은 프로젝트 파일 지속성을 사용하여 다음 요구 사항을 충족합니다.

1. 프로젝트 빌드의 일부로 사용되는 데이터를 유지합니다. (Microsoft 빌드 엔진에 대한 자세한 내용은 [MSBuild를](../../msbuild/msbuild.md)참조하십시오.) 빌드 관련 정보는 다음 중 하나를 수행할 수 있습니다.

    1. 구성 독립적 인 데이터. 즉, MSBuild 요소에 저장된 데이터는 비어 있거나 누락된 조건입니다.

    2. 구성 종속 데이터입니다. 즉, 특정 프로젝트 구성에 대해 조건이 되는 MSBuild 요소에 저장된 데이터입니다. 다음은 그 예입니다.

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. 빌드와 관련이 없는 데이터를 유지합니다. 이 데이터는 XML 스키마에 대해 유효성이 검사되지 않은 자유 형식 XML로 표현할 수 있습니다.

    1. 구성 독립적 인 데이터.

    2. 구성 종속 데이터입니다.

## <a name="persisting-build-related-information"></a>빌드 관련 정보 유지
 프로젝트를 빌드하는 데 유용한 데이터의 지속성은 MSBuild를 통해 처리됩니다. MSBuild 시스템은 빌드 관련 정보의 마스터 테이블을 유지 관리합니다. 프로젝트 하위 유형은 속성 값을 얻고 설정하기 위해 이 데이터에 액세스하는 작업을 담당합니다. 프로젝트 하위 유형은 지속할 추가 속성을 추가하고 속성이 유지되지 않도록 제거하여 빌드 관련 데이터 테이블을 보강할 수도 있습니다.

 MSBuild 데이터를 수정하려면 프로젝트 하위 형식은 기본 프로젝트 시스템에서 를 통해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>MSBuild 속성 개체를 검색합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>는 핵심 프로젝트 시스템에 구현된 인터페이스와 실행하여 `QueryInterface`프로젝트 하위 유형 쿼리를 집계합니다.

 다음 절차에서는 을 사용하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>속성을 제거하는 단계를 간략하게 설명합니다.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>MSBuild 프로젝트 파일에서 속성을 제거하려면

1. 프로젝트 `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 하위 유형을 호출합니다.

2. 제거할 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> `pszPropName` 속성으로 설정하여 호출합니다.

### <a name="persisting-non-build-related-information"></a>비빌드 관련 정보 유지
 빌드에 중요하지 않은 프로젝트 파일의 데이터의 지속성은 을 통해 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>처리됩니다.

 기본 `project subtype aggregator` 개체, 개체 또는 `project subtype project configuration` 둘 다에서 구현할 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 수 있습니다.

 다음 사항은 빌드가 아닌 관련 정보의 지속성에 대한 주요 개념을 간략하게 설명합니다.

- 기본 프로젝트는 기본 프로젝트 하위 유형(즉, 가장 바깥쪽 프로젝트 하위 유형) 집계 개체를 호출하여 구성 독립적인 데이터를 로드하고 저장하며, 프로젝트 하위 유형 프로젝트 구성 개체를 호출하여 구성 종속 데이터를 로드하거나 저장합니다.

- 기본 프로젝트는 각 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 하위 유형 집계 수준에 대해 여러 번 메서드를 호출하고 각 수준에 대한 GUID를 전달합니다.

- 기본 프로젝트는 특정 프로젝트 하위 유형에 전용으로 사용되며 집계 수준 간에 상태를 유지하는 방법으로 이 메커니즘을 사용하는 XML 조각을 전달하거나 받습니다.

- 기본 프로젝트는 GUID에서 전달하는 가장 바깥쪽 프로젝트 하위 형식의 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>구현을 호출합니다. GUID가 가장 바깥쪽 프로젝트 하위 유형에 속하는 경우 호출 자체를 처리합니다. 그렇지 않으면 GUID가 일치하는 프로젝트 하위 유형이 발견될 때까지 내부 프로젝트 하위 유형 등으로 호출을 위임합니다.

- 프로젝트 하위 유형은 내부 프로젝트 하위 유형에 대한 호출을 위임하기 전이나 후에 XML 조각을 수정할 수도 있습니다. 다음 예제에서는 프로젝트 하위 유형과 관련된 속성을 포함하는 파일의 이름이 해당 프로젝트 하위 유형으로 전달되는 프로젝트 파일에서 발췌한 정보를 보여 주었습니다.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>참조
- [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)
