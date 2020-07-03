---
title: PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 구조 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 3845c872-4302-47b6-8912-7b2d7a3b3357
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 3dd3f1e95436805ccc6e07ca45b5864666e52188
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835396"
---
# <a name="profiler_property_type_substring_info-structure"></a>PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 구조체
관계에 사용 되는 부분 문자열 형식에 대 한 정보를 나타냅니다. [PROFILER_HEAP_OBJECT_RELATIONSHIP 구조](../../winscript/reference/profiler-heap-object-relationship-structure.md)에 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef struct _PROFILER_PROPERTY_TYPE_SUBSTRING_INFO {    UINT length;    LPCWSTR value; } PROFILER_PROPERTY_TYPE_SUBSTRING_INFO;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|형식|설명|  
|------------|----------|-----------------|  
|length|UINT|개체가 UINT입니다.|  
|값|LPCWSTR|개체는 LPCWSTR입니다.|