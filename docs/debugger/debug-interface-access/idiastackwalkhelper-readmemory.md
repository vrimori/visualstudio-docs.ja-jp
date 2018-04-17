---
title: IDiaStackWalkHelper::readMemory |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af93d4d49167a6167d971140c3b668c95a34f799
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
メモリ内で実行可能ファイルのイメージからのデータ ブロックを読み取ります。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `type`  
 [in]値、 [MemoryTypeEnum 列挙型](../../debugger/debug-interface-access/memorytypeenum.md)読み取るためのメモリの種類を指定する列挙です。  
  
 va  
 [in]読み取りを開始位置を示すイメージ内の仮想アドレス。  
  
 `cbData`  
 [in]データ バッファーのサイズ (バイト単位)。  
  
 `pcbData`  
 [out]実際に読み取られたバイト数を返します。 場合`pbData`は`NULL`、これは、使用可能なデータのバイトの総数。  
  
 `pbData`  
 [入力、出力].メモリの読み取りが入力バッファー。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum 列挙型](../../debugger/debug-interface-access/memorytypeenum.md)