---
title: Idialoadcallback::notifydebugdir |Microsoft Docs
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
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4496a7941de29f4ef500a135559dcd746036f6d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548377"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[idialoadcallback::notifydebugdir](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialoadcallback-notifydebugdir)します。  
  
.Exe ファイルでデバッグ ディレクトリが見つかったときに呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
## <a name="remarks"></a>Remarks  
 [Idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)メソッドが実行可能ファイルの処理中にデバッグ ディレクトリを見つけたときに、このコールバックを呼び出します。  
  
 このメソッドは、.pdb ファイル内にある以外のデバッグ情報をサポートするためにリバース エンジニア リング、実行可能ファイルやデバッグ ファイルをクライアントの必要性を削除します。 このデータは、クライアントは、利用可能なデバッグ情報の種類と実行可能ファイルまたは .dbg ファイルに存在するかどうかを認識できます。  
  
 は、ほとんどのクライアントにこのコールバックは必要ありません、`IDiaDataSource::loadDataForExe`メソッドが透過的にシンボルを処理するために必要な場合に、.pdb と .dbg の両方のファイルを開きます。  
  
## <a name="see-also"></a>関連項目  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)



