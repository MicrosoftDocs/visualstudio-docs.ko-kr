---
title: 프라이빗 갤러리 | 마이크로 소프트 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 895fbef5459de75c7ccdc6a090fc30ec27a030f9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444923"
---
# <a name="private-galleries"></a>Private Galleries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음과 같이 조직의 인트라넷에 있는 *개인 갤러리에* 게시하여 개발한 컨트롤, 템플릿 및 도구를 공유할 수 있습니다.  
  
- 인트라넷에서 적절하게 구성된 중앙 위치(리포지토리)에 RSS(Atom) 피드를 만듭니다. 자세한 내용은 [개인 갤러리에 대한 원자 피드 만들기 방법을](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)참조하십시오.  
  
- 개인 갤러리를 설명하는 .pkgdef 파일을 배포합니다. 개인 갤러리를 여러 컴퓨터에 동시에 연결하려는 관리자에게는 이 구성을 권장합니다.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>비주얼 스튜디오의 확장 및 업데이트에 개인 갤러리 추가  
 개인 갤러리를 사용할 수 있는 경우 Visual Studio의 **확장 및 업데이트에** 추가할 수 있습니다.  
  
 ![확장 관리자 추가 대화 상자](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>확장 및 업데이트에 비공개 갤러리를 추가하려면  
  
1. 메뉴 모음에서 **도구**, **옵션**을 선택합니다.  
  
2. **환경** 노드에서 확장 및 업데이트 를 **선택합니다.**  
  
3. **추가** 단추를 선택합니다.  
  
4. **이름** 필드에 개인 갤러리의 이름을 입력합니다. `My Gallery`  
  
5. **URL** 필드에 개인 갤러리를 호스팅하는 Atom 피드 또는 SharePoint 사이트의 URL을 입력합니다.  
  
    1. 호스트가 개인 갤러리에 연결되는 Atom 피드인 경우 URL은 다음과 `http://www.mywebsite/mygallery/atom.xml`유사합니다.  이 URL은 파일 또는 네트워크 경로를 참조할 수 있습니다.  
  
    2. 호스트가 SharePoint 사이트인 경우 URL은 다음과 `http://mysharepoint/sites/mygallery/forms/AllItems.aspx`유사합니다.  
  
### <a name="managing-private-galleries"></a>개인 갤러리 관리  
 관리자는 각 컴퓨터의 시스템 레지스트리를 수정하여 여러 컴퓨터에서 동시에 개인 갤러리를 사용할 수 있도록 할 수 있습니다. 이렇게 하려면 새 레지스트리 키와 해당 값을 설명하는 .pkgdef 파일을 만듭니다.  이 파일의 형식은 다음과 같습니다.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 자세한 내용은 [레지스트리 설정을 사용하여 개인 갤러리 를 관리하는 방법을](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)참조하십시오.  
  
## <a name="installing-extensions-from-a-private-gallery"></a>개인 갤러리에서 확장 프로그램 설치  
 확장 및 업데이트의 개인 갤러리에서 Visual Studio 확장을 검색하고 설치할 수 **있습니다.** 다음 단계에서는 개인 갤러리를 `My Gallery`사용합니다.  
  
 ![전용 갤러리를 설치하는 확장 관리자](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>개인 갤러리에서 확장을 검색하고 설치하려면  
  
1. 메뉴 모음에서 **도구**, **확장 및 업데이트**를 선택합니다.  
  
2. 왼쪽 창에서 온라인 **확장을**선택한 다음 **내 갤러리를**선택합니다.  
  
3. 오른쪽 창에서 확장을 선택한 다음 **다운로드** 단추를 선택합니다.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>개인 갤러리에서 확장 프로그램 업데이트  
 새 버전의 Visual Studio 확장이 개인 갤러리에 게시되면 설치한 확장을 업데이트할 수 있습니다. 다음 단계에서는 개인 갤러리를 `My Repository`사용합니다.  
  
 ![확장명 관리자 전용 갤러리 업데이트](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>개인 갤러리에서 설치된 확장을 업데이트하려면  
  
1. 메뉴 모음에서 **도구**, **확장 및 업데이트**를 선택합니다.  
  
2. 왼쪽 창에서 **업데이트를**선택한 다음 **내 리포지토리**를 선택합니다.  
  
3. 오른쪽 창에서 확장을 선택한 다음 **업데이트** 단추를 선택합니다.  
  
## <a name="see-also"></a>참고 항목  
 [비주얼 스튜디오 확장 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)   
 [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)
