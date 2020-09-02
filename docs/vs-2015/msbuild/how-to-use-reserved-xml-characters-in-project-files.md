---
title: '방법: 프로젝트 파일에서 예약된 XML 문자 사용 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aba17e94486ca04e12055c7bf9959f927440c53d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178304"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>방법: 프로젝트 파일에서 예약된 XML 문자 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

프로젝트 파일을 작성할 경우 속성 값이나 작업 매개 변수 값 등에서 예약된 XML 문자를 사용해야 합니다. 그러나 프로젝트 파일을 구문 분석할 수 있도록 일부 예약된 문자를 명명된 엔터티로 바꿔야 합니다.  
  
## <a name="using-reserved-characters"></a>예약된 문자 사용  
 다음 표에서는 프로젝트 파일을 구문 분석할 수 있도록 해당 명명된 엔터티로 대체되어야 하는 예약된 XML 문자를 설명합니다.  
  
|예약된 문자|명명된 엔터티|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>프로젝트 파일에서 큰따옴표를 사용하려면  
  
- 큰따옴표를 해당 명명된 엔터티 &quot;로 바꿉니다. 예를 들어 `EXEFile` 항목 목록 주위에 큰따옴표를 배치하려면 다음을 입력합니다.  
  
    ```  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>예  
 다음 코드 예제에서는 프로젝트 파일에서 출력된 메시지에서 파일 이름을 강조 표시할 때 큰따옴표가 사용됩니다.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is "@(EXEFile)"."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>관련 항목  
 [MSBuild 참조](../msbuild/msbuild-reference.md) [MSBuild](msbuild.md)
