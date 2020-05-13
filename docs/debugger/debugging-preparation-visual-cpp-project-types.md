---
title: 프로젝트 디버그 C++ 준비 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: dc663115e98d7553e03a186874d59b75eb68cb90
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916315"
---
# <a name="debugging-preparation-c-project-types"></a>디버깅 준비: C++ 프로젝트 형식
이 단원에서는 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 프로젝트 템플릿으로 만든 기본 프로젝트 형식을 디버깅하는 방법에 대해 설명합니다.

 Dll을 출력으로 만드는 이러한 프로젝트 형식은 공유 하는 일반적인 기능으로 인해 [Dll 프로젝트로](../debugger/debugging-dll-projects.md) 그룹화 되었습니다.

## <a name="BKMK_In_this_topic"></a> 항목 내용
 [권장되는 속성 설정](#BKMK_Recommended_Property_Settings)

 [Win32 프로젝트](#BKMK_Win32_Projects)

- [C 또는 C++ Win32 애플리케이션을 디버그하려면](#BKMK_To_debug_a_C_or_C___Win32_application)

- [디버그 구성을 직접 설정하려면](#BKMK_To_manually_set_a_Debug_configuration)

  [Windows Forms 애플리케이션(.NET)](#BKMK_Windows_Forms_Applications___NET_)

## <a name="BKMK_Recommended_Property_Settings"></a> 권장되는 속성 설정
  일부 속성은 모든 관리되지 않는 디버깅 시나리오에서 동일한 방식으로 설정해야 합니다. 다음 표에는 권장 속성 설정이 나와 있습니다. 여기에 나와 있지 않은 설정은 관리되지 않는 프로젝트 형식에 따라 서로 다를 수 있습니다. 자세한 내용은 [ C++ 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)을 참조하세요.

### <a name="configuration-properties-124-cc-124-optimization-node"></a>구성 속성 &#124; C/C++ &#124; 최적화 노드

|속성 이름|설정|
|-------------------|-------------|
|**Optimization**|**사용 안 함(/0d)** 으로 설정합니다. 코드를 최적화하면, 생성되는 명령이 소스 코드에 직접 대응되지 않기 때문에 디버깅하기 어렵습니다. 최적화된 코드에만 나타나는 버그가 프로그램에서 발견될 경우에는 이 설정을 선택할 수 있습니다. 그러나 **디스어셈블리** 창에 표시되는 코드는 소스 창에 표시되는 코드와 일치하지 않는 최적화된 코드에서 생성됩니다. 단계별 실행과 같은 다른 기능이 정상적으로 작동하지 않을 수도 있습니다.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>구성 속성 &#124; 링커 &#124; 디버깅 노드

|속성 이름|설정|
|-------------------|-------------|
|**디버깅 정보 생성**|디버깅에 필요한 디버깅 기호와 파일을 만들려면 이 옵션을 항상 **예(/DEBUG)** 로 설정해야 합니다. 애플리케이션을 제품화할 때는 이 옵션을 해제할 수 있습니다.|

 [항목 내용](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Win32_Projects"></a> Win32 프로젝트
 Win32 애플리케이션은 C 또는 C++로 작성된 일반 Windows 프로그램입니다. 이러한 형식의 애플리케이션은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 쉽게 디버깅할 수 있습니다.

 Win32 애플리케이션에는 MFC 애플리케이션과 ATL 프로젝트가 포함됩니다. Win32 응용 프로그램은 Windows API를 사용하며 MFC나 ATL을 사용할 수도 있지만 CLR(공용 언어 런타임)는 사용하지 않습니다. 그러나 CLR을 사용하는 관리 코드를 호출할 수는 있습니다.

 다음은 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 내에서 Win32 프로젝트를 디버깅하는 방법을 보여 주는 절차입니다. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 외부에서 애플리케이션을 시작하고 여기에 연결하는 방법으로 Win32 애플리케이션을 디버깅할 수도 있습니다. 자세한 내용은 [실행 중인 프로세스에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조 하세요.

### <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> C 또는 C++ Win32 애플리케이션을 디버그하려면

1. Visual Studio에서 프로젝트를 엽니다.

2. **디버그** 메뉴에서 **시작**을 선택합니다.

3. [먼저 디버거를 살펴보면](../debugger/debugger-feature-tour.md)에서 설명한 기술을 사용 하 여 디버그 합니다.

### <a name="BKMK_To_manually_set_a_Debug_configuration"></a> 디버그 구성을 직접 설정하려면

1. **보기** 메뉴에서 **속성 페이지**를 클릭합니다.

2. **구성 속성** 노드가 아직 열려 있지 않으면 이 노드를 클릭하여 엽니다.

3. **일반**을 선택하고, **출력** 행의 값을 **디버그**로 설정합니다.

4. **C/C++** 노드를 열고 **일반**을 선택합니다.

    컴파일러에서 생성할 디버깅 정보의 형식을 **디버그** 행에서 지정합니다. 선택한 값에는 **프로그램 데이터베이스(/Zi)** 또는 **편집하며 계속하기를 위한 프로그램 데이터베이스(/ZI)** 가 포함될 수 있습니다.

5. **최적화**를 선택하고, **최적화** 행의 드롭다운 목록에서 **사용 안 함(/0d)** 을 선택합니다.

    코드를 최적화하면, 생성되는 명령이 소스 코드에 직접 대응되지 않기 때문에 디버깅하기 어렵습니다. 최적화된 코드에만 나타나는 버그가 프로그램에서 발견될 경우에는 이 설정을 선택할 수 있습니다. 그러나 디스어셈블리 창에 표시되는 코드는 소스 창에 표시되는 코드와 일치하지 않는 최적화된 코드에서 생성되므로, 단계별 실행 같은 기능을 수행하면 중단점과 실행 지점이 올바르게 표시되지 않을 수 있습니다.

6. **링커** 노드를 열고 **디버깅**을 선택합니다. 첫 번째 **생성** 행의 드롭다운 목록에서 **예(/DEBUG)** 를 선택합니다. 디버깅하는 경우 항상 이 값으로 설정해야 합니다.

   자세한 내용은[ C++ 디버그 구성에 대 한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)을 참조 하세요.

   [항목 내용](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Windows_Forms_Applications___NET_"></a> Windows Forms 애플리케이션(.NET)
 **Windows Forms 애플리케이션(.NET)** 템플릿은 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] Windows Forms 애플리케이션을 만드는 데 사용됩니다. 자세한 내용은 [How to: Create a Windows Application Project](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))을 참조하세요.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 이 형식의 애플리케이션을 디버깅하는 방법은 관리되는 Windows Forms 애플리케이션의 경우와 비슷합니다.

 프로젝트 템플릿을 사용하여 Windows Forms 프로젝트를 만들면 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서는 디버그 및 릴리스 구성에 필요한 설정을 자동으로 만듭니다. 필요한 경우 **\<프로젝트 이름> 속성 페이지** 대화 상자에서 이러한 설정을 변경할 수 있습니다. 자세한 내용은 [디버그 및 릴리스 구성](../debugger/how-to-set-debug-and-release-configurations.md)을 참조하세요.

  자세한 내용은 [C++ 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)을 참조하세요.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 외부에서 애플리케이션을 시작한 후에 애플리케이션에 연결하는 방법으로 Windows Forms 애플리케이션을 디버깅할 수도 있습니다. 자세한 내용은 [실행 중인 프로그램 또는 여러 프로그램에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)을 참조하세요.

 [항목 내용](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>참조
- [디버거 소개](../debugger/debugger-feature-tour.md)
- [C++ 디버그 구성에 대한 프로젝트 설정](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [실행 중인 프로그램 또는 여러 프로그램에 연결](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [디버그 및 릴리스 구성](../debugger/how-to-set-debug-and-release-configurations.md)
- [방법: Windows 애플리케이션 프로젝트 만들기](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))
