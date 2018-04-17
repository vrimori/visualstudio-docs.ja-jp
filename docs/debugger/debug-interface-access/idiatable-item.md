---
title: Idiatable::item |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable::Item method
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af10c9924bb7b319c34b017812289ead48929b13
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiatableitem"></a>IDiaTable::Item
テーブル内の指定されたエントリへの参照を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `index`  
 [in]0 ~ の範囲内のテーブル エントリのインデックス`count`-1 で、ここで`count`によって返される、 [idiatable::get_count](../../debugger/debug-interface-access/idiatable-get-count.md)メソッドです。  
  
 `element`  
 [out]返します、`IUnknown`を指定したテーブルのエントリを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 テーブルでは、オブジェクトのコレクションを表します。 によっては、これらのオブジェクト要素のパラメーターは、適切なインターフェイスにキャストできます。 たとえば、テーブルが含まれている場合[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)オブジェクトに要素のパラメーターをキャストすることができ、`IDiaSegment`インターフェイスです。  
  
 呼び出すより一般的な方法は、`QueryInterface`メソッドで、 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)適切な列挙子インターフェイスのためのインターフェイスし、列挙子の特定のメソッドを使用してテーブルの内容にアクセスします。 参照してください、 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)例については、インターフェイスです。  
  
## <a name="see-also"></a>関連項目  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [Idiatable::get_count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)