---
title: 단일 파일 생성기 등록 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cea2ebba4739695393447a36e9842ade1670954
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705806"
---
# <a name="registering-single-file-generators"></a>단일 파일 생성기 등록
에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]사용자 지정 도구를 사용할 수 있도록 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 하려면 을 인스턴스화하고 특정 프로젝트 유형과 연결할 수 있도록 등록해야 합니다.

### <a name="to-register-a-custom-tool"></a>사용자 지정 도구를 등록하려면

1. 사용자 지정 도구 DLL을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 로컬 레지스트리 또는 시스템 레지스트리에 HKEY_CLASSES_ROOT.

    예를 들어 관리되는 MSDataSetGenerator 사용자 지정 도구에 대한 등록 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]정보는 다음과 같습니다.

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]
   @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"
   "ThreadingModel"="Both"
   "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"
   "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"
   ```

2. 특정 언어의 프로젝트 시스템 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 또는 서비스에\\의해 *GUID* 정의된 GUID인 생성기*GUID에서* 원하는 하이브에 레지스트리 키를 만듭니다. 키의 이름은 사용자 지정 도구의 프로그래밍 이름이 됩니다. 사용자 지정 도구 키에는 다음과 같은 값이 있습니다.

   - (기본값)

        (선택 사항) 사용자 지정 도구에 대한 사용자 친화적인 설명을 제공합니다. 이 매개 변수는 선택 사항이지만 권장됩니다.

   - CLSID

        필수 사항입니다. 을 구현하는 COM 구성 요소의 클래스 라이브러리의 식별자를 지정합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>

   - 생성 디자인타임소스

        필수 사항입니다. 이 사용자 지정 도구에서 생성된 파일의 형식이 시각적 디자이너가 사용할 수 있는지 여부를 나타냅니다. 시각적 디자이너가 사용할 수 없는 형식의 경우 이 매개 변수의 값은 (0) 0이어야 하며 시각적 디자이너가 사용할 수 있는 형식의 경우 (1) 1이어야 합니다.

   > [!NOTE]
   > 사용자 지정 도구를 사용할 수 있도록 하려는 각 언어에 대해 사용자 지정 도구를 별도로 등록해야 합니다.

    예를 들어 MSDataSetGenerator는 각 언어에 대해 한 번 자신을 등록합니다.

   ```
   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]
   @="Microsoft VB Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]
   @="Microsoft C# Code Generator for XSD"
   "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"
   "GeneratesDesignTimeSource"=dword:00000001
   ```

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>
- [단일 파일 생성기 구현](../../extensibility/internals/implementing-single-file-generators.md)
- [비주얼 디자이너에 형식 노출](../../extensibility/internals/exposing-types-to-visual-designers.md)
- [BuildManager 개체 소개](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
