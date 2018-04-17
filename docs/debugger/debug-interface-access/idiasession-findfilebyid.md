---
title: Idiasession::findfilebyid |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25b034abccc60bcbf6f976930083ad0d90598fae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
ソース ファイルをソース ファイル識別子を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `uniqueId`  
 [in]ソース ファイル識別子を指定します。  
  
 `ppResult`  
 [out]返します、 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)ソース ファイルを表すオブジェクトを取得します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 ソース ファイル識別子は、すべてのソース ファイルを一意にする DIA SDK に内部的に使用される一意の値です。 通常、このメソッドは DIA SDK に内部的に使用されます。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Idiasession::findfile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)