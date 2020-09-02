---
title: ClickOnce 관리 되지 않는 API 참조 | Microsoft Docs
ms.date: 11/04/2016
api_name:
- CleanOnlineAppCache
- GetDeploymentDataFromManifest
- LaunchApplication
api_location:
- dfshim.dll
api_type:
- COM
topic_type:
- apiref
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- LaunchApplication [ClickOnce unmanaged]
- ClickOnce, unmanaged APIs
- CleanOnlineAppCache [ClickOnce unmanaged]
- CleanOnlineAppCacheW interface [ClickOnce unmanaged]
- GetDeploymentDataFromManifest [ClickOnce unmanaged]
ms.assetid: ec002138-4054-456d-bcc1-79ac2f4a4fd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 3b536a17df4f54158aa6f157a0d9795cf359ddc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900279"
---
# <a name="clickonce-unmanaged-api-reference"></a>ClickOnce 관리되지 않는 API 참조
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dfshim.dll에서 관리 되지 않는 공용 Api.

## <a name="cleanonlineappcache"></a>CleanOnlineAppCache
 응용 프로그램 캐시에서 모든 온라인 응용 프로그램을 정리 하거나 제거 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 합니다.

### <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류를 나타내는 HRESULT를 반환 합니다. 관리 되는 예외가 발생 하면는 0x80020009 (DISP_E_EXCEPTION)를 반환 합니다.

### <a name="remarks"></a>설명
 CleanOnlineAppCache를 호출 하면 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 서비스가 아직 실행 되 고 있지 않은 경우 서비스가 시작 됩니다.

## <a name="getdeploymentdatafrommanifest"></a>GetDeploymentDataFromManifest
 매니페스트 및 활성화 URL에서 배포 정보를 검색 합니다.

### <a name="parameters"></a>매개 변수

|매개 변수|설명|형식|
|---------------|-----------------|----------|
|`pcwzActivationUrl`|`ActivationURL`에 대한 포인터입니다.|LPCWSTR|
|`pcwzPathToDeploymentManifest`|`PathToDeploymentManifest`에 대한 포인터입니다.|LPCWSTR|
|`pwzApplicationIdentity`|반환 된 전체 응용 프로그램 id를 지정 하는 NULL로 끝나는 문자열을 받기 위한 버퍼에 대 한 포인터입니다.|LPWSTR|
|`pdwIdentityBufferLength`|버퍼 길이인 WCHARs에 해당 하는 DWORD에 대 한 포인터 `pwzApplicationIdentity` 입니다. 여기에는 NULL 종결 문자에 대 한 공간이 포함 됩니다.|LPDWORD|
|`pwzProcessorArchitecture`|매니페스트에서 응용 프로그램 배포의 프로세서 아키텍처를 지정 하는 NULL로 끝나는 문자열을 받기 위한 버퍼에 대 한 포인터입니다.|LPWSTR|
|`pdwArchitectureBufferLength`|버퍼 길이인 WCHARs에 해당 하는 DWORD에 대 한 포인터 `pwzProcessorArchitecture` 입니다.|LPDWORD|
|`pwzApplicationManifestCodebase`|매니페스트에서 응용 프로그램 매니페스트의 코드 베이스를 지정 하는 NULL로 끝나는 문자열을 받기 위한 버퍼에 대 한 포인터입니다.|LPWSTR|
|`pdwCodebaseBufferLength`|버퍼 길이인 WCHARs에 해당 하는 DWORD에 대 한 포인터 `pwzApplicationManifestCodebase` 입니다.|LPDWORD|
|`pwzDeploymentProvider`|매니페스트에서 배포 공급자를 지정 하는 NULL로 끝나는 문자열 (있는 경우)을 수신 하는 버퍼에 대 한 포인터입니다. 그렇지 않으면 빈 문자열이 반환 됩니다.|LPWSTR|
|`pdwProviderBufferLength`|의 길이인 DWORD에 대 한 포인터입니다 `pwzProviderBufferLength` .|LPDWORD|

### <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류를 나타내는 HRESULT를 반환 합니다. 버퍼가 너무 작으면 HRESULTFROMWIN32 (ERROR_INSUFFICIENT_BUFFER)를 반환 합니다.

### <a name="remarks"></a>설명
 포인터는 null이 아니어야 합니다. `pcwzActivationUrl` 및은 `pcwzPathToDeploymentManifest` 비워 둘 수 없습니다.

 호출자는 활성화 URL을 정리 해야 합니다. 예를 들어 필요한 경우 이스케이프 문자를 추가 하거나 쿼리 문자열을 제거 합니다.

 입력 길이를 제한 하는 것은 호출자의 책임입니다. 예를 들어 최대 URL 길이는 2KB입니다.

## <a name="launchapplication"></a>LaunchApplication
 배포 URL을 사용 하 여 응용 프로그램을 시작 하거나 설치 합니다.

### <a name="parameters"></a>매개 변수

|매개 변수|설명|형식|
|---------------|-----------------|----------|
|`deploymentUrl`|배포 매니페스트의 URL을 포함 하는 NULL로 끝나는 문자열에 대 한 포인터입니다.|LPCWSTR|
|`data`|나중에 사용하기 위해 예약되어 있습니다. Null이어야 합니다.|LPVOID|
|`flags`|나중에 사용하기 위해 예약되어 있습니다. 0이어야 합니다.|DWORD|

### <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류를 나타내는 HRESULT를 반환 합니다. 관리 되는 예외가 발생 하면는 0x80020009 (DISP_E_EXCEPTION)를 반환 합니다.

## <a name="see-also"></a>참고 항목
- <xref:System.Deployment.Application.DeploymentServiceCom.CleanOnlineAppCache%2A>