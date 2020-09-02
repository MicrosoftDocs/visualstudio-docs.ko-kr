---
title: GenerateBootstrapper 작업 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 488caf02a20b4f0855df1ba2ef64c85e70e1a6a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149639"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

애플리케이션과 해당 필수 조건을 검색, 다운로드, 설치할 수 있는 자동화된 방법을 제공합니다. 이 작업은 애플리케이션을 구성하는 모든 구성 요소에 대한 개별 설치 관리자를 통합하는 단일 설치 관리자로 사용됩니다.  
  
## <a name="task-parameters"></a>작업 매개 변수  
 다음 표에서는 `GenerateBootstrapper` 작업의 매개 변수에 대해 설명합니다.  
  
- `ApplicationFile`  
  
   선택적 `String` 매개 변수입니다.  
  
   모든 필수 조건이 설치된 후 부트스트래퍼가 애플리케이션의 설치를 시작하는 데 사용할 파일을 지정합니다. `BootstrapperItems` 및 `ApplicationFile` 매개 변수를 둘 다 지정하지 않으면 빌드 오류가 발생합니다.  
  
- `ApplicationName`  
  
   선택적 `String` 매개 변수입니다.  
  
   부트스트래퍼가 설치할 애플리케이션의 이름을 지정합니다. 이 이름은 설치 중에 부트스트래퍼가 사용하는 UI에 표시됩니다.  
  
- `ApplicationRequiresElevation`  
  
   선택적 `Boolean` 매개 변수입니다.  
  
   `true`인 경우 구성 요소는 대상 컴퓨터에 설치될 때 관리자 권한으로 실행됩니다.  
  
- `ApplicationUrl`  
  
   선택적 `String` 매개 변수입니다.  
  
   애플리케이션의 설치 관리자를 호스트 중인 웹 위치를 지정합니다.  
  
- `BootstrapperComponentFiles`  
  
   선택적 `String[]` 출력 매개 변수입니다.  
  
   부트스트래퍼 패키지 파일의 빌드된 위치를 지정합니다.  
  
- `BootstrapperItems`  
  
   선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.  
  
   부트스트래퍼에 빌드할 제품을 지정합니다. 이 매개 변수에 전달된 항목에는 다음 구문이 포함되어야 합니다.  
  
  ```  
  <BootstrapperItem  
      Include="ProductCode">  
      <ProductName>  
          ProductName  
      </ProductName>  
  </BootstrapperItem>  
  ```  
  
   `Include` 특성은 설치해야 하는 필수 조건의 이름을 나타내는 데 사용됩니다. `ProductName` 항목 메타데이터는 선택 사항이고, 패키지를 찾을 수 없는 경우 빌드 엔진에서 사용자에게 친숙한 이름으로 사용됩니다. `ApplicationFile`을 지정할 경우에만 이러한 항목이 필수 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 입력 매개 변수입니다. 애플리케이션용으로 설치되어야 하는 필수 조건별로 하나의 항목을 포함해야 합니다.  
  
   `BootstrapperItems` 및 `ApplicationFile` 매개 변수를 둘 다 지정하지 않으면 빌드 오류가 발생합니다.  
  
- `BootstrapperKeyFile`  
  
   선택적 `String` 출력 매개 변수입니다.  
  
   setup.exe의 빌드 위치를 지정합니다.  
  
- `ComponentsLocation`  
  
   선택적 `String` 매개 변수입니다.  
  
   설치할 설치 필수 조건을 검색할 부트스트래퍼의 위치를 지정합니다. 이 매개 변수는 다음 값 중 하나를 가질 수 있습니다.  
  
  - `HomeSite`: 필수 구성 요소가 구성 요소 공급업체에서 호스트되고 있음을 나타냅니다.  
  
  - `Relative`: 필수 조건이 애플리케이션의 같은 위치에 있음을 나타냅니다.  
  
  - `Absolute`: 모든 구성 요소를 중앙 URL에서 찾을 수 있음을 나타냅니다. 이 값은 `ComponentsUrl` 입력 매개 변수와 함께 사용해야 합니다.  
  
    `ComponentsLocation`을 지정하지 않으면 기본적으로 `HomeSite`가 사용됩니다.  
  
- `ComponentsUrl`  
  
   선택적 `String` 매개 변수입니다.  
  
   설치 필수 조건을 포함하는 URL을 지정합니다.  
  
- `CopyComponents`  
  
   선택적 `Boolean` 매개 변수입니다.  
  
   `true`인 경우 부트스트래퍼가 모든 출력 파일을 `OutputPath` 매개 변수에서 지정된 경로에 복사합니다. `BootstrapperComponentFiles` 매개 변수 값은 모두 이 경로에 기반을 둡니다. `false`인 경우 파일이 복사되지 않고 `BootstrapperComponentFiles` 값은 `Path` 매개 변수 값에 기반을 둡니다.  이 매개 변수의 기본값은 `true`입니다.  
  
- `Culture`  
  
   선택적 `String` 매개 변수입니다.  
  
   부트스트래퍼 UI 및 설치 필수 조건에 사용할 문화권을 지정합니다. 지정된 문화권을 사용할 수 없는 경우 작업에는 `FallbackCulture` 매개 변수 값이 사용됩니다.  
  
- `FallbackCulture`  
  
   선택적 `String` 매개 변수입니다.  
  
   부트스트래퍼 UI 및 설치 필수 조건에 사용할 보조 문화권을 지정합니다.  
  
- `OutputPath`  
  
   선택적 `String` 매개 변수입니다.  
  
   setup.exe 및 모든 패키지 파일을 복사할 위치를 지정합니다.  
  
- `Path`  
  
   선택적 `String` 매개 변수입니다.  
  
   사용 가능한 모든 필수 조건 패키지의 위치를 지정합니다.  
  
- `SupportUrl`  
  
   선택적 `String` 매개 변수입니다.  
  
   부트스트래퍼 설치가 실패할 경우 제공할 URL을 지정합니다.  
  
- `Validate`  
  
   선택적 `Boolean` 매개 변수입니다.  
  
   `true`인 경우 부트스트래퍼가 지정된 입력 부트스트래퍼 항목에 대해 XSD 유효성 검사를 수행합니다. 이 매개 변수의 기본값은 `false`입니다.  
  
## <a name="remarks"></a>설명  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명의 목록은 [Taskextension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조 하세요.  
  
## <a name="example"></a>예제  
 다음 예제에서는 `GenerateBootstrapper` 작업을 사용하여 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]가 필수 조건으로 설치되어야 하는 애플리케이션을 설치합니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">  
            <ProductName>Microsoft .NET Framework 2.0</ProductName>  
        </BootstrapperFile>  
    </ItemGroup>  
  
    <Target Name="BuildBootstrapper">  
        <GenerateBootstrapper  
            ApplicationFile="WindowsApplication1.application"  
            ApplicationName="WindowsApplication1"  
            ApplicationUrl="http://mycomputer"  
            BootstrapperItems="@(BootstrapperFile)"  
            OutputPath="C:\output" />  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>관련 항목  
 [임무](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)
