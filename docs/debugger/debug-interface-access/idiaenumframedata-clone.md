---
title: Idiaenumframedata::clone |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8bd5ac8a9af2ff06e8095dda1c4724f5f76d9b51
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
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
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)