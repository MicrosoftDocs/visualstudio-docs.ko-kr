---
title: 프로젝트의 참조 관리 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ProjectPropertiesReferencePaths
- cs.ProjectPropertiesReferencePaths
helpviewer_keywords:
- Visual C# projects, references
- referencing objects, project references
- external component references
- referencing namespaces
- Visual Basic projects, references
- referencing components, external components
- Web references, types of project references
- namespaces [Visual Studio], referencing
- COM components, referencing
- objects [Visual Studio], referencing
ms.assetid: 05d1c51b-44f3-4973-8a11-6c919b08ad62
caps.latest.revision: 55
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1f2f3c26d89616f083c218c6b11610fe5e329a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651323"
---
# <a name="managing-references-in-a-project"></a>프로젝트의 참조 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

외부 구성 요소 또는 연결된 서비스에 대해 코드를 작성하기 전에 프로젝트에 이에 대한 참조가 포함되어 있어야 합니다. 참조는 기본적으로 Visual Studio에서 구성 요소 또는 서비스를 찾기 위해 필요로 하는 정보를 포함하는 프로젝트 파일의 항목입니다.

 참조를 추가하려면 솔루션 탐색기에서 참조 노드를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다. 자세한 내용은 [방법: 참조 관리자를 사용하여 참조 추가 또는 제거](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)를 참조하세요.

 ![Visual C&#43;&#43;에서 참조 추가](../ide/media/vs2015-cpp-add-reference.png "vs2015_cpp_add_reference")

 다음 형식의 구성 요소/서비스에 대한 참조를 만들 수 있습니다.

- Windows 스토어 앱 참조

- .NET Framework 클래스 라이브러리 또는 어셈블리

- COM 구성 요소

- 동일 솔루션에 있는 다른 어셈블리 또는 프로젝트의 클래스 라이브러리

- XML Web services

## <a name="windows-store-app-references"></a>Windows 스토어 앱 참조

### <a name="project-references"></a>프로젝트 참조
 Windows 10을 대상으로 하는 UWP(유니버설 Windows 플랫폼) 프로젝트는 Windows 10에서 더 이상 사용되지 않는 API를 사용하지 않는 경우 솔루션의 다른 UWP 프로젝트나 Windows 스토어 프로젝트에 대한 참조나 [!INCLUDE[win81](../includes/win81-md.md)]을 대상으로 하는 또는 이진 파일을 만들 수 있습니다. 자세한 내용은 [Windows 런타임 8에서 UWP로 이동](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx)을 참조하세요.

 [!INCLUDE[win81](../includes/win81-md.md)] 프로젝트 대상을 Windows 10으로 다시 지정하도록 선택하는 경우 [Visual Studio 프로젝트 이식, 마이그레이션, 업그레이드](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)를 참조하세요.

### <a name="extension-sdk-references"></a>확장 SDK 참조
 UWP(유니버설 Windows 플랫폼)를 대상으로 하는 Visual Basic, C#, C++, JavaScript Windows 스토어 프로젝트는 [!INCLUDE[win81](../includes/win81-md.md)]을 대상으로 하는 확장 SDK가 Windows 10에서 더 이상 사용되지 않는 API를 사용하지 않는 한 이 확장 SDK를 참조할 수 있습니다. UWP를 대상으로 하는 Windows 저장소 프로젝트에서 확장 SDK를 참조할 수 있는지 확인하려면 해당 확장 SDK의 공급업체 사이트를 참조하세요.

 앱에서 참조하는 확장 SDK가 지원되지 않는 경우 다음 단계를 수행해야 합니다.

1. 오류를 일으키는 프로젝트의 이름을 확인합니다. 프로젝트의 대상 플랫폼이 프로젝트 이름 옆의 괄호 안에 표시됩니다. 예를 들어 **MyProjectName (Windows 8.1)** 은 **MyProjectName** 프로젝트가 플랫폼 버전 [!INCLUDE[win81](../includes/win81-md.md)]을 대상으로 한다는 것을 의미합니다.

2. 지원되지 않는 확장 SDK를 소유한 공급업체의 사이트로 이동하여 프로젝트의 대상 플랫폼 버전과 호환되는 종속성으로 확장 SDK 버전을 설치합니다.

    > [!NOTE]
    > 다른 확장 SDK에 대한 종속성이 있는 확장 SDK에서 Visual Studio를 다시 시작할지 여부를 확인하려면 새 C# Windows 스토어 프로젝트를 만들고 해당 프로젝트를 마우스 오른쪽 단추를 클릭한 후 **참조 추가**를 선택하여 **Windows** 탭의 **확장** 하위 탭으로 이동한 후 확장 SDK를 선택하고 **참조 관리자**의 오른쪽 창을 확인합니다. 종속성이 있는 경우 나열됩니다.

    > [!IMPORTANT]
    > 프로젝트가 Windows 10을 대상으로 하고 이전에 설치된 확장 SDK가 Microsoft Visual C++ 런타임 패키지에 종속된 경우 Windows 10과 호환되는 Microsoft Visual C++ 런타임 패키지의 버전은 v14.0이고 Visual Studio 2015와 함께 설치됩니다.

3. 이전에 설치한 확장 SDK가 다른 확장 SDK에 종속된 경우 종속성을 소유한 공급업체의 사이트로 이동하여 프로젝트의 대상 플랫폼 버전과 호환되는 종속성 버전을 설치합니다.

4. Visual Studio를 다시 시작하고 앱을 엽니다.

5. 오류가 발생한 프로젝트에서 **참조** 노드를 마우스 오른쪽 단추로 클릭한 다음 **참조 추가**를 선택합니다.

6. **Windows** 탭과 **확장** 하위 탭을 차례로 클릭 한 다음 이전 확장 sdk에 대 한 확인란의 선택을 취소 하 고 새 확장 sdk에 대 한 확인란을 선택 합니다. **확인**을 클릭합니다.

## <a name="adding-a-reference-at-design-time"></a>디자인 타임에 참조 추가
 프로젝트에서 어셈블리에 대한 참조를 만드는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에서는 다음 위치에서 어셈블리를 검색합니다.

- 현재 프로젝트 디렉터리. 이 어셈블리는 **찾아보기** 탭을 통해 찾을 수 있습니다.

- 같은 솔루션에 있는 다른 프로젝트 디렉터리. 이러한 어셈블리는 **프로젝트** 탭에서 찾을 수 있습니다.

> [!NOTE]
> 모든 프로젝트에는 mscorlib에 대한 암시적 참조가 포함되어 있습니다. Visual Basic 프로젝트에는 `Microsoft.VisualBasic`에 대한 암시적 참조가 포함되어 있습니다.
>
> Visual Studio에서는 `System.Core`가 참조 목록에서 제거된 경우를 포함한 모든 프로젝트에 `System.Core` 에 대한 암시적 참조가 포함되어 있습니다.

## <a name="references-to-shared-components-at-run-time"></a>런타임의 공유 구성 요소에 대한 참조
 런타임에 구성 요소는 프로젝트의 출력 경로 또는 GAC ( [전역 어셈블리 캐시](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) )에 있어야 합니다. 프로젝트에 이러한 위치 중 하나에 없는 개체에 대한 참조가 포함되어 있는 경우 프로젝트를 빌드할 때 프로젝트의 출력 경로에 대한 참조를 복사해야 합니다. <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> 속성은 복사본을 만들 수 있는지 여부를 나타냅니다. 값이 **True**이면 프로젝트를 빌드할 때 참조가 프로젝트 디렉터리에 복사됩니다. 값이 **False**이면 참조가 복사되지 않습니다.

 GAC에 등록되어 있는 사용자 지정 구성 요소에 대한 참조가 포함된 애플리케이션을 배포하는 경우 구성 요소는 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> 설정과 관계없이 애플리케이션과 함께 배포되지 않습니다. 이전 버전의 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서는 어셈블리가 배포되었는지 확인하기 위해 참조에 대한 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> 속성을 설정할 수 있습니다. 이제 \Bin 폴더에 어셈블리를 수동으로 추가해야 합니다. 그러면 모든 사용자 지정 코드가 조사되어 친숙하지 않은 사용자 지정 코드를 게시할 가능성이 줄어듭니다.

 어셈블리 또는 구성 요소를 전역 어셈블리 캐시 내에 있거나 프레임워크 구성 요소인 경우 기본적으로 <xref:Microsoft.VisualStudio.VCProjectEngine.VCProjectReference.CopyLocal%2A> 속성은 **False** 입니다. 그렇지 않으면 이 속성의 값은 **True**로 설정됩니다. 프로젝트 간 참조는 항상 **True**로 설정됩니다.

## <a name="referencing-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>다른 버전의.NET Framework를 대상으로 하는 프로젝트 또는 어셈블리 참조
 다른 .NET Framework 버전을 대상으로 하는 프로젝트나 어셈블리를 참조하는 애플리케이션을 만들 수 있습니다. 예를 들어, [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] 을 대상으로 하는 어셈블리를 참조하는 [!INCLUDE[dnprdnext](../includes/dnprdnext-md.md)]을 대상으로 하는 애플리케이션을 만들 수도 있습니다. 이전 버전의 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]를 대상으로 하는 프로젝트를 만드는 경우 해당 프로젝트에서 [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] 또는 .NET Framework 버전 4를 대상으로 하는 프로젝트나 어셈블리에 대한 참조를 설정할 수 없습니다.

 자세한 내용은 [특정 대상 .NET Framework 버전 지정](../ide/targeting-a-specific-dotnet-framework-version.md)을 참조하세요.

