---
title: "複数プロジェクトの接続設定の適用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理プラグインを設定の適用"
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 複数プロジェクトの接続設定の適用
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソース管理プラグイン API 1.2 を使用して作成されたソース管理プラグインは複数のプロジェクトまたは複数のコネクション コンテキストにわたって同じソース管理操作を実行するにはバッチ処理を使用できます。  バッチが詳細のユーザー エクスペリエンスからプロジェクトのダイアログ ボックスを削除するために使用できます。  
  
 ユーザーがソース管理プラグイン API を使用して 1.1 \(たとえばファイル共有のコンピューターの 2 種類の Web プロジェクト\) ビルド ソース管理プラグインの接続に属しファイルをチェック アウトする複数の項目を選択するとユーザーはダイアログ ボックスを繰り返し表示されます。  これはIDE が各接続コンテキストの状態をリセットするためユーザーがダイアログ ボックスの \[ENT1ENT\] チェック ボックスをクリックした場合でも発生します。  
  
## 新しい機能のフラグ  
 `SccBeginBatch` 関数の設定のバッチ処理が進行中であることを示すフラグ `SCC_CAP_BATCH`  
  
## 新しい関数  
 次の新しい機能はバッチ処理をサポートします :  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 `SCCBeginBatch` の関数はソース管理操作のグループを開始します。  `SccEndBatch` はグループを閉じます。  グループが入れ子になっていない可能性があります。  
  
## 参照  
 [ソース管理プラグイン API バージョン 1.2 の新機能します。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)