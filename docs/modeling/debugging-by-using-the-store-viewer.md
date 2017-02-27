---
title: "ストア ビューアーを使用したデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン固有言語, ストア"
  - "ドメイン固有言語, ストア ビューアー"
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 17
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 17
---
# ストア ビューアーを使用したデバッグ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ストア ビューアーを使用すると[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] で使用される  *ストア*  の状態を確認できます。  ストア ビューアーは要素での要素のプロパティとリンクとともに特定のストアにドメイン モデルのすべての要素が表示されます。  
  
## 開始ストア ビューアー  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の実験用ビルドではモデル ストアのインスタンスが情報を含むブレークポイントでコードが停止します。  次に \[ENT9ENT\] ウィンドウで次のコマンドを入力してストア ビューアーを表示します :  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
>  ストアのインスタンスの名前で `mystore` を置き換える必要があります。  またコードに名前空間を追加する場合は完全修飾名前空間なしでストアのビューアーを表示するためのコマンドを入力して :  
>   
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
>  `…`  
>   
>  `StoreViewer.Show(mystore);`  
  
 `Show` メソッドには、いくつかのオーバーロードがあります。  パラメーターとして格納またはパーティションのインスタンスを指定できます。  
  
 別の方法として`Show` にメソッドに渡すパラメーターがスコープ内にあるコードに関するビューアーをどこでも表示コード行を配置できます。  この操作はコード行がストアのコンテンツのスナップショットとして実行するとストア ビューアーを表示します。  
  
### ビューアーを使用してストア  
 ストア ビューアーが開きますがモードレス ウィンドウの Windows フォームが表示されたら次の図に示すよう。  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
ビューアーを保存します。  
  
 ストア ビューアーは3 種類のウィンドウがあります : 左ペイン右上のペインと右側のペイン。  左ペインにはストア内の `DomainDataDirectory` のメンバーの型のツリー ビューです。  パーティションのノードを展開し要素をクリックすると要素のプロパティに上から下のペインに表示されます。  要素が他の要素にリンクする場合は追加の要素が右側のペインに表示されます。  右側のペインの各要素をクリックし要素は左ペインで強調表示されます。  
  
## 参照  
 [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)