---
title: Idiastackwalkframe::readmemory |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 6d23b46f0f487bddc678814e41b5cb96331ff46c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
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