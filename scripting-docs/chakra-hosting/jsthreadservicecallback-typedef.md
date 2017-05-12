---
title: "JsThreadServiceCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsThreadServiceCallback Typedef
スレッド サービス コールバック。  
  
## 構文  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### パラメーター  
 callback  
 バックグラウンド作業項目のコールバック。  
  
 callbackData  
 コールバックに渡すデータ引数。  
  
## 解説  
 ホストは、JsCreateRuntime の呼び出し時にバックグラウンド スレッド サービスを指定できます。  指定時には、バックグラウンド作業項目がこのコールバックを使用してホストに渡されます。  ホストは、バックグラウンド作業項目の実行を直ちに開始し、true または false を返す必要があります。そしてランタイムがスレッド内の作業項目を処理します。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)