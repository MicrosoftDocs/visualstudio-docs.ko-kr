---
title: 단일 파일 생성기 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6afcd708ac50a46ceb3359f0d2c0821e3b788f47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696097"
---
# <a name="registering-single-file-generators"></a>단일 파일 생성기 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

에서 사용자 지정 도구를 사용할 수 있도록 하려면 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 등록 해야 합니다. 이렇게 하면 해당 도구를 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 인스턴스화하고 특정 프로젝트 형식에 연결할 수 있습니다.  
  
### <a name="to-register-a-custom-tool"></a>사용자 지정 도구를 등록 하려면  
  
1. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]HKEY_CLASSES_ROOT에서 로컬 레지스트리 또는 시스템 레지스트리에 사용자 지정 도구 DLL을 등록 합니다.  
  
     예를 들어 다음은와 함께 제공 되는 관리 되는 MSDataSetGenerator 사용자 지정 도구에 대 한 등록 정보입니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2. 원하는 hive에서 생성기 guid 아래에 레지스트리 키를 만듭니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] \\ *GUID* . 여기서 *guid* 는 특정 언어의 프로젝트 시스템이 나 서비스에서 정의 된 guid입니다. 키 이름은 사용자 지정 도구의 프로그래밍 이름이 됩니다. 사용자 지정 도구 키의 값은 다음과 같습니다.  
  
    - (기본값)  
  
         선택 사항입니다. 사용자 지정 도구에 대해 사용자에 게 친숙 한 설명을 제공 합니다. 이 매개 변수는 선택 사항 이지만 권장 됩니다.  
  
    - CLSID  
  
         필수 요소. 을 구현 하는 COM 구성 요소의 클래스 라이브러리 식별자를 지정 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> .  
  
    - GeneratesDesignTimeSource  
  
         필수 요소. 이 사용자 지정 도구에서 생성 한 파일의 형식을 비주얼 디자이너에서 사용할 수 있는지 여부를 나타냅니다. 비주얼 디자이너에서 사용할 수 없는 형식에 대해이 매개 변수의 값이 0 (0) 이거나 비주얼 디자이너에서 사용할 수 있는 형식에 대해 1 (1) 이어야 합니다.  
  
    > [!NOTE]
    > 사용자 지정 도구를 사용할 수 있도록 하려는 각 언어에 대해 사용자 지정 도구를 별도로 등록 해야 합니다.  
  
     예를 들어 MSDataSetGenerator는 각 언어에 대해 한 번씩 등록 합니다.  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [단일 파일 생성기 구현](../../extensibility/internals/implementing-single-file-generators.md)   
 [프로젝트의 기본 네임 스페이스 확인](../../misc/determining-the-default-namespace-of-a-project.md)   
 [비주얼 디자이너에 형식 노출](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [BuildManager 개체 소개](https://msdn.microsoft.com/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
