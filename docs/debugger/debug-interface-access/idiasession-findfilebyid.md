---
title: Idiasession::findfilebyid |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: f92e811936e4ed7e8bc5e5272c22256f66fbf689
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53832847"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
ソース ファイルの識別子を使用してソース ファイルを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `uniqueId`  
 [in]ソース ファイルの識別子を指定します。  
  
 `ppResult`  
 [out]返します、 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)ソース ファイルを表すオブジェクトを取得します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 ソース ファイルの識別子は、すべてのソース ファイルを一意にする DIA SDK に内部的に使用される一意の値です。 通常、DIA SDK に内部的にこのメソッドが使用されます。  
  
## <a name="see-also"></a>「  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)