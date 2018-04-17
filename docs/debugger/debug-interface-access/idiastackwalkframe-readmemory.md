---
title: Idiastackwalkframe::readmemory |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9874972bd5d6ec72ecd36e32d4487343fa4c231e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
イメージからメモリを読み取ります。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `type`  
 [in]1 つ、 [MemoryTypeEnum 列挙型](../../debugger/debug-interface-access/memorytypeenum.md)にアクセスするメモリの種類を指定する列挙値。  
  
 `va`  
 [in]読み取りを開始するイメージ内の仮想アドレスの位置。  
  
 `cbData`  
 [in]データバッファのサイズ（バイト単位）。  
  
 `pcbData`  
 [out]返されるバイト数を返します。 場合`data`は`NULL`、し`pcbData`使用可能なデータのバイト数合計にはが含まれています。  
  
 `data`  
 [out]指定した場所からデータを使用して入力をバッファーします。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)