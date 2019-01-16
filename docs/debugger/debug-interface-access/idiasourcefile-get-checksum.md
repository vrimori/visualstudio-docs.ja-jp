---
title: Idiasourcefile::get_checksum |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 463720503440771dcbdfbef39703a53cdc875e66
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843347"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
チェックサムのバイトを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cbData`  
 [in](バイト単位)、データ バッファーのサイズ。  
  
 `pcbData`  
 [out]チェックサムのバイト数を返します。 このパラメーターを `NULL` とすることはできません。  
  
 `data`  
 [入力、出力]チェックサムのバイトで塗りつぶされているバッファー。 このパラメーターは場合`NULL`、し`pcbData`必要なバイト数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 チェックサムのバイトの生成に使用されたチェックサム アルゴリズムの種類を確認するのには、呼び出し、 [idiasourcefile::get_checksumtype](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)メソッド。  
  
 チェックサムは、チェックサムのバイト単位で変更のソース ファイルの変更が反映されますのでに通常のイメージのソース ファイルから生成されます。 チェックサムのバイトが一致しない場合、ファイルを考慮する必要があり、ファイルの読み込まれたイメージから生成されたチェックサムが壊れているか、改ざん。  
  
 一般的なチェックサムは、32 バイトを超えるサイズではありませんが、チェックサムの最大サイズと見なさないでください。 設定、`data`パラメーターを`NULL`チェックサムの取得に必要なバイト数を取得します。 適切なサイズのバッファーを割り当てし、もう一度新しいバッファーでは、このメソッドを呼び出します。  
  
## <a name="see-also"></a>「  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)