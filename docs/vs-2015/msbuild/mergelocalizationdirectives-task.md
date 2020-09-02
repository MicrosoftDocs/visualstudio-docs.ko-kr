---
title: MergeLocalizationDirectives 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d6c2aa6cea687119e69b565da5468e8fa723641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703404"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> 작업은 하나 이상의 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 이진 형식 파일에 대한 지역화 특성과 주석을 전체 어셈블리에 대한 단일 파일로 병합합니다.  
  
## <a name="task-parameters"></a>작업 매개 변수  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|필수 **ITaskItem[]** 매개 변수입니다.<br /><br /> 개별 파일에 대한 지역화 지시문 파일 목록을 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 이진 형식으로 지정합니다.|  
|`OutputFile`|필수 **String** 출력 매개 변수입니다.<br /><br /> 컴파일된 지역화 지시문 어셈블리의 출력 경로를 지정합니다.|  
  
## <a name="remarks"></a>설명  
 지역화 특성 및 주석을 [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] 내용에 추가할 수 있습니다. [!INCLUDE[TLA#tla_wpf](../includes/tlasharptla-wpf-md.md)] 지역화 지원을 사용하면 지역화 특성 및 주석을 제거하고 생성된 어셈블리와는 별개인 .loc 파일에 추가할 수 있습니다. 이 작업은 **LocalizationPropertyStorage** 특성을 사용하여 수행할 수 있습니다. 지역화 특성 및 주석과 **LocalizationPropertyStorage**에 대한 자세한 내용은 [지역화 특성 및 주석](https://msdn.microsoft.com/library/ead2d9ac-b709-4ec1-a924-39927a29d02f)을 참조하세요.  
  
## <a name="example"></a>예제  
 다음 예제에서는 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] 이진 형식 파일에 해당하는 지역화 주석을 단일 .loc 파일에 병합합니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>관련 항목  
 [WPF MSBuild 참조](../msbuild/wpf-msbuild-reference.md)   
 [작업 참조](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild 참조](../msbuild/msbuild-reference.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)   
 [WPF 애플리케이션 빌드(WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
