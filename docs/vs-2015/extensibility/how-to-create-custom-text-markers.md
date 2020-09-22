---
title: '방법: 사용자 지정 텍스트 표식 만들기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - custom text markers
ms.assetid: 6e32ed81-c604-4a32-9012-8db3bec7c846
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac681879e0f7ad0902358be23d74d57ccee406f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841378"
---
# <a name="how-to-create-custom-text-markers"></a>방법: 사용자 지정 텍스트 표식 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 지정 텍스트 표식을 만들어 코드를 강조 표시 하거나 구성 하려면 다음 단계를 수행 해야 합니다.  
  
- 다른 도구에서 액세스할 수 있도록 새 텍스트 표식을 등록 합니다.  
  
- 텍스트 표식의 기본 구현 및 구성 제공  
  
- 다른 프로세스에서 텍스트 표식을 사용 하는 데 사용할 수 있는 서비스를 만듭니다.  
  
  코드 영역에 텍스트 마커를 적용 하는 방법에 대 한 자세한 내용은 [방법: 텍스트 표식 사용](../extensibility/how-to-use-text-markers.md)을 참조 하세요.  
  
### <a name="to-register-a-custom-marker"></a>사용자 지정 마커를 등록 하려면  
  
1. 다음과 같이 레지스트리 항목을 만듭니다.  
  
    HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* \Text Editor\External 마커\\*\<MarkerGUID>*  
  
    <em>\<MarkerGUID></em>`GUID`추가할 표식을 식별 하는 데 사용 되는입니다.  
  
    *\<Version>* 는의 버전입니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (예: 8.0).  
  
    *\<PackageGUID>* 자동화 개체를 구현 하는 VSPackage의 GUID입니다.  
  
   > [!NOTE]
   > HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio의 루트 경로는 \\ *\<Version>* Visual Studio 셸이 초기화 될 때 대체 루트를 사용 하 여 재정의할 수 있습니다. 자세한 내용은 [명령줄 스위치](../extensibility/command-line-switches-visual-studio-sdk.md)를 참조 하세요.  
  
2. HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ \Text Editor\External marker에서 4 개의 값을 만듭니다. *\<Version>*\\*\<MarkerGUID>*  
  
   - (기본값)  
  
   - 서비스  
  
   - DisplayName  
  
   - 패키지  
  
   - `Default` REG_SZ 형식의 선택적 항목입니다. 설정 하는 경우 항목의 값은 일부 유용한 식별 정보를 포함 하는 문자열입니다 (예: "사용자 지정 텍스트 표식").  
  
   - `Service` proffering에 의해 사용자 지정 텍스트 표식을 제공 하는 서비스의 GUID 문자열을 포함 하는 REG_SZ 형식의 항목입니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> . 형식은 {XXXXXX XXXX xxxx XXXX XXXXXXXXX}입니다.  
  
   - `DisplayName` 사용자 지정 텍스트 표식의 이름에 대 한 리소스 ID를 포함 하는 REG_SZ 형식의 항목입니다. #YYYY 형식입니다.  
  
   - `Package` 는 `GUID` 서비스에 나열 된 서비스를 제공 하는 VSPackage의를 포함 하는 REG_SZ 형식의 항목입니다. 형식은 {XXXXXX XXXX xxxx XXXX XXXXXXXXX}입니다.  
  
### <a name="to-create-a-custom-text-marker"></a>사용자 지정 텍스트 표식을 만들려면  
  
1. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> 인터페이스를 구현합니다.  
  
     이 인터페이스의 구현은 사용자 지정 표식 형식의 동작과 모양을 정의 합니다.  
  
     이 인터페이스는 다음과 같은 경우에 호출 됩니다.  
  
    1. 사용자가 처음으로 IDE를 시작 합니다.  
  
    2. 사용자가 IDE의 **도구** 메뉴에서 가져온 **옵션** 대화 상자의 왼쪽 창에 있는 **환경** 폴더의 **글꼴 및 색** 속성 페이지에서 **기본값 다시 설정** 단추를 선택 합니다.  
  
2. 메서드를 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider.GetTextMarkerType%2A> 하 여 `IVsPackageDefinedTextMarkerType` 메서드 호출에 지정 된 마커 형식 GUID에 따라 반환 되어야 하는 구현을 지정 합니다.  
  
     환경에서는 사용자 지정 표식 형식이 처음 생성 될 때이 메서드를 호출 하 고 사용자 지정 표식 유형을 식별 하는 GUID를 지정 합니다.  
  
### <a name="to-proffer-your-marker-type-as-a-service"></a>표식 유형을 서비스로 proffer  
  
1. <xref:Microsoft.VisualStudio.OLE.Interop.IOleComponentManager.QueryService%2A>에 대해 메서드를 호출 <xref:Microsoft.VisualStudio.Shell.Interop.SProfferService> 합니다.  
  
     에 대 한 포인터가 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> 반환 됩니다.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.ProfferService%2A>사용자 지정 표식 유형 서비스를 식별 하 고 인터페이스 구현에 대 한 포인터를 제공 하는 GUID를 지정 하 여 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> . <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>구현에서 인터페이스의 구현에 대 한 포인터를 반환 해야 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider> .  
  
     서비스가 반환 됨을 식별 하는 고유한 쿠키입니다. 나중에이 쿠키를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> 이 쿠키 값을 지정 하는 인터페이스의 메서드를 호출 하 여 사용자 지정 표식 형식 서비스를 해지할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> .  
  
## <a name="see-also"></a>참고 항목  
 [레거시 API에서 텍스트 표식 사용](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [방법: 표준 텍스트 표식 추가](../extensibility/how-to-add-standard-text-markers.md)   
 [방법: 오류 마커 구현](../extensibility/how-to-implement-error-markers.md)   
 [방법: 텍스트 표식 사용](../extensibility/how-to-use-text-markers.md)
