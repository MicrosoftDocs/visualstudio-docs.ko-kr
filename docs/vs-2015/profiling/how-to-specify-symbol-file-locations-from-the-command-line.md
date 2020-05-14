---
title: '방법: 명령줄에서 기호 파일 위치 지정 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 01fbb6cfd1717562af79c067ede0cad9753ad5dd
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557896"
---
# <a name="how-to-specify-symbol-file-locations-from-the-command-line"></a>방법: 명령줄에서 기호 파일 위치 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

함수 이름, 줄 번호 등의 기호 정보를 표시하려면 VSPerfReport 명령줄 도구가 프로파일링된 구성 요소 및 Windows 시스템 파일의 기호 파일(.pdb)에 액세스할 수 있어야 합니다. 기호 파일은 구성 요소가 컴파일될 때 만들어집니다. 자세한 내용은 [VSPerfReport](../profiling/vsperfreport.md)를 참조하세요. VSPerfReport는 다음 위치에서 기호 파일을 자동으로 검색합니다.  
  
- **/SymbolPath** 옵션 또는 **_NT_SYMBOL_PATH** 환경 변수에 지정된 경로.  
  
- 구성 요소가 컴파일된 정확한 로컬 경로.  
  
- 프로파일링 데이터(.vsp 또는 .vsps) 파일이 포함된 디렉터리.  
  
  Microsoft에서는 기호 서버에서 온라인으로 많은 제품에 대한 .pdb 파일을 제공합니다. 보고에 사용하고 있는 컴퓨터가 인터넷에 연결되면 VSPerfReport는 온라인 기호 서버에 연결되고 자동으로 기호 정보를 조회하여 파일을 로컬 저장소에 저장합니다.  
  
  다음 방법으로 Microsoft 기호 서버 저장소 및 기호 파일의 위치를 지정할 수 있습니다.  
  
- **_NT_SYMBOL_PATH** 환경 변수를 설정합니다.  
  
- VSPerfReport 명령줄에 **/SymbolPath** 옵션을 추가합니다.  
  
  이러한 방법을 둘 다 사용할 수도 있습니다.  
  
> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]가 로컬 컴퓨터에 설치될 경우 Windows 기호 파일의 위치가 이미 지정되었을 수 있습니다. 자세한 내용은 [방법: Windows 기호 정보 참조](../profiling/how-to-reference-windows-symbol-information.md)를 참조하세요. 이 항목의 뒷 부분에 설명된 대로 위치 및 서버를 사용하도록 VSPerfReport를 구성해야 합니다.  
  
## <a name="specifying-windows-symbol-files"></a>Windows 기호 파일 지정  
  
#### <a name="to-configure-the-use-of-the-windows-symbol-server"></a>Windows 기호 서버의 사용을 구성하려면  
  
1. 필요한 경우 로컬에 기호 파일을 저장할 디렉터리를 만듭니다.  
  
2. 다음 구문을 사용하여 **_NT_SYMBOL_PATH** 환경 변수 또는 VSPerfReport /SymbolPath 옵션을 설정합니다.  
  
   `srv*<LocalStore>*https://msdl.microsoft.com/downloads/symbols`  
  
   여기서 *<LocalStore>* 는 사용자가 만든 로컬 디렉터리의 경로입니다.  
  
## <a name="specifying-component-symbol-files"></a>구성 요소 기호 파일 지정  
 프로파일링 도구는 프로파일링 데이터 파일이 포함된 폴더 또는 구성 요소에 저장된 원래 위치에서 프로파일링하려는 구성 요소의 .pdb 파일을 검색합니다. **_NT_SYMBOL_PATH** 또는 **/SymbolPath** 옵션에 하나 이상의 경로를 추가하여 검색할 다른 위치를 지정할 수 있습니다. 경로를 세미콜론으로 구분합니다.  
  
## <a name="example"></a>예제  
 다음 명령줄은 **_NT_SYMBOL_PATH** 환경 변수를 Windows 기호 서버로 설정하고 로컬 디렉터리를 **C:\Symbols**로 설정합니다.  

 ```cmd
 set  _NT_SYMBOL_PATH=srv*C:\symbols*https://msdl.microsoft.com/downloads/symbols
 ```

 다음 VSPerfReport 명령줄은 **/SymbolPath** 옵션을 사용하여 C:\Projects\Symbols 디렉터리를 검색 경로에 추가합니다.  
  
 **VSPerfReport** **/기호 경로: c:\projects\symbols/summary: all**
