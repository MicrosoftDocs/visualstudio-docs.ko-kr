---
title: Vspackage 등록 및 등록 취소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6bc85fb00c15831dcf1a9f64e4b886272df218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193825"
---
# <a name="registering-and-unregistering-vspackages"></a>VSPackage 등록 및 등록 취소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

특성을 사용 하 여 VSPackage를 등록 하지만  
  
## <a name="registering-a-vspackage"></a>VSPackage 등록  
 특성을 사용 하 여 관리 되는 Vspackage의 등록을 제어할 수 있습니다. 모든 등록 정보는 .pkgdef 파일에 포함 되어 있습니다. 파일 기반 등록에 대 한 자세한 내용은 [Createpkgdef 유틸리티](../extensibility/internals/createpkgdef-utility.md)를 참조 하세요.  
  
 다음 코드에서는 표준 등록 특성을 사용 하 여 VSPackage를 등록 하는 방법을 보여 줍니다.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>확장 등록 취소  
 다양 한 Vspackage를 실험 한 후 실험적 인스턴스에서 제거 하려는 경우 **Reset** 명령만 실행 하면 됩니다. 컴퓨터의 시작 페이지에서 **Visual Studio 실험적 인스턴스 다시 설정** 을 찾거나 명령줄에서 다음 명령을 실행 합니다.  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Visual Studio의 개발 인스턴스에 설치한 확장을 제거 하려면 **도구/확장 및 업데이트**로 이동 하 여 확장을 찾은 다음 **제거**를 클릭 합니다.  
  
 어떤 이유로 든 확장을 제거 하는 데 이러한 메서드가 모두 성공 하지 못하는 경우 다음과 같이 명령줄에서 VSPackage 어셈블리를 등록 취소할 수 있습니다.  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSPackages](../extensibility/internals/vspackages.md)
