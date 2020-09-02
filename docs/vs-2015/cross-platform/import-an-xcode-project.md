---
title: XCode 프로젝트 가져오기 | Microsoft 문서
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 4faa2ecae7f53d29e6aad92723ca6d12e50e2812
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150944"
---
# <a name="import-an-xcode-project"></a>XCode 프로젝트 가져오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

플랫폼 간 모바일 개발용 Microsoft Visual C++에서는 Visual Studio로 XCode 프로젝트 이동을 지원하여 플랫폼 간 라이브러리를 만들고 다른 프로젝트와 코드를 공유할 수 있습니다. XCode에서 가져오기 마법사를 사용하면 정적 라이브러리 또는 공유 코드 프로젝트로 사용하기 위해 프로젝트를 가져오고 XCode 대상에서 C++ 코드를 분할하는 프로세스가 간단해집니다. Visual Studio에서 iOS 관련 코드를 관리할 수 있으며 XCode를 계속 사용하여 스토리보드 및 빌드를 수행할 수 있습니다. Visual Studio와 XCode 간에 코드를 쉽게 이동하는 방법에 대한 자세한 내용은 XCode와 Visual Studio 간에 변경 내용 이동을 참조하세요.  
  
## <a name="using-the-import-from-xcode-wizard"></a>XCode에서 가져오기 마법사 사용  
 이 항목에서는 XCode 프로젝트를 Visual Studio로 이동하여 코드 공유 및 플랫폼 간 솔루션을 활용하는 방법을 보여 줍니다. 프로젝트를 가져오고, 내보내고, 빌드할 수 있으려면 필수 조건으로 Mac을 Visual Studio에 연결해야 합니다. 페어링을 설정 하는 방법에 대 한 지침은 [iOS를 사용 하 여 빌드할 도구 설치 및 구성](../cross-platform/install-and-configure-tools-to-build-using-ios.md)을 참조 하세요. 또한 네트워크를 통해 XCode 프로젝트를 공유하거나 Visual Studio 컴퓨터로 Xcode 프로젝트를 옮겨 XCode에서 가져오기 마법사를 사용해야 합니다.  
  
#### <a name="import-from-xcode"></a>XCode에서 가져오기  
  
1. **파일** 메뉴에서 **새로 만들기**, **가져오기**, **XCode에서 가져오기**를 선택합니다. 그러면 **XCode에서 가져오기** 마법사 대화 상자가 시작됩니다.  
  
    ![가져올 XCode 대상 프로젝트를 선택 하세요.](../cross-platform/media/cppmdd-u2-importxcode-choose.PNG "CPPMDD_U2_ImportXCode_Choose")  
  
2. **프로젝트 선택** 창에서 찾아보기 단추를 선택하여 Xcode .pbxproj 파일을 선택합니다. **XCode 프로젝트 파일 선택** 대화 상자에서 프로젝트 파일로 이동한 다음 **열기**를 선택합니다.  
  
    ![Xcode 프로젝트 파일 선택 대화 상자에서 프로젝트 파일 선택](../cross-platform/media/cppmdd-u2-importxcode-browse.PNG "CPPMDD_U2_ImportXCode_Browse")  
  
    XCode에서 가져오기 마법사에서 **다음**을 선택합니다.  
  
3. **대상** 창에서 Visual Studio 프로젝트로 가져올 XCode 프로젝트의 대상을 선택합니다. XCode 대상은 Visual Studio 프로젝트와 유사합니다. 대부분은 이진을 생성하는 리소스 및 코드의 컬렉션입니다. XCode에서 가져오기 마법사에서는 정적 라이브러리가 아닌 이진을 대상으로 생성하는 대상의 가져오기만 허용합니다. XCode 정적 라이브러리 대상은 다음 단계의 주제입니다.  
  
    ![XCode에서 가져오기 마법사 대상 대상 창](../cross-platform/media/cppmdd-u2-importxcode-destination.jpg "CPPMDD_U2_ImportXCode_Destination")  
  
    **가져올 대상**에서 선택한 각 대상에 대해 마법사는 별도의 정적 라이브러리 프로젝트로 분할할 수 있는 C++ 코드 파일을 자동으로 검색하여 **C++ 프로젝트 항목** 섹션에 넣습니다. 다른 코드 및 리소스는 **XCode 프로젝트 항목** 섹션에 그대로 유지됩니다. 마법사에서 가져오기 프로세스를 완료하면 이러한 항목은 Visual Studio에서 별도의 정적 라이브러리 및 애플리케이션 프로젝트가 됩니다. 기본적으로 단위 테스트 및 프레임워크 대상은 마법사에서 별도의 프로젝트로 분할되지 않습니다.  
  
    각 프로젝트에 있는 파일을 변경하려면 위로 및 아래로 단추를 사용합니다. 각 프로젝트의 파일에 만족하는 경우 **다음**을 선택하여 계속합니다.  
  
