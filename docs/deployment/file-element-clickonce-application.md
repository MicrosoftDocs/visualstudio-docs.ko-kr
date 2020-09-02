---
title: '&lt;file &gt; 요소 (ClickOnce 응용 프로그램) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9345f3f094e1c48204892cd40cca71a7e28eba7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900280"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;file &gt; 요소 (ClickOnce 응용 프로그램)
응용 프로그램에서 다운로드 하 여 사용 하는 모든 nonassembly 파일을 식별 합니다.

## <a name="syntax"></a>Syntax

```xml
<file
    name
    size
    group
    optional
    writeableType
>
    <typelib
        tlbid
        version
        helpdir
        resourceid
        flags
    />
    <comClass
        clsid
        description
        threadingModel
        tlbid
        progid
        miscStatus
        miscStatusIcon
        miscStatusContent
        miscStatusDocPrint
        miscStatusThumbnail
    />
    <comInterfaceExternalProxyStub
        iid
        baseInterface
        numMethods
        name
        tlbid
        proxyStubClass32
    />
    <comInterfaceProxyStub
        iid
        baseInterface
        numMethods
        name
        tlbid
        proxyStubClass32
    />
    <windowClass
        versioned
    />
</file>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `file` 요소는 선택적입니다. 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`name`|필수 요소. 파일의 이름을 식별 합니다.|
|`size`|필수 요소. 파일의 크기 (바이트)를 지정 합니다.|
|`group`|`optional`특성이 지정 되지 않거나로 설정 되어 있으면 `false` 이 고,가 이면 필수 `optional` `true` 입니다. 이 파일이 속한 그룹의 이름입니다. 이름은 개발자가 선택한 모든 유니코드 문자열 값일 수 있으며 클래스를 사용 하 여 요청 시 파일을 다운로드 하는 데 사용 됩니다 <xref:System.Deployment.Application.ApplicationDeployment> .|
|`optional`|선택 사항입니다. 응용 프로그램을 처음 실행할 때이 파일을 다운로드 해야 하는지 여부 또는 응용 프로그램이 요청 시 요청을 요청할 때까지 파일이 서버에만 있어야 하는지 여부를 지정 합니다. `false`또는 undefined 이면 응용 프로그램을 처음 실행 하거나 설치할 때 파일이 다운로드 됩니다. 이면 `true` `group` 응용 프로그램 매니페스트가 유효 하도록를 지정 해야 합니다. `optional``writeableType`값을 사용 하 여를 지정 하면 true가 될 수 없습니다 `applicationData` .|
|`writeableType`|선택 사항입니다. 이 파일이 데이터 파일 임을 지정 합니다. 현재 유효한 값은 `applicationData`뿐입니다.|

## <a name="typelib"></a>typelib
 `typelib`요소는 file 요소의 선택적 자식 요소입니다. 요소는 COM 구성 요소에 속하는 형식 라이브러리를 설명 합니다. 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`tlbid`|필수 요소. 형식 라이브러리에 할당 된 GUID입니다.|
|`version`|필수 요소. 형식 라이브러리의 버전 번호입니다.|
|`helpdir`|필수 요소. 구성 요소에 대 한 도움말 파일이 들어 있는 디렉터리입니다. 길이가 0 일 수 있습니다.|
|`resourceid`|선택 사항입니다. 로캘 식별자 (LCID)의 16 진수 문자열 표현입니다. 0x 접두사가 없고 앞에 오는 0이 없는 1 ~ 4 자리의 16 진수입니다. LCID에는 중립 하위 언어 식별자가 있을 수 있습니다.|
|`flags`|선택 사항입니다. 이 형식 라이브러리에 대 한 형식 라이브러리 플래그의 문자열 표현입니다. 특히 "제한 됨", "CONTROL", "HIDDEN" 및 "HASDISKIMAGE" 중 하나 여야 합니다.|

## <a name="comclass"></a>comClass
 `comClass`요소는 요소의 선택적 자식 요소 `file` 이지만 응용 프로그램에 등록이 필요 없는 com을 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 사용 하 여 배포 하려는 com 구성 요소가 포함 된 경우에 필요 합니다. 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`clsid`|필수 요소. GUID로 표현 된 COM 구성 요소의 클래스 ID입니다.|
|`description`|선택 사항입니다. 클래스 이름입니다.|
|`threadingModel`|선택 사항입니다. In-process COM 클래스에서 사용 하는 스레딩 모델입니다. 이 속성이 null 이면 스레딩 모델이 사용 되지 않습니다. 구성 요소가 클라이언트의 주 스레드에 만들어지고 다른 스레드의 호출이이 스레드로 마샬링됩니다. 다음 목록에서는 유효한 값을 보여 줍니다.<br /><br /> `Apartment`, `Free`, `Both` 및 `Neutral`.|
|`tlbid`|선택 사항입니다. 이 COM 구성 요소의 형식 라이브러리에 대 한 GUID입니다.|
|`progid`|선택 사항입니다. COM 구성 요소와 연결 된 버전 종속 프로그래밍 id입니다. 의 형식은 `ProgID` `<vendor>.<component>.<version>` 입니다.|
|`miscStatus`|선택 사항입니다. 어셈블리 매니페스트의 중복은 레지스트리 키에서 제공 하는 정보를 제공 합니다 `MiscStatus` . ,, 또는 특성에 대 한 값을 찾을 수 없는 경우 `miscStatusIcon` `miscStatusContent` `miscStatusDocprint` `miscStatusThumbnail` 에 나열 된 해당 기본값이 `miscStatus` 누락 된 특성에 사용 됩니다. 값은 다음 표에 있는 특성 값의 쉼표로 구분 된 목록 일 수 있습니다. COM 클래스가 레지스트리 키 값을 필요로 하는 OCX 클래스인 경우이 특성을 사용할 수 있습니다 `MiscStatus` .|
|`miscStatusIcon`|선택 사항입니다. 어셈블리 매니페스트의 중복은 DVASPECT_ICON에서 제공 하는 정보를 제공 합니다. 개체의 아이콘을 제공할 수 있습니다. 값은 다음 표에 있는 특성 값의 쉼표로 구분 된 목록 일 수 있습니다. COM 클래스가 레지스트리 키 값을 필요로 하는 OCX 클래스인 경우이 특성을 사용할 수 있습니다 `Miscstatus` .|
|`miscStatusContent`|선택 사항입니다. 어셈블리 매니페스트의 중복은 DVASPECT_CONTENT에서 제공 하는 정보를 제공 합니다. 화면 또는 프린터에 대해 표시할 수 있는 복합 문서를 제공할 수 있습니다. 값은 다음 표에 있는 특성 값의 쉼표로 구분 된 목록 일 수 있습니다. COM 클래스가 레지스트리 키 값을 필요로 하는 OCX 클래스인 경우이 특성을 사용할 수 있습니다 `MiscStatus` .|
|`miscStatusDocPrint`|선택 사항입니다. 어셈블리 매니페스트의 중복은 DVASPECT_DOCPRINT에서 제공 하는 정보를 제공 합니다. 프린터에 인쇄 된 것 처럼 화면에 표시 가능한 개체 표현을 제공할 수 있습니다. 값은 다음 표에 있는 특성 값의 쉼표로 구분 된 목록 일 수 있습니다. COM 클래스가 레지스트리 키 값을 필요로 하는 OCX 클래스인 경우이 특성을 사용할 수 있습니다 `MiscStatus` .|
|`miscStatusThumbnail`|선택 사항입니다. 어셈블리 매니페스트의 중복은 DVASPECT_THUMBNAIL에서 제공 하는 정보를 제공 합니다. 검색 도구에서 표시할 수 있는 개체의 미리 보기를 제공할 수 있습니다. 값은 다음 표에 있는 특성 값의 쉼표로 구분 된 목록 일 수 있습니다. COM 클래스가 레지스트리 키 값을 필요로 하는 OCX 클래스인 경우이 특성을 사용할 수 있습니다 `MiscStatus` .|

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub
 `comInterfaceExternalProxyStub`요소는 요소의 선택적 자식 `file` 이지만, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 등록이 필요 없는 com을 사용 하 여 배포 하려는 com 구성 요소가 응용 프로그램에 포함 된 경우 필요할 수 있습니다. 요소는 다음 특성을 포함 합니다.

|특성|설명|
|---------------|-----------------|
|`iid`|필수 요소. 이 프록시에서 제공 하는 IID (인터페이스 ID)입니다. IID에는 중괄호가 있어야 합니다.|
|`baseInterface`|선택 사항입니다. 에서 참조 하는 인터페이스가 파생 되는 인터페이스의 IID입니다 `iid` .|
|`numMethods`|선택 사항입니다. 인터페이스에 의해 구현 된 메서드의 수입니다.|
|`name`|선택 사항입니다. 코드에 표시 되는 인터페이스의 이름입니다.|
|`tlbid`|선택 사항입니다. 특성으로 지정 된 인터페이스에 대 한 설명을 포함 하는 형식 라이브러리입니다 `iid` .|
|`proxyStubClass32`|선택 사항입니다. IID를 32 비트 프록시 Dll의 CLSID에 매핑합니다.|

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub
 `comInterfaceProxyStub`요소는 요소의 선택적 자식 `file` 이지만, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 등록이 필요 없는 com을 사용 하 여 배포 하려는 com 구성 요소가 응용 프로그램에 포함 된 경우 필요할 수 있습니다. 요소는 다음 특성을 포함 합니다.

|특성|설명|
|---------------|-----------------|
|`iid`|필수 요소. 이 프록시에서 제공 하는 IID (인터페이스 ID)입니다. IID에는 중괄호가 있어야 합니다.|
|`baseInterface`|선택 사항입니다. 에서 참조 하는 인터페이스가 파생 되는 인터페이스의 IID입니다 `iid` .|
|`numMethods`|선택 사항입니다. 인터페이스에 의해 구현 된 메서드의 수입니다.|
|`Name`|선택 사항입니다. 코드에 표시 되는 인터페이스의 이름입니다.|
|`Tlbid`|선택 사항입니다. 특성으로 지정 된 인터페이스에 대 한 설명을 포함 하는 형식 라이브러리입니다 `iid` .|
|`proxyStubClass32`|선택 사항입니다. IID를 32 비트 프록시 Dll의 CLSID에 매핑합니다.|
|`threadingModel`|선택 사항입니다. 선택 사항입니다. In-process COM 클래스에서 사용 하는 스레딩 모델입니다. 이 속성이 null 이면 스레딩 모델이 사용 되지 않습니다. 구성 요소가 클라이언트의 주 스레드에 만들어지고 다른 스레드의 호출이이 스레드로 마샬링됩니다. 다음 목록에서는 유효한 값을 보여 줍니다.<br /><br /> `Apartment`, `Free`, `Both` 및 `Neutral`.|

## <a name="windowclass"></a>windowClass
 `windowClass`요소는 요소의 선택적 자식 `file` 이지만, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 등록이 필요 없는 com을 사용 하 여 배포 하려는 com 구성 요소가 응용 프로그램에 포함 된 경우 필요할 수 있습니다. 요소는 버전을 적용 해야 하는 COM 구성 요소에 의해 정의 된 창 클래스를 참조 합니다. 요소는 다음 특성을 포함 합니다.

|특성|설명|
|---------------|-----------------|
|`versioned`|선택 사항입니다. 등록에 사용 되는 내부 창 클래스 이름이 창 클래스를 포함 하는 어셈블리의 버전을 포함 하는지 여부를 제어 합니다. 이 특성의 값이 될 수 있습니다 `yes` 또는 `no`합니다. 기본값은 `yes`입니다. 이 값은 `no` 동일한 창 클래스가 side-by-side 구성 요소 및 이와 동등한 side-by-side 구성 요소에 의해 정의 되 고 동일한 창 클래스로 처리 하려는 경우에만 사용 해야 합니다. 창 클래스 등록에 대한 일반적인 규칙이 적용됩니다. 창 클래스에 적용되는 버전이 없기 때문에 창 클래스를 등록하는 첫 번째 구성 요소만 해당 클래스를 등록할 수 있습니다.|

## <a name="hash"></a>hash
 요소는 `hash` 요소의 선택적 자식 요소입니다 `file` . `hash` 요소에는 특성이 없습니다.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램의 모든 파일에 대 한 알고리즘 해시를 보안 검사로 사용 하 여 배포 후 파일이 변경 되지 않도록 합니다. `hash`요소가 포함 되지 않은 경우에는이 검사가 수행 되지 않습니다. 따라서 요소를 생략 하는 `hash` 것은 권장 되지 않습니다.

 매니페스트에 해시 되지 않은 파일이 포함 되어 있는 경우 사용자는 해시 되지 않은 파일의 콘텐츠를 확인할 수 없으므로 해당 매니페스트를 디지털 서명할 수 없습니다.

## <a name="dsigtransforms"></a>dsig:Transforms
 요소는 `dsig:Transforms` 요소의 필수 자식 요소입니다 `hash` . `dsig:Transforms` 요소에는 특성이 없습니다.

## <a name="dsigtransform"></a>dsig:Transform
 요소는 `dsig:Transform` 요소의 필수 자식 요소입니다 `dsig:Transforms` . `dsig:Transform` 요소에는 다음 특성이 있습니다.

| 특성 | 설명 |
|-------------| - |
| `Algorithm` | 이 파일의 다이제스트를 계산 하는 데 사용 되는 알고리즘입니다. 현재에서 사용 되는 유일한 값은 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `urn:schemas-microsoft-com:HashTransforms.Identity` 입니다. |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 요소는 `dsig:DigestMethod` 요소의 필수 자식 요소입니다 `hash` . `dsig:DigestMethod` 요소에는 다음 특성이 있습니다.

| 특성 | 설명 |
|-------------| - |
| `Algorithm` | 이 파일의 다이제스트를 계산 하는 데 사용 되는 알고리즘입니다. 현재에서 사용 되는 유일한 값은 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `http://www.w3.org/2000/09/xmldsig#sha1` 입니다. |

## <a name="dsigdigestvalue"></a>dsig:DigestValue
 요소는 `dsig:DigestValue` 요소의 필수 자식 요소입니다 `hash` . `dsig:DigestValue` 요소에는 특성이 없습니다. 해당 텍스트 값은 지정 된 파일에 대해 계산 된 해시입니다.

## <a name="remarks"></a>설명
 이 요소는 응용 프로그램을 구성 하는 모든 nonassembly 파일 및 특히 파일 확인을 위한 해시 값을 식별 합니다. 이 요소는 파일에 연결 된 COM (구성 요소 개체 모델) 격리 데이터를 포함할 수도 있습니다. 파일이 변경 된 경우에도 변경 내용을 반영 하도록 응용 프로그램 매니페스트 파일을 업데이트 해야 합니다.

## <a name="example"></a>예
 다음 코드 예제에서는를 `file` 사용 하 여 배포 된 응용 프로그램에 대 한 응용 프로그램 매니페스트의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

```xml
<file name="Icon.ico" size="9216">
  <hash>
    <dsig:Transforms>
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
    </dsig:Transforms>
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>
  </hash>
</file>
```

## <a name="see-also"></a>추가 정보
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)