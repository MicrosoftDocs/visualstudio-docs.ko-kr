---
title: '방법: 수동으로 확장 패키지 (VSIX 배포) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: jillfra
ms.openlocfilehash: a615aea75ec00e49ee4d2837b8b4e2b1d20d3306
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74293615"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>방법: 수동으로 확장 패키지(VSIX 배포)
배포를 위해 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장을 래핑할 VSIX 패키지를 만들 수 있습니다. 패키지를 만드는 방법에는 다음 세 가지가 있습니다.  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK에 포함된 확장성 템플릿 중 하나를 사용하여 VSIX 패키지 프로젝트를 만듭니다. 이것이 대부분의 시나리오에서 가장 쉬운 옵션입니다.  
  
- 빈 [VSIX 프로젝트](../extensibility/vsix-project-template.md)에 확장 프로젝트의 출력을 래핑합니다. 템플릿, 지원되지 않는 어셈블리 및 사용자 지정 형식에 이 옵션을 사용하는 것이 좋습니다.  
  
- VSIX 패키지를 수동으로 만듭니다. 다른 두 옵션을 사용할 수 없는 경우에만 이 옵션을 사용하는 것이 좋습니다.  
  
  이 문서에서는 세 번째 옵션을 설명합니다.  
  
## <a name="creating-a-vsix-package"></a>VSIX 패키지 만들기  
 확장을 수동으로 패키지하려면 extension.manifest 파일 및 [Content_Types].xml 파일을 확장 프로젝트에 추가하고 빌드 출력과 함께 압축 파일에 넣은 다음 .vsix 파일 이름 확장명을 갖도록 압축 파일의 이름을 바꿉니다. 패키지할 확장은 [VSIX 스키마](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)에서 지원되는 형식이어야 합니다.  
  
> [!NOTE]
> VSIX 패키지의 파일 이름에는 [ \[ RFC2396 \] ](https://go.microsoft.com/fwlink/?LinkId=90339)아래에 정의 된 대로 URI (Uniform resource identifier)로 예약 된 문자 또는 공백을 포함 해서는 안 됩니다.  
  
#### <a name="to-manually-create-a-vsix-package"></a>VSIX 패키지를 수동으로 만들려면  
  
1. VSIX 스키마에서 지원되는 형식의 Visual Studio 확장을 만듭니다.  
  
2. XML 파일을 만들고 이름을 `extension.vsixmanifest`로 지정합니다.  
  
3. VSIX 스키마에 따라 extension.vsixmanifest 파일을 채웁니다. 예제 매니페스트는 [PackageManifest 요소(루트 요소, VSX 스키마)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)를 참조하세요.  
  
4. 두 번째 XML 파일을 만들고 이름을 `[Content_Types].xml`로 지정합니다.  
  
5. [Content_types \] .xml 파일의 구조](../extensibility/the-structure-of-the-content-types-dot-xml-file.md)에 지정 된 대로 [Content_Types] .xml 파일을 입력 합니다.  
  
6. 배포할 확장과 함께 두 XML 파일을 디렉터리에 넣습니다.  
  
     프로젝트 템플릿 또는 항목 템플릿의 경우 템플릿이 포함된 .zip 파일을 XML 파일과 동일한 폴더에 넣습니다. .zip 파일에 XML 파일을 넣지 마세요.  
  
     다른 모든 경우에는 빌드 출력과 동일한 디렉터리에 XML 파일을 넣습니다.  
  
7. Windows 탐색기에서 확장 콘텐츠 및 두 개의 XML 파일이 포함된 폴더를 마우스 오른쪽 단추로 클릭하고 **보내기**를 클릭한 다음 **압축(zip) 폴더**를 클릭합니다.  
  
8. 결과 .zip 파일의 이름을 *Filename*.vsix로 바꿉니다. 여기서 *Filename* 은 패키지를 설치하는 재배포 가능 파일의 이름입니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 확장 출시](../extensibility/shipping-visual-studio-extensions.md)   
 [VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)   
 [PackageManifest 요소(루트 요소, VSX 스키마)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)