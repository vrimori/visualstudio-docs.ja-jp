---
title: "非同期 Windows ランタイム メソッドからの特別なエラー プロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# 非同期 Windows ランタイム メソッドからの特別なエラー プロパティ
エラーが呼び出し履歴の奥深いところからスローされることがあるため、JavaScript で非同期 Windows ランタイム メソッドをデバッグするのは困難な場合があります。  JavaScript の `Error` オブジェクトには、アプリがデバッグ モードで実行されているときにエラーが非同期 Windows ランタイム メソッドからスローされた場合にのみ表示される、追加のプロパティがあります。  
  
## 特殊なエラー プロパティ  
 デバッグ モードで Windows ランタイムの非同期操作に失敗した結果として生じるエラー オブジェクトには、次の特別なプロパティがあります。  
  
-   `asyncOpSource` \(オブジェクト\) は、エラーの原因となった呼び出しが行われた元の場所に関する情報を取得します。  プロパティ `asyncOpSource.originatingCall` \(文字列\) は、非同期操作を開始した場所をユーザー コード内で表示します。  
  
-   asyncOpType \(文字列\) は、エラーの原因となった非同期操作の型の名前を取得します。  
  
 非同期操作でのエラーの詳細については、以下を参照してください。  
  
-   [How to handle errors with promises](http://msdn.microsoft.com/ja-jp/01d5a901-c4ea-46f6-8005-6d39c32203eb)  
  
-   [Windows ランタイム エラーのトラブルシューティング](http://msdn.microsoft.com/ja-jp/1ef7d7df-82ac-441d-8ad0-54ab1318de64)