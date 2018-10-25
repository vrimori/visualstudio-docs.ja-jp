---
title: Idiasession::findlines |Microsoft Docs
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
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 087248b4d4f25847fa8896a6896c335e2751b906
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49910746"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

指定したコンパイル単位とソース ファイル識別子内で行番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT findLines (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `compiland`  
 [in][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)コンパイル単位を表すオブジェクト。 行番号を検索するためのコンテキストとしては、このインターフェイスを使用します。  
  
 `file`  
 [in][IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)で行番号を検索するソース ファイルを表すオブジェクト。  
  
 `ppResult`  
 [out]返します、 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)行番号の一覧を含むオブジェクトを取得します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



