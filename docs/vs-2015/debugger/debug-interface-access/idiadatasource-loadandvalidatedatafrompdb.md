---
title: 'IDiaDataSource:: loadAndValidateDataFromPdb | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f19a910af45ed70ae74c72441890ecae6c81d2a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198625"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로그램 데이터베이스 (.pdb) 파일이 제공 된 서명 정보와 일치 하는지 확인 하 고 .pdb 파일을 디버그 데이터 소스로 준비 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pdbPath`  
 진행 .Pdb 파일의 경로입니다.  
  
 `pcsig70`  
 진행 .Pdb 파일 서명에 대해 확인할 GUID 서명입니다. 이상 버전의 .pdb 파일에만 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] GUID 서명이 있습니다.  
  
 `sig`  
 진행 .Pdb 파일 서명에 대해 확인할 32 비트 시그니처입니다.  
  
 `age`  
 진행 확인할 Age 값입니다. 사용 기간이 알려진 시간 값에 해당 하는 것은 아닙니다. .pdb 파일이 해당 .exe 파일과 동기화 되지 않은 상태 인지 확인 하는 데 사용 됩니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 다음 표에서는이 메서드에 사용할 수 있는 반환 값을 보여 줍니다.  
  
|값|설명|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|파일을 열지 못했거나 파일의 형식이 잘못 되었습니다.|  
|E_PDB_FORMAT|사용 되지 않는 형식으로 파일에 액세스 하려고 했습니다.|  
|E_PDB_INVALID_SIG|서명이 일치 하지 않습니다.|  
|E_PDB_INVALID_AGE|Age가 일치 하지 않습니다.|  
|E_INVALIDARG|잘못된 매개 변수입니다.|  
|E_UNEXPECTED|데이터 원본이 이미 준비 되었습니다.|  
  
## <a name="remarks"></a>설명  
 .Pdb 파일에는 시그니처와 age 값이 모두 포함 되어 있습니다. 이러한 값은 .pdb 파일에 일치 하는 .exe 또는 .dll 파일에 복제 됩니다. 이 메서드는 데이터 소스를 준비 하기 전에 명명 된 .pdb 파일의 시그니처와 나이가 제공 된 값과 일치 하는지 확인 합니다.  
  
 유효성 검사 없이 .pdb 파일을 로드 하려면 [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) 메서드를 사용 합니다.  
  
 콜백 메커니즘을 통해 데이터 로드 프로세스에 대 한 액세스 권한을 얻으려면 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드를 사용 합니다.  
  
 메모리에서 직접 .pdb 파일을 로드 하려면 [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) 메서드를 사용 합니다.  
  
## <a name="example"></a>예제  
  
```cpp#  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
