---
title: IDiaStackWalkHelper::readMemory |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 7d12d1da983a69f71d96bb06271bd3a971a16cbb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825738"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
メモリ内で実行可能ファイルのイメージからのデータのブロックを読み取ります。  
  
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
 [in]値、 [MemoryTypeEnum 列挙型](../../debugger/debug-interface-access/memorytypeenum.md)読み取るためのメモリの種類を指定する列挙体。  
  
 va  
 [in]読み取りを開始位置を示すイメージ内の仮想アドレス。  
  
 `cbData`  
 [in]データ バッファーのバイト単位のサイズ。  
  
 `pcbData`  
 [out]実際に読み取られたバイト数を返します。 場合`pbData`は`NULL`、これは、使用可能なデータのバイトの合計数。  
  
 `pbData`  
 [入力、出力]メモリの読み取りが入力バッファー。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum 列挙型](../../debugger/debug-interface-access/memorytypeenum.md)