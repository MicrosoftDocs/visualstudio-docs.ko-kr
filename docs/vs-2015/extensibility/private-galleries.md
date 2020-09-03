---
title: 전용 갤러리 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444923"
---
# <a name="private-galleries"></a>Private Galleries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음과 같이 조직의 인트라넷에 있는 *개인 갤러리* 에 게시 하 여 개발 하는 컨트롤, 템플릿 및 도구를 공유할 수 있습니다.  
  
- 인트라넷에서 적절 하 게 구성 된 중앙 위치 (리포지토리)에 Atom (RSS) 피드를 만듭니다. 자세한 내용은 [방법: 전용 갤러리에 대 한 Atom 피드 만들기](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)를 참조 하세요.  
  
- 전용 갤러리를 설명 하는 .pkgdef 파일을 배포 합니다. 개인 갤러리를 여러 컴퓨터에 동시에 연결 하려는 관리자에 게이 구성을 권장 합니다.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Visual Studio에서 확장 및 업데이트에 전용 갤러리 추가  
 전용 갤러리를 사용할 수 있는 경우 Visual Studio의 **확장 및 업데이트** 에 추가할 수 있습니다.  
  
 ![확장 관리자 추가 대화 상자](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>확장 및 업데이트에 전용 갤러리를 추가 하려면  
  
1. 메뉴 모음에서 **도구**, **옵션**을 선택 합니다.  
  
2. **환경** 노드에서 **확장 및 업데이트**를 선택 합니다.  
  
3. **추가** 단추를 선택합니다.  
  
4. **이름** 필드에 개인 갤러리의 이름 (예:)을 입력 `My Gallery` 합니다.  
  
5. **Url** 필드에 비공개 갤러리를 호스트 하는 Atom 피드 또는 SharePoint 사이트의 url을 입력 합니다.  
  
    1. 호스트가 개인 갤러리에 연결 하는 Atom 피드 이면 URL은와 유사 `http://www.mywebsite/mygallery/atom.xml` 합니다.  이 URL은 파일이 나 네트워크 경로를 참조할 수 있습니다.  
  
    2. 호스트가 SharePoint 사이트인 경우 URL은와 유사 `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` 합니다.  
  
### <a name="managing-private-galleries"></a>개인 갤러리 관리  
 관리자는 각 컴퓨터에서 시스템 레지스트리를 수정 하 여 동시에 여러 컴퓨터에서 사용할 수 있는 개인 갤러리를 만들 수 있습니다. 이를 수행 하려면 새 레지스트리 키와 해당 값을 설명 하는 .pkgdef 파일을 만듭니다.  이 파일의 형식은 다음과 같습니다.  
  
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
  
 자세한 내용은 [방법: 레지스트리 설정을 사용 하 여 전용 갤러리 관리](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md)를 참조 하세요.  
  
## <a name="installing-extensions-from-a-private-gallery"></a>전용 갤러리에서 확장 설치  
 **확장 및 업데이트**의 전용 갤러리에서 Visual Studio 확장을 검색 하 고 설치할 수 있습니다. 다음 단계에서는 라는 개인 갤러리를 사용 합니다 `My Gallery` .  
  
 ![전용 갤러리를 설치하는 확장 관리자](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>전용 갤러리에서 확장을 검색 하 고 설치 하려면  
  
1. 메뉴 모음에서 **도구**, **확장 및 업데이트**를 선택합니다.  
  
2. 왼쪽 창에서 **온라인 확장**을 선택한 다음 **내 갤러리**를 선택 합니다.  
  
3. 오른쪽 창에서 확장을 선택 하 고 **다운로드** 단추를 선택 합니다.  
  
## <a name="updating-extensions-from-a-private-gallery"></a>전용 갤러리에서 확장 업데이트  
 새 버전의 Visual Studio 확장이 전용 갤러리에 게시 되 면 설치한 확장을 업데이트할 수 있습니다. 다음 단계에서는 라는 개인 갤러리를 사용 합니다 `My Repository` .  
  
 ![확장명 관리자 전용 갤러리 업데이트](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>전용 갤러리에서 설치 된 확장을 업데이트 하려면  
  
1. 메뉴 모음에서 **도구**, **확장 및 업데이트**를 선택합니다.  
  
2. 왼쪽 창에서 **업데이트**를 선택 하 고 **내 리포지토리**를 선택 합니다.  
  
3. 오른쪽 창에서 확장을 선택 하 고 **업데이트** 단추를 선택 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 확장 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)   
 [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)
