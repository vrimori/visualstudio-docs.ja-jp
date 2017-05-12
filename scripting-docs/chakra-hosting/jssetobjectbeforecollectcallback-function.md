---
title: "JsSetObjectBeforeCollectCallback 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: ea2cbd94-d8b0-4fa9-a4a1-c75a4e338eaf
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsSetObjectBeforeCollectCallback 関数
オブジェクトのガベージ コレクションの前にランタイムに呼び出されるコールバック関数を設定します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsSetObjectBeforeCollectCallback(  
   _In_ JsRef ref,  
   _In_opt_ void *callbackState,  
   _In_ JsObjectBeforeCollectCallback objectBeforeCollectCallback  
);  
```  
  
#### パラメーター  
 `ref`  
 コールバックを登録する対象となるオブジェクト。  
  
 `callbackState`  
 コールバックに返されるユーザー指定の状態。  
  
 `objectBeforeCollectCallback`  
 設定するコールバック関数。  以前に登録されたコールバックをクリアするには、null を使用します。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 コールバックは現在のランタイム実行スレッド上で呼び出されるため、コールバックが完了するまで実行がブロックされます。  
  
 この API は、エッジ モードでのみサポートされます。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)