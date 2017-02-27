---
title: "IDiaTable::Item | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaTable::Item メソッド"
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaTable::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

テーブルの指定されたエントリへの参照を取得します。  
  
## 構文  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### パラメーター  
 `index`  
 \[入力\] `count` が [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md) のメソッドによって返される場合0 ~ \-1 `count` のテーブル エントリのインデックス。  
  
 `element`  
 \[出力\] 指定したテーブルのエントリを表す `IUnknown` のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 テーブルはオブジェクトのコレクションを表します。  これらのオブジェクトには要素のパラメーターは適切なインターフェイスにキャストできます。  たとえばテーブルが [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) のオブジェクトが含まれている場合要素のパラメーター `IDiaSegment` のインターフェイスにキャストできます。  
  
 これは適切な列挙子インターフェイスの [IDiaTable](../../debugger/debug-interface-access/idiatable.md) のインターフェイス `QueryInterface` のメソッドを呼び出しテーブルの内容にアクセスするには列挙子の特定のメソッドを使用する一般的な方法です。  例については[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) のインターフェイスを参照してください。  
  
## 参照  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)