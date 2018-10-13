---
title: IDiaStackWalkHelper::readMemory |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::readMemory method
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e110a67f7db5359d9f840f8853307206b84e339
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201527"
---
# <a name="idiastackwalkhelperreadmemory"></a>IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

メモリ内で実行可能ファイルのイメージからのデータのブロックを読み取ります。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
 Va  
 [in]読み取りを開始位置を示すイメージ内の仮想アドレス。  
  
 `cbData`  
 [in]データ バッファーのバイト単位のサイズ。  
  
 `pcbData`  
 [out]実際に読み取られたバイト数を返します。 場合`pbData`は`NULL`、これは、使用可能なデータのバイトの合計数。  
  
 `pbData`  
 [入力、出力]メモリの読み取りが入力バッファー。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [MemoryTypeEnum 列挙型](../../debugger/debug-interface-access/memorytypeenum.md)



