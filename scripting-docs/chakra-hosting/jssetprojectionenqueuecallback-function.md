---
title: "JsSetProjectionEnqueueCallback 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsSetProjectionEnqueueCallback 関数
呼び出し元の必要なスレッドに対して、射影の完了を呼び出すのに使用するコールバックを設定します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### パラメーター  
 `projectionEnqueueContext`  
 バックグラウンド スレッドで射影の完了が発生するときに呼び出されるコールバック。  
  
 `callbackState`  
 `projectionEnqueueContext` に提供されるアプリケーション コンテキスト。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
 呼び出しは、別の COM アパートメントまたは同じ MTA の別のスレッドから行われる必要があります。  
  
 この API は、エッジ モードでのみサポートされます。  
  
> [!CAUTION]
>  PInvoke は、現在この API ではサポートされていません。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)