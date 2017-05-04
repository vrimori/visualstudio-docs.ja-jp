---
title: "JsRef Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsRef Typedef
Chakra ガベージ コレクターが所有するオブジェクトへの参照。  
  
## 構文  
  
```  
typedef void *JsRef;  
```  
  
## 解説  
 Chakra ランタイムは、JsRef 参照がローカル変数またはパラメーター \(つまりスタック上\) に格納されている限り、JsRef 参照を自動的に追跡します  。  スタック以外の場所に JsRef を格納すると、オブジェクトの有効期間を管理するために、JsAddRef および JsRelease を呼び出す必要があります。そうしない場合、オブジェクトが使用中であってもガベージ コレクターによって解放されることがあります。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)