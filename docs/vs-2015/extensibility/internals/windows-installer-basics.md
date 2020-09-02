---
title: Windows Installer 기본 사항 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4693654e12dc37209cb92e3e2ba95bde8bd13e77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687673"
---
# <a name="windows-installer-basics"></a>Windows Installer 기본 사항
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Windows Installer은 사용자 컴퓨터에 응용 프로그램 또는 소프트웨어 제품을 설치 및 제거 하 고, 이러한 작업을 Windows Installer 구성 요소 (예를 들어 WICs 또는 구성 요소 라고도 함) 라는 단위로 수행 합니다. GUID는 설치의 기본 단위인 각 WIC를 식별 하 고 Windows Installer를 사용 하는 설치에 대 한 참조 수를 계산 합니다.  
  
 Windows Installer에 대 한 포괄적인 설명서는 Platform SDK 항목 [Windows Installer](/previous-versions/2kt85ked(v=vs.120))을 참조 하세요.  
  
## <a name="authoring-a-vspackage"></a>VSPackage 작성  
 Windows Installer는 Windows Installer 제품을 설치, 제거 또는 복구 하 고 설치 프로그램 UI (사용자 인터페이스)를 실행 하는 데 필요한 정보가 포함 된 설치 패키지를 사용 합니다. 각 설치 패키지에는 설치 데이터베이스, 요약 정보 스트림 및 설치의 여러 부분에 대 한 데이터 스트림이 포함 된 .msi 파일이 포함 되어 있습니다. 설치 관리자를 사용 하려면 설치를 작성 해야 합니다. 설치 관리자는 구성 요소의 개념을 중심으로 설치를 구성 하 고 설치에 대 한 정보를 관계형 데이터베이스에 저장 하므로 설치 패키지를 광범위 하 게 작성 하는 과정에는 다음 단계가 수반 됩니다.  
  
1. 버전 관리 및 병렬 전략을 지원 하도록 설치 제작을 계획 합니다.  
  
2. 사용자에 게 제공할 기능을 식별 합니다.  
  
3. VSPackage 및 종속성을 구성 요소로 구성 합니다.  
  
4. 정보를 사용 하 여 설치 데이터베이스를 채웁니다.  
  
5. 설치 패키지의 유효성을 검사 합니다.  
  
   이 설명서에서는 주로 프로세스의 첫 번째 단계와 세 번째 단계를 다룹니다. 이러한 단계를 수행 하는 동안 VSPackage 기능을 WICs로 구성 하 여 이후 버전의에 대 한 고려 사항에 대 한 버전 관리 및 서비스 전략을 세울 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 나머지 세 단계는 Platform SDK의 Windows Installer 설명서에 자세히 설명 되어 있습니다.  
  
## <a name="key-terms"></a>주요 용어  
 다음은 Windows Installer 기술과 관련 된 주요 용어에 대 한 정의입니다.  
  
 리소스  
 파일, 레지스트리 키, 바로 가기 등을 컴퓨터에 설치할 수 있습니다. 이러한 리소스는 Windows Installer 구성 요소로 논리적으로 그룹화 됩니다.  
  
 Windows Installer 구성 요소 (WIC)  
 하나의 단위로 설치 및 제거 되는 관련 리소스의 논리적 그룹화를 나타내는 설치의 기본 단위입니다. Windows Installer 구성 요소는 고유한 구성 요소 ID 또는 GUID로 식별 됩니다. 또한 Windows Installer은 WIC 수준에서 참조 횟수를 유지 관리 합니다. 최대 버전 관리 유연성을 위해 지정 된 WIC에는 DLL과 같은 둘 이상의 주 리소스를 포함 하지 않습니다. WIC를 식별 하 고 채운 후 GUID를 제공 하 고 배포 하는 경우 해당 구성을 변경할 수 없습니다. 자세한 내용은 [응용 프로그램을 구성 요소로](https://msdn.microsoft.com/library/aa370561.aspx)구성을 참조 하세요.  
  
 패키지 (Redist 패키지)  
 이 파일이 가리킬 수 있는 .msi 파일 및 외부 소스 파일로 구성 된 배포 단위입니다. 패키지에는 Windows Installer UI를 실행 하 고 응용 프로그램을 설치 하거나 제거 하는 데 필요한 모든 정보가 포함 되어 있습니다.  
  
 .msi 파일  
 응용 프로그램을 설치 하는 데 필요한 지침과 데이터를 포함 하는 COM 구조적 저장소 파일입니다. 모든 패키지에는 .msi 파일이 하나 이상 포함 되어 있습니다. .Msi 파일에는 설치 관리자 데이터베이스, 요약 정보 스트림 및 하나 이상의 변환 및 내부 원본 파일이 포함 되어 있을 수 있습니다. 설치할 파일은 캐비닛으로 압축 되 고 .msi 파일의 스트림에 저장 되거나 원본 미디어의 .msi 파일 외부에 저장, 압축 또는 압축을 해제할 수 있습니다. 자세한 내용은 [Windows Installer 파일 확장명](https://msdn.microsoft.com/library/aa372842\(VS.85\).aspx)을 참조 하세요.  
  
## <a name="windows-installer-rules-enforcement"></a>Windows Installer 규칙 적용  
 두 규칙 집합은 설치의 구성 요소를 통해 리소스 배포를 결정 합니다. 한 규칙 집합은 Windows Installer 자체에서 유지 관리 되는 반면 두 번째 집합을 설치 작성자로 적용 해야 합니다.  
  
> [!NOTE]
> Windows Installer 규칙의 적용은 .msi 파일의 유효성 검사를 실행 하는 경우에만 발생 합니다. 그럼에도 불구 하 고 이러한 규칙을 모범 사례에 cautioned 합니다. 자세한 내용은 [설치 데이터베이스 유효성](https://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) 검사 및 [패키지 유효성 검사](https://msdn.microsoft.com/library/aa370569\(VS.85\).aspx)를 참조 하세요.  
  
#### <a name="installer-enforced-rules"></a>설치 관리자 적용 규칙  
  
- 지정 된 구성 요소의 모든 파일은 동일한 디렉터리에 설치 해야 합니다. 반대로 별도의 폴더에 설치 된 파일은 개별 구성 요소에 속해야 합니다.  
  
- 구성 요소별 키 경로는 하나만 있을 수 있습니다. 키 경로는 단순히 전체 구성 요소를 나타내는 파일 또는 레지스트리 키입니다.  
  
#### <a name="component-provider-responsibilities"></a>구성 요소-공급자 책임  
  
- 이후 버전에서 별도로 제공할 수 있는 두 리소스는 별도의 구성 요소에 있어야 합니다. 리소스는 이러한 리소스를 별도로 제공 하지 않는 것이 확실 한 경우에만 동일한 구성 요소로 그룹화 해야 합니다. 실제로 모든 기본 리소스 (예: Dll)는 항상 별도의 WICs에 존재 하는 것이 좋습니다. 자세한 내용은 [설치 관리자 구성 요소 정의](https://msdn.microsoft.com/library/aa368269\(VS.85\).aspx)를 참조 하세요.  
  
- 버전이 지정 된 리소스는 둘 이상의 WIC에서 제공 되어야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [구성 요소 규칙이 중단 되 면 어떻게 되나요?](https://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)
