---
title: '방법: 계측할 Web.Config 파일 수정 및 동적으로 컴파일된 ASP.NET 웹 애플리케이션 프로파일링 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d9e4fc4dfdff336b9ddcbd04bd031b48a8acc4dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841546"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>방법: 계측할 Web.Config 파일 수정 및 동적으로 컴파일된 ASP.NET 웹 애플리케이션 프로파일링
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로파일링 도구 계측 방법을 사용하여 동적으로 컴파일된 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션에서 세부 타이밍 데이터, .NET 메모리 할당 데이터 및 .NET 개체 수명 데이터를 수집할 수 있습니다.  
  
 이 항목에서는 web.config 구성 파일을 수정하여 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션의 계측 및 프로파일링을 사용하도록 설정하는 방법을 설명합니다.  
  
> [!NOTE]
> 샘플링 프로파일링 방법을 사용할 경우 또는 미리 컴파일된 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 모듈을 계측하고자 할 경우 web.config 파일을 수정할 필요가 없습니다.  
  
 web.config 파일의 루트는 **configuration** 요소입니다. 동적으로 컴파일된 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션을 계측 및 프로파일링하려면 다음 요소를 추가하거나 수정해야 합니다.  
  
- **configuration/runtime/assemblyBinding/dependentAssembly** 요소 - 프로파일링을 제어하는 Microsoft.VisualStudio.Enterprise.ASPNetHelper 어셈블리를 식별합니다. **dependentAssembly** 요소에는 두 개의 자식 요소인 **assemblyIdentity** 및 **codeBase**가 포함됩니다.  
  
- **configuration/system.web/compilation** 요소 - 대상 어셈블리에 대한 프로파일러 사후 처리 컴파일 단계를 식별합니다.  
  
- 프로파일링 도구의 위치를 식별하는 두 개의 **add** 요소가 **configuration/appSettings** 섹션에 추가됩니다.  
  
  애플리케이션 구성을 복원하는 데 사용할 수 있는 원래 web.config 파일의 복사본을 만드는 것이 좋습니다.  
  
### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>ASPNetHelper 어셈블리를 configuration/runtime/assemblyBinding/dependentAssembly 요소로 추가하려면  
  
1. 필요한 경우 **runtime** 요소를 **configuration** 요소의 자식 요소로 추가하고, 그렇지 않으면 다음 단계로 이동합니다.  
  
     **runtime** 요소에는 특성이 없습니다. **configuration** 요소에는 하나의 **runtime** 자식 요소만 포함될 수 있습니다.  
  
2. 필요한 경우 **assemblyBinding** 요소를 **runtime** 요소의 자식 요소로 추가하고, 그렇지 않으면 다음 단계로 이동합니다.  
  
     **runtime** 요소에는 하나의 **assemblyBinding** 요소만 포함될 수 있습니다.  
  
3. 다음 특성 이름 및 값을 **assemblyBinding** 요소에 추가합니다.  
  
    |특성 이름|특성 값|  
    |--------------------|---------------------|  
    |**Xmlns**|**urn:schemas-microsoft-com:asm.v1**|  
  
4. **dependentAssembly** 요소를 **assemblyBinding** 요소의 자식 요소로 추가합니다.  
  
     **dependentAssembly** 요소에는 특성이 없습니다.  
  
5. **assemblyIdentity** 요소를 **dependentAssembly** 요소의 자식으로 추가합니다.  
  
6. 다음 특성 이름 및 값을 **assemblyIdentity** 요소에 추가합니다.  
  
    |특성 이름|특성 값|  
    |--------------------|---------------------|  
    |**name**|**Microsoft.VisualStudio.Enterprise.ASPNetHelper**|  
    |**PublicKeyToken**|**b03f5f7f11d50a3a**|  
    |**culture**|**Neutral**|  
  
7. **codeBase** 요소를 **dependentAssembly** 요소의 자식으로 추가합니다.  
  
8. 다음 특성 이름 및 값을 **codeBase** 요소에 추가합니다.  
  
    |특성 이름|특성 값|  
    |--------------------|---------------------|  
    |**version**|**10.0.0.0**|  
    |**href**|`PathToASPNetHelperDll`|  
  
     `PathToASPNetHelperDll`은 Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll의 파일 URL입니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]가 기본 위치에 설치된 경우 **href** 값은 `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`이어야 합니다.  
  
```  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity                         name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"                         culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
```  
  
### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>프로파일러 사후 처리 단계를 configuration/system.web/compilation 요소에 추가하려면  
  
1. 필요한 경우 **system.web** 요소를 **configuration** 요소의 자식 요소로 추가하고, 그렇지 않으면 다음 단계로 이동합니다.  
  
     **system.web** 요소에는 특성이 없습니다. **configuration** 요소에는 하나의 **system.web** 자식 요소만 포함될 수 있습니다.  
  
2. 필요한 경우 **compilation** 요소를 **system.web** 요소의 자식 요소로 추가하고, 그렇지 않으면 다음 단계로 이동합니다.  
  
     **system.web** 요소에는 하나의 **compilation** 자식 요소만 포함될 수 있습니다.  
  
3. **compilation** 요소에서 기존 특성을 제거하고 다음 특성 이름 및 값을 추가합니다.  
  
    |특성 이름|특성 값|  
    |--------------------|---------------------|  
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a**|  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
    <configuration>  
```  
  
### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>configuration/appSettings 요소에 프로파일러 위치 설정을 추가하려면  
  
1. 필요한 경우 **appSettings** 요소를 **configuration** 요소의 자식 요소로 추가하고, 그렇지 않으면 다음 단계로 이동합니다.  
  
     **appSettings** 요소에는 특성이 없습니다. **configuration** 요소에는 하나의 **appSettings** 자식 요소만 포함될 수 있습니다.  
  
2. **add** 요소를 **appSettings** 요소의 자식으로 추가합니다.  
  
3. 다음 특성 이름 및 값을 **add** 요소에 추가합니다.  
  
    |특성 이름|특성 값|  
    |--------------------|---------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation**|  
    |**value**|`PerformanceToolsFolder` **\VSInstr.Exe**|  
  
4. 또 다른 **add** 요소를 **appSettings** 요소의 자식으로 추가합니다.  
  
5. 다음 특성 이름 및 값을 **add** 요소에 추가합니다.  
  
    |특성 이름|특성 값|  
    |--------------------|---------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|  
    |**value**|`PerformanceToolsFolder`|  
  
     `PerformanceToolsFolder`는 프로파일러 실행 파일의 경로입니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]가 기본 위치에 설치되면 값은 **C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools**가 됩니다.  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        . . .  
        <system.web>  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
        />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
```  
  
## <a name="example"></a>예제  
 동적으로 컴파일된 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션의 계측 및 프로파일링을 사용하도록 설정하는 전체 web.config 파일은 다음과 같습니다. 이 예제에서는 수정하기 전에 파일에 다른 설정이 없었다고 가정합니다.  
  
```  
<?xml version="1.0"?>  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity   
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"  
                        culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral,  
                    PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
            />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
  
```  
  
## <a name="see-also"></a>참고 항목  
 [방법: 동적으로 컴파일된 ASP.NET 응용 프로그램 계측 및 자세한 타이밍 데이터 수집](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)   
 [방법: 동적으로 컴파일된 ASP.NET 응용 프로그램 계측 및 메모리 데이터 수집](/visualstudio/profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data?view=vs-2015)
