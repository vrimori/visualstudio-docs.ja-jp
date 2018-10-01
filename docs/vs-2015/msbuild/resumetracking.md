---
title: ResumeTracking | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- ResumeTracking
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47d565bde6ef6211589e9293996c7a651ffdd8bd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538380"
---
# <a name="resumetracking"></a>ResumeTracking
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ResumeTracking](https://docs.microsoft.com/visualstudio/msbuild/resumetracking)します。  
  
  
現在のコンテキストで追跡を再開します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## <a name="return-value"></a>戻り値  
 [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) と [SUCCEEDED] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) ビット セットの追跡が再開された場合。 [E_FAIL](<!-- TODO: review code entity reference <xref:assetId:///E_FAIL?qualifyHint=False&amp;autoUpgrade=True>  -->) コンテキストが利用できなかったため、追跡を再開できないかどうかが返されます。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** FileTracker.h  
  
## <a name="see-also"></a>関連項目  
 [SuspendTracking](../msbuild/suspendtracking.md)