4. **라이브러리 대상** 창에서 Visual Studio 프로젝트로 가져올 XCode 프로젝트의 정적 라이브러리 대상을 선택합니다. 이 창에서 공유 코드 프로젝트에 배치되는 파일과 정적 라이브러리 프로젝트에 배치되는 파일을 선택할 수 있습니다. **가져올 대상** 목록의 각 대상에서 위로 및 아래로 단추를 사용하여 **공유 코드 프로젝트 항목** 및 **정적 라이브러리 프로젝트 항목**에 배치되는 파일을 제어할 수 있습니다.  
  
    ![XCode 라이브러리 대상 창에서 가져오기](../cross-platform/media/cppmdd-u2-importxcode-library.jpg "CPPMDD_U2_ImportXCode_Library")  
  
    공유 코드 프로젝트는 Visual Studio에서 프로젝트 간에 소스 코드 파일 집합을 공유하는 방법입니다. 코드는 자체 프로젝트가 아니라 코드를 포함하는 프로젝트의 일부로 빌드됩니다. 공유 코드를 포함하는 프로젝트마다 아키텍처 및 구성이 다를 수 있으므로 이 방법은 많은 종류의 플랫폼에 대해 빌드될 수 있는 코드가 포함된 단일 프로젝트를 제공하는 데 가장 좋습니다.  
  
    각 프로젝트의 파일에 만족하는 경우 **다음**을 선택하여 계속합니다.  
  
5. **전역 속성** 창을 사용하면 Visual Studio에서 모든 iOS 프로젝트에 대해 프레임워크 검색 경로 및 헤더 검색 경로 포함을 설정할 수 있습니다. Visual Studio는 소스 코드 검색 및 IntelliSense에 이러한 경로를 사용합니다. 이러한 전역 경로는 헤더 및 프레임워크 공통 집합을 사용하는 iOS 프로젝트를 만들 때 유용합니다.  
  
    ![XCode에서 가져오기 전역 속성 창](../cross-platform/media/cppmdd-u2-importxcode-global.jpg "CPPMDD_U2_ImportXCode_Global")  
  
    이러한 전역 경로는 Visual studio의 **옵션** 대화 상자에서도 설정할 수 있습니다. 이 대화 상자를 찾으려면 **도구** 메뉴에서 **옵션**을 선택합니다. **옵션** 대화 상자에서 **플랫폼 간**, **C++**, **iOS**, **전역 속성**을 확장합니다.  
  
    **다음** 을 선택하여 계속 진행합니다.  
  
6. **프레임워크** 창은 Visual Studio에서 프로젝트에 대한 검색 및 IntelliSense를 위해 사용하는 경로를 구성하는 데 사용됩니다. 경로를 통해 XCode 프로젝트에서 참조하는 각 프레임워크에 대해 Visual Studio에 액세스할 수 있어야 합니다. 마법사는 XCode 프로젝트에서 프레임워크 참조를 확인하고 Visual Studio에서 프레임워크를 찾을 수 있는지 여부를 표시합니다. 전역 속성에서 이미 설정한 모든 경로는 Visual Studio에서 검색되어야 합니다. 예외는 프레임워크 목록에 나열됩니다. X 표시와 함께 나열된 각 프레임워크에 대해 Visual Studio에서 프레임워크를 찾을 수 있도록 PC에서 액세스할 수 있는 경로를 제공합니다. 찾아보기 단추 [...]를 사용하면 **폴더 선택** 대화 상자를 사용하여 경로를 찾을 수 있습니다. 프레임워크 경로는 로컬 복사본이거나 Mac에서 네트워크를 통해 액세스할 수 있는 공유일 수 있습니다.  
  
    ![XCode 프레임 워크 창에서 가져오기](../cross-platform/media/cppmdd-u2-importxcode-frameworks.jpg "CPPMDD_U2_ImportXCode_Frameworks")  
  
    **다음** 을 선택하여 계속 진행합니다.  
  
7. **프로젝트 설정** 창에서는 프레임워크를 변경하고 마법사에서 만드는 각 프로젝트에 대한 헤더 검색 경로 설정을 포함할 수 있습니다. 이 창을 사용하여 전역 설정과 다른 프로젝트 관련 경로를 설정합니다.  
  
    특정 프로젝트에 대한 경로를 설정하려면 **대상 프로젝트** 드롭다운에서 프로젝트 파일을 선택한 다음 **프레임워크 검색 경로** 및 **헤더 검색 경로 포함** 컨트롤에서 값을 설정합니다. 각 컨트롤 옆에 있는 찾아보기 단추 [...]를 사용 하 여 **폴더 선택** 대화 상자를 사용 하 여 경로를 찾을 수 있습니다.  
  
    ![XCode 프로젝트 창에서 가져오기](../cross-platform/media/cppmdd-u2-importxcode-projects.jpg "CPPMDD_U2_ImportXCode_Projects")  
  
    원격 Mac이 Visual Studio에서 이 PC와 연결되지 않은 경우 [원격 컴퓨터 구성] 링크가 표시됩니다. 페어링을 설정 하는 방법에 대 한 지침은 [iOS를 사용 하 여 빌드할 도구 설치 및 구성](../cross-platform/install-and-configure-tools-to-build-using-ios.md)을 참조 하세요.  
  
    마법사 설정을 사용하여 XCode 프로젝트를 가져오려면 **가져오기**를 선택합니다.  
  
   XCode에서 가져오기 마법사는 선택한 XCode 프로젝트 대상에 해당하는 프로젝트를 Visual Studio에 만듭니다. 다른 C++ 프로젝트와 공유할 수 있는 코드는 별도의 공유 코드 및 정적 라이브러리 프로젝트로 분할됩니다. 나머지 코드는 Visual Studio에서 원격으로 빌드할 수 있는 iOS 라이브러리 및 애플리케이션 프로젝트에 배치됩니다. Visual Studio와 XCode 간에 코드를 이동 하는 방법에 대 한 자세한 내용은 [XCode와 Visual Studio 간에 변경 내용 동기화](../cross-platform/sync-changes-between-xcode-and-visual-studio.md)를 참조 하세요.
