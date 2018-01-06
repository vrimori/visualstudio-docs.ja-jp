---
title: "Idiaenumframedata::clone |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9c684eb3f9e18e331190e379ff167b8a296ef041
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
現在の列挙子と同じ列挙の状態を含む列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Clone(   
   IDiaEnumFrameData** ppenum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 ppenum  
 [out]返します、 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)列挙子の重複を含むオブジェクトです。 列挙子だけデータが、フレームが重複しています。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>参照  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)