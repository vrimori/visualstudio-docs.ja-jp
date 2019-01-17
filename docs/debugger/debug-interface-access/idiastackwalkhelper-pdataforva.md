---
title: IDiaStackWalkHelper::pdataForVA |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::pdataByVA method
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a29c1a9fa21b973bca5db03bae07f608f82014f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888024"
---
# <a name="idiastackwalkhelperpdataforva"></a>IDiaStackWalkHelper::pdataForVA
仮想アドレスに関連付けられている PDATA データ ブロックを返します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `va`  
 [in]取得するデータの仮想アドレスを指定します。  
  
 `cbData`  
 [in](バイト) を取得するデータのサイズ。  
  
 `pcbData`  
 [out]取得したバイトでは、データの実際のサイズを返します。  
  
 `pbData`  
 [入力、出力]要求されたデータが入力バッファー。 `NULL` にすることはできません。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`指定されたアドレスの PDATA がない場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 PDATA (".pdata"という名前の部分)、コンパイル単位の関数の例外処理に関する情報が含まれています。  
  
 データの量が、呼び出し元に、データの量は使用を要求する必要がないために返される、呼び出し元が認識しています。 そのため、許容される場合は、エラーを返すには、このメソッドの実装は、`pbData`パラメーターが`NULL`します。  
  
## <a name="see-also"></a>「  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)