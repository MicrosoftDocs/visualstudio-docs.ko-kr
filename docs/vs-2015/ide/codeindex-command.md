---
title: CodeIndex 명령 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 070106dc4db0f5200c1346bbbf8c0b653aa104e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619672"
---
# <a name="codeindex-command"></a>CodeIndex 명령
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**CodeIndex** 명령을 사용하여 Team Foundation Server의 코드 인덱싱을 관리합니다. 예를 들어 인덱싱을 다시 설정하여 CodeLens 정보를 수정하거나 인덱싱을 해제하여 서버 성능 문제를 조사할 수 있습니다.

 **필요한 권한**

 **CodeIndex** 명령을 사용하려면 **Team Foundation Administrators** 보안 그룹의 멤버여야 합니다. [Team Foundation Server에 대한 사용 권한 참조](https://msdn.microsoft.com/library/39997de5-b7fb-4777-b779-07de0543abe6)를 참조하세요.

> [!NOTE]
> 관리자 자격 증명으로 로그온한 경우에도 이 명령을 실행하려면 관리자 권한 명령 프롬프트 창을 열어야 합니다. 또한 Team Foundation의 애플리케이션 계층에서 이 명령을 실행해야 합니다.

## <a name="syntax"></a>구문

```
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

#### <a name="parameters"></a>매개 변수

|**Argument**|**설명**|
|------------------|---------------------|
|`CollectionName`|팀 프로젝트 컬렉션의 이름을 지정합니다. 이름에 공백이 있으면 "Fabrikam 웹 사이트"와 같이 이름을 큰따옴표로 묶습니다.|
|`CollectionId`|팀 프로젝트 컬렉션의 ID 번호를 지정합니다.|
|`ServerPath`|코드 파일의 경로를 지정합니다.|

|**옵션**|**설명**|
|----------------|---------------------|
|**/indexingStatus**|코드 인덱싱 서비스의 상태 및 구성을 보여 줍니다.|
|**/setIndexing:** [ on &#124; off &#124; keepupOnly ]|-   **on**: 모든 변경 집합의 인덱싱을 시작합니다.<br />-   **off**: 모든 변경 집합의 인덱싱을 중지합니다.<br />-   **keepupOnly**: 이전에 만든 변경 집합의 인덱싱을 중지하고 새 변경 집합의 인덱싱만 시작합니다.|
|**/ignoreList:** [ add &#124; remove &#124; removeAll &#124; view ] `ServerPath`<br /><br /> 서버 경로의 시작이나 끝 또는 양쪽 끝에 와일드카드 문자(*)를 사용할 수 있습니다.|인덱싱하지 않을 코드 파일의 목록 및 해당 경로를 지정합니다.<br /><br /> -   **add**: 인덱싱하지 않을 파일을 무시된 파일 목록에 추가합니다.<br />-   **remove**: 인덱싱할 파일을 무시된 파일 목록에서 제거합니다.<br />-   **removeAll**: 무시된 파일 목록을 지우고 모든 파일의 인덱싱을 시작합니다.<br />-   **view**: 인덱싱되고 있지 않는 모든 파일이 표시됩니다.|
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|지정된 크기(KB)를 초과하는 지정된 파일 수를 표시합니다. 그런 다음 **/ignoreList** 옵션을 사용하여 인덱싱에서 해당 파일을 제외할 수 있습니다.|
|**/reindexAll**|이전에 인덱싱된 데이터를 지우고 인덱싱을 다시 시작합니다.|
|**/destroyCodeIndex [/noPrompt]**|코드 인덱스를 삭제하고 인덱싱된 모든 데이터를 제거합니다. **/noPrompt** 옵션을 사용하는 경우 확인이 필요하지 않습니다.|
|**/temporaryDataSizeLimit**:[ view &#124; <`SizeInGBs`> &#124; disable ]|변경 집합을 처리할 때 CodeLens에서 만드는 임시 데이터의 양을 제어합니다. 기본 제한은 6GB입니다.<br /><br /> -   **view**: 현재 크기 제한을 표시합니다.<br />-   `SizeInGBs`: 크기 제한을 변경합니다.<br />-   **disable**: 크기 제한을 제거합니다.<br /><br /> 이 제한은 CodeLens가 새 변경 집합을 처리하기 전에 확인됩니다. 임시 데이터가 이 제한을 초과하면 CodeLens는 새 변경 집합이 아닌 이전 변경 집합 처리를 일시 중지합니다. CodeLens는 데이터가 정리되고 이 제한 아래로 떨어진 후에 처리를 다시 시작합니다. 하루에 한 번씩 자동으로 정리됩니다. 정리가 시작되기 전까지 임시 데이터가 이 제한을 초과할 수 있습니다.|
|**/indexHistoryPeriod**:[ view &#124; all &#124; <`NumberOfMonths`> ]|변경 내용을 인덱싱할 기간을 제어합니다. 이 옵션은 CodeLens에서 표시하는 기록의 양에 영향을 줍니다. 기본 제한은 12개월입니다. 즉, CodeLens는 지난 12개월의 변경 내용만 표시합니다.<br /><br /> -   **view**: 현재 기간(월)을 표시합니다.<br />-   **all**: 모든 변경 내용을 인덱싱합니다.<br />-   `NumberOfMonths`: 변경 내용을 인덱싱하는 데 사용되는 기간(월)을 변경합니다.|
|**/collectionName:** `CollectionName`|**CodeIndex** 명령을 실행할 팀 프로젝트 컬렉션의 이름을 지정합니다. **/CollectionId**를 사용하지 않는 경우 필수적 요소입니다.|
|**/collectionId:** `CollectionId`|**CodeIndex** 명령을 실행할 팀 프로젝트 컬렉션의 식별 번호를 지정합니다. **/CollectionName**을 사용하지 않는 경우 필수적 요소입니다.|

## <a name="examples"></a>예

> [!NOTE]
> 용례에 사용된 회사, 조직, 제품, 도메인 이름, 전자 메일 주소, 로고, 사람, 장소 및 이벤트는 실제 데이터가 아닙니다.  어떠한 실제 회사, 기관, 제품, 도메인 이름, 전자 메일 주소, 로고, 사람, 장소 또는 이벤트와도 연관시킬 의도가 없으며 그렇게 유추해서도 안 됩니다.

 코드 인덱싱 상태 및 구성을 보려면

```
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"
```

 모든 변경 집합의 인덱싱을 시작하려면

```
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"
```

 이전에 만든 변경 집합의 인덱싱을 중지하고 새 변경 집합의 인덱싱만 시작하려면

```
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"
```

 10KB보다 큰 파일을 최대 50개 찾으려면:

```
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"
```

 인덱싱에서 특정 파일을 제외하고 무시된 파일 목록에 추가하려면

```
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"
```

 인덱싱되지 않는 모든 파일을 보려면:

```
TFSConfig CodeIndex /ignoreList:view
```

 이전에 인덱싱된 데이터를 지우고 인덱싱을 다시 시작하려면

```
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"
```

 모든 변경 집합 기록을 저장하려면

```
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"
```

 CodeLens 임시 데이터에 대한 크기 제한을 제거하고 임시 데이터 크기에 관계 없이 인덱싱을 계속하려면

```
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"
```

 확인 후 코드 인덱스를 삭제하려면

```
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"
```

## <a name="see-also"></a>관련 항목
 [TFS 용](https://msdn.microsoft.com/be8c997a-b97b-4e59-97f5-04db0a601a6c) TFSConfig 명령줄 도구 [를 사용 하 여 서버 구성 관리](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62)
