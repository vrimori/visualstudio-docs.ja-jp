---
title: Idiasourcefile::get_checksum |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4c8ce89bd4cfe42be0fc67897a4545ecbe6a8a2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546860"
---
# <a name="idiasourcefilegetchecksum"></a>IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[idiasourcefile::get_checksum](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasourcefile-get-checksum)します。  
  
チェックサムのバイトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [out]チェックサムのバイト数を返します。 このパラメーターにすることはできません`NULL`します。  
  
 `data`  
 [入力、出力]チェックサムのバイトで塗りつぶされているバッファー。 このパラメーターは場合`NULL`、し`pcbData`必要なバイト数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 チェックサムのバイトの生成に使用されたチェックサム アルゴリズムの種類を確認するのには、呼び出し、 [idiasourcefile::get_checksumtype](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)メソッド。  
  
 チェックサムは、チェックサムのバイト単位で変更のソース ファイルの変更が反映されますのでに通常のイメージのソース ファイルから生成されます。 チェックサムのバイトが一致しない場合、ファイルを考慮する必要があり、ファイルの読み込まれたイメージから生成されたチェックサムが壊れているか、改ざん。  
  
 一般的なチェックサムは、32 バイトを超えるサイズではありませんが、チェックサムの最大サイズと見なさないでください。 設定、`data`パラメーターを`NULL`チェックサムの取得に必要なバイト数を取得します。 適切なサイズのバッファーを割り当てし、もう一度新しいバッファーでは、このメソッドを呼び出します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)



