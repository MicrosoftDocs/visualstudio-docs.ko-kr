---
title: MSBuild 프로젝트 파일에 데이터 유지 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 39d2ab449c3623a90dd76729b46a9f353900fc88
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704124"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild 프로젝트 파일의 데이터 유지
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 하위 형식에서 나중에 사용 하기 위해 하위 형식 관련 데이터를 프로젝트 파일에 저장 해야 할 수도 있습니다. 프로젝트 하위 유형은 프로젝트 파일 지 속성을 사용 하 여 다음 요구 사항을 충족 합니다.  
  
1. 프로젝트를 빌드하는 과정에서 사용 되는 데이터를 유지 합니다. Microsoft Build Engine에 대 한 자세한 내용은 [MSBuild](https://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)를 참조 하세요. 빌드 관련 정보는 다음 중 하나를 수행할 수 있습니다.  
  
    1. 구성 독립적인 데이터. 즉, 비어 있거나 누락 된 조건이 있는 MSBuild 요소에 저장 된 데이터입니다.  
  
    2. 구성에 종속 된 데이터입니다. 즉, 특정 프로젝트 구성에 대해 조건 화 된 MSBuild 요소에 저장 된 데이터입니다. 예를 들면 다음과 같습니다.  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2. 빌드와 관련이 없는 데이터를 유지 합니다. 이 데이터는 XML 스키마에 대해 유효성이 검사 되지 않는 자유 형식 XML로 표현 될 수 있습니다.  
  
    1. 구성 독립적인 데이터.  
  
    2. 구성에 종속 된 데이터입니다.  
  
## <a name="persisting-build-related-information"></a>빌드 관련 정보 유지  
 프로젝트를 빌드하는 데 유용한 데이터의 지 속성은 MSBuild를 통해 처리 됩니다. MSBuild 시스템은 빌드 관련 정보의 마스터 테이블을 유지 관리 합니다. 프로젝트 하위 유형은 속성 값을 가져오고 설정 하기 위해이 데이터에 액세스 하는 일을 담당 합니다. 또한 프로젝트 하위 형식은 지속형 속성을 추가 하 고 유지 되지 않도록 속성을 제거 하 여 빌드 관련 데이터 테이블을 확장할 수 있습니다.  
  
 MSBuild 데이터를 수정 하기 위해 프로젝트 하위 유형은를 통해 기본 프로젝트 시스템에서 MSBuild 속성 개체를 검색 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 는 핵심 프로젝트 시스템에서 구현 된 인터페이스 이며를 실행 하 여 집계 프로젝트 하위 형식 쿼리를 실행 `QueryInterface` 합니다.  
  
 다음 절차에서는를 사용 하 여 속성을 제거 하는 단계를 간략하게 설명 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> .  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>MSBuild 프로젝트 파일에서 속성을 제거 하려면  
  
1. `QueryInterface`프로젝트 하위 형식에 대해를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> 합니다.  
  
2. 을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> 제거 하려는 속성으로 설정 하 여를 호출 `pszPropName` 합니다.  
  
### <a name="persisting-non-build-related-information"></a>비 빌드 관련 정보 유지  
 빌드에 중요 하지 않은 프로젝트 파일의 데이터 지 속성은를 통해 처리 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>주 `project subtype aggregator` 개체, `project subtype project configuration` 개체 또는 둘 다에서를 구현할 수 있습니다.  
  
 다음은 비 빌드 관련 정보에 대 한 지 속성과 관련 된 주요 개념을 간략하게 설명 하는 것입니다.  
  
- 기본 프로젝트는 구성 독립적인 데이터를 로드 및 저장 하기 위해 주 프로젝트 하위 형식 (즉, 가장 바깥쪽 프로젝트 하위 형식)에 대해를 호출 하 고, 프로젝트 하위 형식 프로젝트 구성 개체에서를 호출 하 여 구성 종속 데이터를 로드 하거나 저장 합니다.  
  
- 기본 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 각 수준의 프로젝트 하위 형식 집계에 대해 여러 번의 메서드를 호출 하 고 각 수준에 대 한 GUID를 전달 합니다.  
  
- 기본 프로젝트는 특정 프로젝트 하위 형식에 전용으로 사용 되는 XML 조각을 전달 하거나 수신 하 고, 집계 수준 간에 상태를 유지 하는 방법으로이 메커니즘을 사용 합니다.  
  
- 기본 프로젝트는 GUID를 전달 하는 가장 바깥쪽 프로젝트 하위 형식 구현을 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> . GUID가 가장 바깥쪽 프로젝트 하위 형식에 속하는 경우 호출 자체를 처리 합니다. 그렇지 않으면 GUID에 해당 하는 프로젝트 하위 형식이 발견 될 때까지 내부 프로젝트 하위 형식에 대 한 호출을 위임 합니다.  
  
- 프로젝트 하위 형식에서 내부 프로젝트 하위 형식에 대 한 호출을 위임 하기 전이나 후에 XML 조각을 수정할 수도 있습니다. 다음 예제에서는 프로젝트 파일에서 발췌 한 부분을 보여 줍니다. 여기에서 프로젝트 하위 형식에 해당 하는 속성을 포함 하는 파일의 이름이 해당 프로젝트 하위 형식으로 전달 됩니다.  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## <a name="see-also"></a>관련 항목  
 [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)