## <a name="project-to-project-references"></a>프로젝트 간 참조
 프로젝트 간 참조는 어셈블리가 포함 된 프로젝트에 대 한 참조입니다. **프로젝트 탭을** 사용 하 여 만들 수 있습니다. 프로젝트에 대 한 경로가 지정 되 면 Visual Studio에서 어셈블리를 찾을 수 있습니다.

 어셈블리를 생성하는 프로젝트를 사용하는 경우에는 프로젝트를 참조하고 파일 참조(아래 참조)를 사용하지 말아야 합니다. 프로젝트 간 참조의 이점은 빌드 시스템에서 프로젝트 간의 종속성을 만들 수 있다는 점입니다. 참조하는 프로젝트가 마지막으로 빌드된 이후 변경된 경우 종속 프로젝트가 빌드됩니다. 파일 참조는 빌드 종속성을 만들지 않습니다. 따라서 종속 프로젝트를 빌드하지 않고 참조되는 프로젝트를 빌드할 수 있으며 해당 참조가 더 이상 사용되지 않습니다. (즉, 프로젝트가 이전에 빌드된 프로젝트 버전을 참조할 수 있습니다.) 그러면 bin 디렉터리에 여러 버전의 단일 DLL이 필요하게 되는데 이것은 불가능합니다. 이러한 충돌이 발생 하면 [경고: ' project ' 프로젝트의 ' file ' 종속성이 ' file ' 참조를 덮어쓰므로 실행 디렉터리에 복사할 수 없습니다](../misc/warning-the-dependency-file-in-project-project-cannot-be-copied.md).와 같은 메시지가 표시 됩니다. 자세한 내용은 [Troubleshooting Broken References](../ide/troubleshooting-broken-references.md) 및 [How to: Create and Remove Project Dependencies](../ide/how-to-create-and-remove-project-dependencies.md)를 참조하세요.

> [!NOTE]
> 한 프로젝트의 대상 .NET Framework 버전이 버전 4.5이고 다른 프로젝트의 대상 버전이 버전 2, 3, 3.5 또는 4.0인 경우 프로젝트 간 참조 대신 파일 참조가 만들어집니다.

## <a name="file-references"></a>파일 참조
 파일 참조는 Visual Studio 프로젝트의 컨텍스트 외부에서 어셈블리에 대한 직접 참조로서, **참조 관리자** 의 **찾아보기**탭을 사용하여 만들 수 있습니다. 어셈블리나 구성 요소는 있고 출력으로서 작성하는 프로젝트는 없는 경우 파일 참조를 사용하세요.

## <a name="see-also"></a>관련 항목
 [끊어진 참조](../ide/troubleshooting-broken-references.md) [어셈블리를 사용한 프로그래밍](https://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6) 문제 해결 [방법: 참조 관리자를 사용 하 여 참조 추가 또는 제거](../ide/how-to-add-or-remove-references-by-using-the-reference-manager.md)
