---
title: Idiasourcefile::get_checksum |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 002ad16d94467c135e08ef0040fd7ffd51462719
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31463138"
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
 [in]データバッファのサイズ（バイト単位）。  
  
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
  
## <a name="see-also"></a>関連項目  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)