---
title: "Idiasourcefile::get_checksum |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3cc815608c1871de7269a432e02f95acbb3e0d81
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
 [out]チェックサムのバイト数を返します。 このパラメーターを指定できません`NULL`です。  
  
 `data`  
 [入力、出力].チェックサムのバイトで塗りつぶされているバッファー。 このパラメーターは、する場合`NULL`、し`pcbData`必要なバイト数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 チェックサムのバイトの生成に使用されたチェックサム アルゴリズムの種類を特定するのには、呼び出し、 [idiasourcefile::get_checksumtype](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)メソッドです。  
  
 チェックサムをチェックサム バイトで変更のソース ファイルの変更が反映されますので、通常、イメージ ソース ファイルから生成されます。 チェックサムのバイトが一致しない場合、ファイルを考慮し、ファイルの読み込まれたイメージから生成されたチェックサムが壊れているか、改ざん。  
  
 一般的なチェックサムは、32 バイトを超えるサイズではありませんが、チェックサムの最大サイズであると想定されません。 設定、`data`パラメーターを`NULL`チェックサムを取得するために必要なバイト数を取得します。 適切なサイズのバッファーを割り当てし、新しいバッファーでもう一度このメソッドを呼び出します。  
  
## <a name="see-also"></a>参照  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)