---
title: Idialoadcallback::notifydebugdir |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: baa1dbde2f4cbe9d537c181c73832f57b31b6041
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043039"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
.Exe ファイルでデバッグ ディレクトリが見つかったときに呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fExecutable`  
 [in]`TRUE` (.dbg ファイルではなく) 実行可能ファイルからデバッグ ディレクトリは読み取り専用である場合。  
  
 `cbData`  
 [in]デバッグ ディレクトリ内のデータのバイト数をカウントします。  
  
 `data[]`  
 [in]デバッグ ディレクトリに設定している配列。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 リターン コードは通常は無視されます。  
  
## <a name="remarks"></a>コメント  
 [Idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)メソッドが実行可能ファイルの処理中にデバッグ ディレクトリを見つけたときに、このコールバックを呼び出します。  
  
 このメソッドは、.pdb ファイル内にある以外のデバッグ情報をサポートするためにリバース エンジニア リング、実行可能ファイルやデバッグ ファイルをクライアントの必要性を削除します。 このデータは、クライアントは、利用可能なデバッグ情報の種類と実行可能ファイルまたは .dbg ファイルに存在するかどうかを認識できます。  
  
 は、ほとんどのクライアントにこのコールバックは必要ありません、`IDiaDataSource::loadDataForExe`メソッドが透過的にシンボルを処理するために必要な場合に、.pdb と .dbg の両方のファイルを開きます。  
  
## <a name="see-also"></a>「  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)