---
title: ResumeTracking | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
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
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: af99ba7e34de4db27f503ba4a7608373fee7d4cc
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="resumetracking"></a>ResumeTracking
現在のコンテキストで追跡を再開します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>戻り値  
 追跡が再開された場合、**HRESULT** に **SUCCEEDED** ビットが設定されます。 コンテキストが利用できず、追跡を再開できない場合、**E_FAIL** が返されます。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** FileTracker.h  
  
## <a name="see-also"></a>参照  
 [SuspendTracking](../msbuild/suspendtracking.md)