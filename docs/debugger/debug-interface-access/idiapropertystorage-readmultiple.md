---
title: "IDiaPropertyStorage::ReadMultiple | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadMultiple"
ms.assetid: 6ccc9397-ce41-4f72-b261-72ac252cd4a5
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage::ReadMultiple
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

現在のプロパティの設定を指定されたプロパティを読み取ります。  
  
## 構文  
  
```cpp#  
HRESULT ReadMultiple(   
   ULONG          cpspec,  
   PROPSPEC const rgpspec,  
   PROPVARIANT    rgvar  
);  
```  
  
#### パラメーター  
 `cpspec`  
 \[入力\] `rgpspec` の配列で指定されたプロパティの数。  ゼロが正常に終了コードとしてメソッドがを返した場合にプロパティが `S_OK` を返します。  
  
 `rgpspec`  
 \[入力\] 読み込まれるプロパティの配列。  プロパティはプロパティ ID または省略可能な文字列名で指定できます。  配列内の特定の順序でプロパティを指定する必要はありません。  配列は単純なプロパティには重複したプロパティ値によって重複したプロパティを含めることができます。  非単純なプロパティがもう一度ファイルを開くときに拒否を返す必要があります。  配列にはプロパティ ID の組み合わせが含まれID を対象とすることができます。  この配列にはプロパティ値の少なくとも `cpspec` の数が必要です。  
  
 `rgvar`  
 \[入力出力\] の各プロパティの値が格納される `PROPVARIANT` の構造体の配列 \(Microsoft.VisualStudio.OLE.Interop の名前空間\)。  配列には少なくとも `cpspec` の要素である必要があります。  呼び出し元は配列の値を初期化する必要はありません。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` プロパティの一つ以上が検索 `S_FALSE` を返します。  それ以外の場合はエラー コードを返します。  
  
## 解説  
 プロパティが見つかった場合 `rgvar` の配列の対応するエントリは `VT_EMPTY` の種類がの `VARIANT` が含まれています。  
  
## 参照  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)