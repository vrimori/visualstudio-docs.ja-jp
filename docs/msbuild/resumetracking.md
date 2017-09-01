---
title: ResumeTracking | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 4
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 11a9cee75f912c5fb31cf4a031644abe9c63d744
ms.openlocfilehash: b904d3cb9039088dbaaa3dce8701a32839eb78b9
ms.contentlocale: ja-jp
ms.lasthandoff: 06/03/2017

---
# <a name="resumetracking"></a>ResumeTracking
現在のコンテキストで追跡を再開します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>戻り値  
 追跡が再開された場合、**HRESULT** に **SUCCEEDED** ビットが設定されます。 コンテキストが利用できず、追跡を再開できない場合、**E_FAIL** が返されます。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** FileTracker.h  
  
## <a name="see-also"></a>関連項目  
 [SuspendTracking](../msbuild/suspendtracking.md)
