---
title: IDE에서 빌드 시작 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- build
ms.assetid: 936317aa-63b7-4eb0-b9db-b260a0306196
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94685a2b06b14c232d9e1f79a1d7440e1ceb765b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161337"
---
# <a name="starting-a-build-from-within-the-ide"></a>IDE에서 빌드 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 지정 프로젝트 시스템은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor>를 사용하여 빌드를 시작해야 합니다. 이 항목에서는 이에 대한 이유를 설명하고 프로시저를 간략하게 설명합니다.  
  
## <a name="parallel-builds-and-threads"></a>병렬 빌드 및 스레드  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]는 공통 리소스에 액세스하기 위한 중재를 필요로 하는 병렬 빌드를 허용합니다. 프로젝트 시스템은 빌드를 비동기적으로 실행할 수 있지만 이러한 시스템은 빌드 관리자에게 다시 제공되는 호출 내에서 빌드 함수를 호출하지 않아야 합니다.  
  
 프로젝트 시스템이 환경 변수를 수정할 경우 빌드의 NodeAffinity를 OutOfProc로 설정해야 합니다. 즉, in-proc 노드가 필요하므로 호스트 개체를 사용할 수 없습니다.  
  
## <a name="using-ivsbuildmanageraccessor"></a>IVSBuildManagerAccessor 사용  
 아래 코드는 프로젝트 시스템이 빌드를 시작하는 데 사용할 수 있는 메서드를 간략하게 설명합니다.  
  
```  
  
public bool Build(Project project, bool isDesignTimeBuild)  
{  
    // Get the accessor from the IServiceProvider interface for the   
    // project system  
    IVsBuildManagerAccessor accessor =  
        serviceProvider.GetService(typeof(SVsBuildManagerAccessor)) as     
        IVsBuildManagerAccessor;  
    bool releaseUIThread = false;  
    try  
    {  
        if(accessor != null)  
        {  
            // Claim the UI thread under the following conditions:  
            // 1. The build must use a resource that uses the UI thread  
            // or,  
            // 2. The build requires the in-proc node AND waits on the   
            // UI thread for the build to complete  
            if(NeedsUIThread)  
            {  
                int result = accessor.ClaimUIThreadForBuild();  
                if(result != S_OK)  
                {  
                     // Not allowed to claim the UI thread right now  
                     return false;  
                }  
                releaseUIThread = true;  
             }  
             if(isDesignTimeBuild)  
             {  
// Start the design time build  
                  int result = accessor.BeginDesignTimeBuild();  
                  if(result != S_OK)  
                  {  
                      // Not allowed to begin a design-time build at  
                      // this time. Try again later.  
                      return false;  
                  }  
             }  
         }  
         bool buildSucceeded = false;  
         // perform project-system specific build set up tasks  
         // Create your BuildRequestData  
         // This assumes a IHostServices variable (hostServices) set   
   // to your host services. If you don't use a project instance   
         // (you build from a file for example) then use another   
         // constructor.  
         BuildRequestData requestData = new   
             BuildRequestData(project.CreateProjectInstance(),   
             "myTarget", hostServices,   
             BuildRequestData.BuildRequestDataFlags.None);  
         // Mark your your submission as Pending  
         BuildSubmission submission =  
              BuildManager.DefaultBuildManager.  
              PendBuildRequest(requestData);  
         // Register the loggers in BuildLoggers  
         if (accessor != null)  
         {  
               foreach (ILogger logger in BuildLoggers)  
               {  
                    accessor.RegisterLogger(submission.SubmissionId,   
                        logger);  
               }  
         }  
         BuildResult buildResult = submission.Execute();  
         return buildResult;  
     }  
     // Clean up resources  
     finally  
     {  
         if(accessor != null)  
         {  
             // Unregister the loggers, if necessary.  
             accessor.UnregisterLoggers(submission.SubmissionId);  
             // Release the UI thread, if used  
             if(releaseUIThread)  
             {  
                  accessor.ReleaseUIThreadForBuild();  
             }  
             // End the design time build, if used  
             if(isDesignTimeBuild)  
             {  
                  accessor.EndDesignTimeBuild();  
             }  
         }  
     }  
}  
  
```
